#!/bin/bash

# --- CONFIGURATION ---
# Remplacez par l'URL de votre playlist YouTube (Non répertoriée)
PLAYLIST_URL="VOTRE_URL_DE_PLAYLIST_ICI"

# Chemins vers votre dossier Obsidian (relatifs ou absolus)
DOSSIER_VIDEOS="./0-Inbox/Youtube"
FICHIER_HISTORIQUE="./_Arca-BrainOS/scripts/historique_youtube_log.md"

# Créer le dossier et le fichier d'historique s'ils n'existent pas
mkdir -p "$DOSSIER_VIDEOS"
touch "$FICHIER_HISTORIQUE"

echo "🔍 Scan de la playlist..."

# yt-dlp récupère instantanément toutes les URLs de la playlist
URLS_PLAYLIST=$(yt-dlp --flat-playlist --get-url "$PLAYLIST_URL")

for url in $URLS_PLAYLIST; do
    # On vérifie si l'URL est déjà dans notre fichier d'historique
    if ! grep -q "$url" "$FICHIER_HISTORIQUE"; then
        echo "⚡ Nouvelle vidéo détectée : $url"
        
        # 1. Obtenir le titre propre
        TITRE_FICHIER=$(antigravity-cli -prompt "Donne-moi UNIQUEMENT le titre de la vidéo $url traduit en Français, max 5 mots, sans ponctuation.")
        NOM_FICHIER=$(echo "$TITRE_FICHIER" | tr ' ' '-')
        CHEMIN_FINAL="$DOSSIER_VIDEOS/$NOM_FICHIER.md"
        
        echo "📝 Génération de la note dans $CHEMIN_FINAL..."
        
        # 2. Exécuter l'ingestion YouTube avec l'agent IA
        arca-youtube "$url" > "$CHEMIN_FINAL"
        
        # 3. Consigner l'URL dans le registre
        echo "$url" >> "$FICHIER_HISTORIQUE"
        echo "✅ Traitement terminé."
    fi
done

echo "🎉 Scan terminé !"
