#!/bin/bash
# ==============================================================================
# 🎥 Script-get-Youtube-video.md (Arca-BrainOS)
# Ingestion automatique et distillation des vidéos YouTube depuis une playlist
# ==============================================================================

# --- CONFIGURATION ---
# Détection dynamique et portable des dossiers (relative à l'emplacement du script)
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
VAULT_DIR="$(cd "$SCRIPT_DIR/../.." && pwd)"

# Remplacez par l'URL de votre playlist YouTube (Non répertoriée recommandée)
PLAYLIST_URL="VOTRE_URL_DE_PLAYLIST_ICI"

DOSSIER_VIDEOS="$VAULT_DIR/0-Inbox/Youtube"
FICHIER_HISTORIQUE="$SCRIPT_DIR/historique_youtube_log.md"
FICHIER_LOG="$VAULT_DIR/_Arca-BrainOS/log.md"

# Préparation des dossiers et fichiers
mkdir -p "$DOSSIER_VIDEOS"
touch "$FICHIER_HISTORIQUE"

if [ "$PLAYLIST_URL" = "VOTRE_URL_DE_PLAYLIST_ICI" ]; then
    echo "⚠️ Veuillez configurer PLAYLIST_URL dans ce script avec le lien de votre playlist YouTube."
    exit 1
fi

echo "🔍 Scan de la playlist 2ndBrain..."

# Récupération des URLs de la playlist via yt-dlp
URLS_PLAYLIST=$(yt-dlp --no-warnings --flat-playlist --get-url "$PLAYLIST_URL" 2>/dev/null)

if [ -z "$URLS_PLAYLIST" ]; then
    echo "⚠️ Aucune URL trouvée ou erreur de connexion à la playlist."
    exit 0
fi

NB_NOUVELLES=0

for url in $URLS_PLAYLIST; do
    # Vérification si l'URL a déjà été traitée
    if ! grep -q "$url" "$FICHIER_HISTORIQUE"; then
        echo "⚡ Nouvelle vidéo détectée : $url"
        
        # 1. Extraction instantanée des métadonnées via yt-dlp
        TITRE_BRUT=$(yt-dlp --no-warnings --print "%(title)s" "$url" 2>/dev/null)
        AUTEUR_BRUT=$(yt-dlp --no-warnings --print "%(uploader)s" "$url" 2>/dev/null)
        
        if [ -z "$TITRE_BRUT" ]; then
            echo "⚠️ Impossible de récupérer les métadonnées pour $url. Ignorée."
            continue
        fi

        # Nettoyage du titre pour un nom de fichier sain (sans caractères interdits)
        NOM_FICHIER=$(echo "$TITRE_BRUT" | sed -e 's/[/:*?"<>|]/ /g' -e 's/[[:space:]]\+/-/g' -e 's/^-\+//' -e 's/-\+$//' | cut -c1-60)
        CHEMIN_FINAL="$DOSSIER_VIDEOS/$NOM_FICHIER.md"
        
        echo "📝 Traitement : $TITRE_BRUT ($AUTEUR_BRUT)"
        echo "⏳ Extraction de la retranscription et génération par l'IA..."

        # 2. Extraction des sous-titres et génération via script Python dédié
        python3 - << 'PYEOF' "$url" "$TITRE_BRUT" "$AUTEUR_BRUT" "$CHEMIN_FINAL"
import sys, os, subprocess, tempfile, glob, re
from datetime import date

url = sys.argv[1]
title = sys.argv[2]
author = sys.argv[3]
dest_file = sys.argv[4]
today = date.today().isoformat()

