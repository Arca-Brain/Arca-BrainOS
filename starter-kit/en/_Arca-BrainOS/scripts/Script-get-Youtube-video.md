#!/bin/bash
# ==============================================================================
# 🎥 Script-get-Youtube-video.md (Arca-BrainOS)
# Automated ingestion and distillation of YouTube videos from a playlist
# ==============================================================================

# --- CONFIGURATION ---
# Portable dynamic folder detection (relative to script location)
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
VAULT_DIR="$(cd "$SCRIPT_DIR/../.." && pwd)"

# Replace with your YouTube playlist URL (Unlisted recommended)
PLAYLIST_URL="YOUR_PLAYLIST_URL_HERE"

DOSSIER_VIDEOS="$VAULT_DIR/0-Inbox/Youtube"
FICHIER_HISTORIQUE="$SCRIPT_DIR/historique_youtube_log.md"
FICHIER_LOG="$VAULT_DIR/_Arca-BrainOS/log.md"

# Ensure directories and registry exist
mkdir -p "$DOSSIER_VIDEOS"
touch "$FICHIER_HISTORIQUE"

if [ "$PLAYLIST_URL" = "YOUR_PLAYLIST_URL_HERE" ]; then
    echo "⚠️ Please configure PLAYLIST_URL in this script with your YouTube playlist link."
    exit 1
fi

echo "🔍 Scanning YouTube playlist..."

# yt-dlp fetches playlist video URLs
URLS_PLAYLIST=$(yt-dlp --no-warnings --flat-playlist --get-url "$PLAYLIST_URL" 2>/dev/null)

if [ -z "$URLS_PLAYLIST" ]; then
    echo "⚠️ No URLs found or error connecting to playlist."
    exit 0
fi

NB_NOUVELLES=0

for url in $URLS_PLAYLIST; do
    # Check if URL was already processed
    if ! grep -q "$url" "$FICHIER_HISTORIQUE"; then
        echo "⚡ New video detected: $url"
        
        # 1. Instant metadata extraction via yt-dlp
        TITRE_BRUT=$(yt-dlp --no-warnings --print "%(title)s" "$url" 2>/dev/null)
        AUTEUR_BRUT=$(yt-dlp --no-warnings --print "%(uploader)s" "$url" 2>/dev/null)
        
        if [ -z "$TITRE_BRUT" ]; then
            echo "⚠️ Unable to fetch metadata for $url. Skipped."
            continue
        fi

        # Sanitize title for valid filename (cross-platform)
        NOM_FICHIER=$(echo "$TITRE_BRUT" | sed -e 's/[/:*?"<>|]/ /g' -e 's/[[:space:]]\+/-/g' -e 's/^-\+//' -e 's/-\+$//' | cut -c1-60)
        CHEMIN_FINAL="$DOSSIER_VIDEOS/$NOM_FICHIER.md"
        
        echo "📝 Processing: $TITRE_BRUT ($AUTEUR_BRUT)"
        echo "⏳ Extracting transcript and generating note with AI..."

        # 2. Subtitle extraction and distillation via dedicated Python script
        python3 - << 'PYEOF' "$url" "$TITRE_BRUT" "$AUTEUR_BRUT" "$CHEMIN_FINAL"
import sys, os, subprocess, tempfile, glob, re
from datetime import date

url = sys.argv[1]
title = sys.argv[2]
author = sys.argv[3]
dest_file = sys.argv[4]
today = date.today().isoformat()

