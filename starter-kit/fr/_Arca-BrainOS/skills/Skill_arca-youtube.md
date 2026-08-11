# 🛠️ Skill : arca-youtube

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape `arca-youtube` (ou `brain-youtube`) suivi d'une URL YouTube.

## Objectif
Extraire la retranscription et la substance conceptuelle d'une vidéo YouTube pour générer une note d'inbox structurée, dense et directement exploitable.

## Workflow d'Exécution Séquentiel

1. **Extraction de la Retranscription :**
   - Récupère le titre, l'auteur/chaîne, les timestamps et le texte de la retranscription de l'URL fournie.

2. **Génération de la Note de Synthèse :**
   - Applique strictly le modèle `/_Arca-BrainOS/templates/Template-Transcript-Media.md`.
   - Extrait le résumé exécutif, les idées clés avec repères temporels `[00:00]`, les citations marquantes, les actions concrètes et les références citées.

3. **Sauvegarde dans l'Inbox :**
   - Sauvegarde la note générée dans `0-Inbox/Youtube/` (ex: `0-Inbox/Youtube/transcript-[titre-video].md`).

4. **Journalisation Système & Registre :**
   - Consigne l'URL dans le registre `/_Arca-BrainOS/scripts/historique_youtube_log.md` pour éviter le traitement en doublon.
   - Ajoute la ligne d'action dans `/_Arca-BrainOS/log.md` :
     `[AAAA-MM-JJ HH:mm] - Action IA (YouTube) : Nouvelle vidéo traitée depuis [URL]`

---

## 🚫 Règles de Formatage Strictes (Anti-Chatter)
1. Génère exclusivement le contenu du fichier Markdown.
2. **AUCUNE introduction** (ne dis pas "Voici la note de synthèse").
3. **AUCUNE conclusion** (ne dis pas "J'ai terminé l'analyse").
4. La réponse doit démarrer exactement par les trois tirets du frontmatter `---` et se terminer à la fin du résumé détaillé.