# Téléchargement des sous-titres (vtt) via yt-dlp dans un dossier temporaire
with tempfile.TemporaryDirectory() as tmpdir:
    sub_base = os.path.join(tmpdir, "sub")
    subprocess.run(
        ["yt-dlp", "--no-warnings", "--write-auto-sub", "--write-sub", "--sub-lang", "fr,en", "--skip-download", "--sub-format", "vtt", "-o", f"{sub_base}.%(ext)s", url],
        stdout=subprocess.DEVNULL,
        stderr=subprocess.DEVNULL
    )
    vtt_files = glob.glob(f"{sub_base}*.vtt")
    transcript = ""
    if vtt_files:
        # Priorité au français
        fr_files = [f for f in vtt_files if ".fr." in f]
        chosen_vtt = fr_files[0] if fr_files else vtt_files[0]
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
            # Regroupement par blocs temporels
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

    # Fallback si pas de sous-titres : récupération de la description
    if not transcript:
        try:
            desc = subprocess.check_output(["yt-dlp", "--no-warnings", "--print", "%(description)s", url], text=True, errors="ignore").strip()
            transcript = f"Retranscription indisponible. Description officielle de la vidéo :\n{desc}"
        except Exception:
            transcript = "Aucune retranscription ni description disponible."

    # Construction du prompt pour agy
    safe_title = title.replace('"', "'").replace(':', ' -')
    safe_author = author.replace('"', "'")
    
    prompt = f"""Tu es le distillateur de connaissances d'Arca-BrainOS. Transforme cette retranscription de vidéo YouTube en une note Obsidian structurée de haute qualité.

Métadonnées :
- Titre original : {safe_title}
- Auteur / Chaîne : {safe_author}
- URL source : {url}
- Date : {today}

Structure STRICTE attendue :
---
date_created: {today}
title: "{safe_title} avec {safe_author}"
description: "Synthèse conceptuelle et opérationnelle de la vidéo"
category: "media"
url: "{url}"
tags:
  - media
  - youtube
---
# 🎥 {safe_title}

## ⚡ Résumé Exécutif
(Un paragraphe dense et clair de 3 à 5 lignes résumant la thèse centrale).

## 💡 Idées Clés
* (Idée clé 1 : Explication en 2 phrases max avec timestamp exact [MM:SS])
* (Idée clé 2 avec timestamp)
* (Idée clé 3 avec timestamp)
* (Idée clé 4 avec timestamp)
* (Idée clé 5 avec timestamp)

## 🗣️ Citations Marquantes
> "Citation percutante 1"

> "Citation percutante 2"

## 🛠️ Actions Concrètes Proposées
- [ ] Action 1 directement actionnable.
- [ ] Action 2.
- [ ] Action 3.

## 📚 Références & Outils Mentionnés
* Livre / Auteur : Titre
* Concept / Outil : Nom

## 📝 Retranscription Détaillée & Notes de Synthèse
(Synthèse détaillée sous forme de 5 à 10 sous-points chronologiques avec timestamps [MM:SS] retraçant fidèlement l'argumentaire de la vidéo).

RÈGLES DE FORMATAGE ABSOLUES (ANTI-CHATTER) :
1. AUCUNE introduction (ne dis jamais "Voici la note...").
2. AUCUNE conclusion (ne dis jamais "J'espère que cela vous aide...").
3. Ta réponse doit commencer EXACTEMENT par le premier tiret `---` du frontmatter YAML et se terminer à la fin de la dernière section.
4. N'utilise JAMAIS de tiret cadratin (—). Utilise des deux-points, virgules ou parenthèses.

Retranscription de la vidéo :
{transcript}
"""

    res = subprocess.run(["agy", "--dangerously-skip-permissions", "-p", prompt], capture_output=True, text=True)
    if res.returncode == 0 and res.stdout.strip():
        # Écriture du fichier markdown
        with open(dest_file, "w", encoding="utf-8") as f_out:
            f_out.write(res.stdout.strip() + "\n")
PYEOF

        # 3. Validation de sécurité avant journalisation
        if [ -s "$CHEMIN_FINAL" ] && [ $(wc -c < "$CHEMIN_FINAL") -gt 150 ]; then
            echo "$url" >> "$FICHIER_HISTORIQUE"
            if [ -f "$FICHIER_LOG" ]; then
                echo "[$(date '+%Y-%m-%d %H:%M')] - Action IA (YouTube) : Nouvelle vidéo traitée depuis $url" >> "$FICHIER_LOG"
            fi
            echo "✅ Note créée avec succès : $CHEMIN_FINAL"
            NB_NOUVELLES=$((NB_NOUVELLES + 1))
        else
            echo "❌ Erreur : la génération a échoué pour $url. Fichier non inscrit dans l'historique."
            rm -f "$CHEMIN_FINAL"
        fi
    fi
done

if [ $NB_NOUVELLES -gt 0 ]; then
    echo "🎉 Batch complet ! $NB_NOUVELLES nouvelle(s) vidéo(s) ajoutée(s) dans Obsidian."
else
    echo "🎉 Batch complet ! Aucune nouvelle vidéo à traiter (tout est déjà à jour)."
fi

