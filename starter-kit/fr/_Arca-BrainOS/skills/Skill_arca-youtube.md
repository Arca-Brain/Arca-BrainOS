# 🛠️ Skill : arca-youtube

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape `arca-youtube` (ou `brain-youtube`) suivi d'une URL YouTube.

## Workflow d'Exécution
1. **Extraction :** Récupère la retranscription de la vidéo fournie.
2. **Génération :** Applique strictement les règles de formatage du template pour extraire l'essence du contenu.
3. **Sauvegarde :** Crée le fichier généré directement dans le dossier `0-Inbox/Youtube/`.
4. **Journalisation :** Ajoute une ligne dans `_Arca-BrainOS/log.md` : `[Date] - Action IA (YouTube) : Nouvelle vidéo traitée depuis [URL]`.