# Download subtitles (vtt) via yt-dlp into a temporary directory
with tempfile.TemporaryDirectory() as tmpdir:
    sub_base = os.path.join(tmpdir, "sub")
    subprocess.run(
        ["yt-dlp", "--no-warnings", "--write-auto-sub", "--write-sub", "--sub-lang", "en,fr", "--skip-download", "--sub-format", "vtt", "-o", f"{sub_base}.%(ext)s", url],
        stdout=subprocess.DEVNULL,
        stderr=subprocess.DEVNULL
    )
    vtt_files = glob.glob(f"{sub_base}*.vtt")
    transcript = ""
    if vtt_files:
        # Prefer English subtitles if available
        en_files = [f for f in vtt_files if ".en." in f]
        chosen_vtt = en_files[0] if en_files else vtt_files[0]
        try:
            with open(chosen_vtt, "r", encoding="utf-8", errors="ignore") as f:
                content = f.read()
            cues = re.split(r"\n\s*\n", content)
            lines = []
            last_line = ""
            for cue in cues:
                parts = cue.strip().split("\n")
                if not parts: continue
                ts_m = re.search(r"(\d{2}:\d{2}:\d{2})", parts[0])
                if not ts_m and len(parts) > 1:
                    ts_m = re.search(r"(\d{2}:\d{2}:\d{2})", parts[1])
                    parts = parts[1:]
                if not ts_m: continue
                ts = ts_m.group(1)
                if ts.startswith("00:"): ts = ts[3:] # MM:SS
                cue_text = " ".join(parts[1:])
                cue_text = re.sub(r"<[^>]+>", "", cue_text)
                cue_text = re.sub(r"\s+", " ", cue_text).strip()
                if cue_text and cue_text != last_line:
                    if last_line and cue_text.startswith(last_line):
                        diff = cue_text[len(last_line):].strip()
                        if diff:
                            lines[-1] = (ts, cue_text)
                            last_line = cue_text
                    else:
                        lines.append((ts, cue_text))
                        last_line = cue_text
            # Group into readable blocks
            blocks = []
            cur_ts = ""
            cur_txt = []
            for ts, txt in lines:
                if not cur_ts: cur_ts = ts
                cur_txt.append(txt)
                if len(" ".join(cur_txt)) > 200:
                    blocks.append(f"[{cur_ts}] " + " ".join(cur_txt))
                    cur_ts = ""
                    cur_txt = []
            if cur_txt:
                blocks.append(f"[{cur_ts}] " + " ".join(cur_txt))
            transcript = "\n\n".join(blocks)
        except Exception:
            transcript = ""

    # Fallback to official description if no subtitles
    if not transcript:
        try:
            desc = subprocess.check_output(["yt-dlp", "--no-warnings", "--print", "%(description)s", url], text=True, errors="ignore").strip()
            transcript = f"Transcript unavailable. Official video description:\n{desc}"
        except Exception:
            transcript = "No transcript or description available."

    # Build prompt for agy
    safe_title = title.replace('"', "'").replace(':', ' -')
    safe_author = author.replace('"', "'")
    
    prompt = f"""You are the Arca-BrainOS knowledge distiller. Transform this YouTube video transcript into a high-quality, structured Obsidian note.

Metadata:
- Original Title: {safe_title}
- Author / Channel: {safe_author}
- Source URL: {url}
- Date: {today}

STRICT expected structure:
---
date_created: {today}
title: "{safe_title} with {safe_author}"
description: "Conceptual and operational summary of the video"
category: "media"
url: "{url}"
tags:
  - media
  - youtube
---
# 🎥 {safe_title}

## ⚡ Executive Summary
(A dense and clear paragraph of 3 to 5 lines summarizing the core thesis).

## 💡 Key Ideas
* (Key idea 1 : Explanation in 2 sentences max with exact timestamp [MM:SS])
* (Key idea 2 with timestamp)
* (Key idea 3 with timestamp)
* (Key idea 4 with timestamp)
* (Key idea 5 with timestamp)

## 🗣️ Notable Quotes
> "Impactful quote 1"

> "Impactful quote 2"

## 🛠️ Actionable Takeaways
- [ ] Actionable step 1.
- [ ] Actionable step 2.
- [ ] Actionable step 3.

## 📚 References & Mentioned Tools
* Book / Author : Title
* Concept / Tool : Name

## 📝 Detailed Transcript & Synthesis Notes
(Structured synthesis in 5 to 10 chronological points with timestamps [MM:SS] tracking the video's arguments).

STRICT FORMATTING RULES (ANTI-CHATTER):
1. NO introduction (never say "Here is the note...").
2. NO conclusion (never say "Hope this helps...").
3. Your answer must start EXACTLY with the first triple dash `---` of the YAML frontmatter and end with the last section.
4. NEVER use em-dashes (—). Use colons, commas, or parentheses instead.

Video transcript:
{transcript}
"""

    res = subprocess.run(["agy", "--dangerously-skip-permissions", "-p", prompt], capture_output=True, text=True)
    if res.returncode == 0 and res.stdout.strip():
        with open(dest_file, "w", encoding="utf-8") as f_out:
            f_out.write(res.stdout.strip() + "\n")
PYEOF

        # 3. Security validation before adding to history
        if [ -s "$CHEMIN_FINAL" ] && [ $(wc -c < "$CHEMIN_FINAL") -gt 150 ]; then
            echo "$url" >> "$FICHIER_HISTORIQUE"
            if [ -f "$FICHIER_LOG" ]; then
                echo "[$(date '+%Y-%m-%d %H:%M')] - AI Action (YouTube): New video processed from $url" >> "$FICHIER_LOG"
            fi
            echo "✅ Note successfully created: $CHEMIN_FINAL"
            NB_NOUVELLES=$((NB_NOUVELLES + 1))
        else
            echo "❌ Error: generation failed for $url. Not added to registry."
            rm -f "$CHEMIN_FINAL"
        fi
    fi
done

if [ $NB_NOUVELLES -gt 0 ]; then
    echo "🎉 Batch complete! $NB_NOUVELLES new video(s) added to Obsidian."
else
    echo "🎉 Batch complete! No new videos to process (everything is up to date)."
fi

