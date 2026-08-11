#!/bin/bash

# --- CONFIGURATION ---
# Replace with your YouTube playlist URL (Unlisted recommended)
PLAYLIST_URL="YOUR_PLAYLIST_URL_HERE"

# Paths to your Obsidian directories
DOSSIER_VIDEOS="./0-Inbox/Youtube"
FICHIER_HISTORIQUE="./_Arca-BrainOS/scripts/historique_youtube_log.md"

# Create folder and registry if they don't exist
mkdir -p "$DOSSIER_VIDEOS"
touch "$FICHIER_HISTORIQUE"

echo "🔍 Scanning YouTube playlist..."

# yt-dlp fetches playlist video URLs
URLS_PLAYLIST=$(yt-dlp --flat-playlist --get-url "$PLAYLIST_URL")

for url in $URLS_PLAYLIST; do
    # Check if URL was already processed
    if ! grep -q "$url" "$FICHIER_HISTORIQUE"; then
        echo "⚡ New video detected: $url"
        
        # 1. Get clean title
        TITRE_FICHIER=$(antigravity-cli -prompt "Give me ONLY the title of video $url translated to English, max 5 words, no punctuation.")
        NOM_FICHIER=$(echo "$TITRE_FICHIER" | tr ' ' '-')
        CHEMIN_FINAL="$DOSSIER_VIDEOS/$NOM_FICHIER.md"
        
        echo "📝 Generating note in $CHEMIN_FINAL..."
        
        # 2. Execute YouTube ingestion via AI agent
        arca-youtube "$url" > "$CHEMIN_FINAL"
        
        # 3. Append URL to registry
        echo "$url" >> "$FICHIER_HISTORIQUE"
        echo "✅ Video processing complete."
    fi
done

echo "🎉 Batch complete!"
