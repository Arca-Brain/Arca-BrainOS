# 🛠️ Skill : arca-query (Le Pont Cognitif & Triage du Savoir)

- **Processus de Référence :** [[Process-Exploration-Semantique-et-Recherche]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape `arca-query` (ou `query` / `brain-query`) suivi d'une question, d'un concept ou d'une problématique de recherche.

## Objectif
Agir comme un pont cognitif dans le Second Cerveau en croisant le savoir déjà distillé, les sources brutes en attente dans l'Inbox, et en suggérant des opportunités de maillage ou des lacunes de connaissances (gaps).

## Workflow d'Exécution Séquentiel

1. **Recherche Multi-niveaux (Sémantique & Structure) :**
   - Effectue une recherche sémantique ciblée pour identifier les notes distillées concernées (`2-Ressources/IA-generated/AI-Distil-...`).
   - Effectue une recherche sémantique dans l'Inbox (`0-Inbox/` et ses sous-dossiers) pour trouver des sources brutes ou des notes en attente de traitement liées au sujet.
   - Parcourt les MOCs thématiques (`T-...`) dans `2-Ressources/Themes/` pour identifier où ces notes sont ancrées.

2. **Analyse de Structure & Gaps :**
   - Analyse si des notes distillées partagent des concepts forts mais ne sont pas reliées entre elles.
   - Identifie si des projets actifs (`P-...`) ou des notes de ressources sont concernés par la thématique mais manquent de liens vers les nouvelles synthèses.

3. **Formatage de la Réponse (Rapport Flash) :**
   Rédige une réponse structurée et concise dans le chat sous le format suivant :
   - **🧠 Savoir Distillé (Synthèse) :** Synthèse croisée et structurée de ce qui est déjà maîtrisé et ancré dans le Vault. Chaque affirmation forte doit être sourcée avec des wikilinks Obsidian `[[AI-Distil-Nom]]`.
   - **📥 Sources Brutes (Inbox) :** Liste des notes brutes, vidéos Youtube ou brouillons situés dans l'Inbox qui traitent de la thématique mais ne sont pas encore distillés.
   - **🕸️ Opportunités de Maillage (Gaps) :** Suggestions de liens ou de passerelles manquantes entre vos projets (`P-`), notes de connaissances et thèmes (`T-`) pour renforcer le maillage sémantique.

4. **Sauvegarde & Cristallisation (Optionnel) :**
   - Si la synthèse croisée apporte une forte valeur conceptuelle, propose à l'utilisateur de la sauvegarder sous forme de note de travail pérenne dans `2-Ressources/IA-generated/AI-Query-[Nom].md`.
   - **Règle de Journalisation :** N'écris dans `_Arca-BrainOS/log.md` que si l'utilisateur valide la création d'un fichier `AI-Query-...` (afin de ne pas polluer le journal avec de simples questions de chat). Le format de log à utiliser est :
     `[Date] - Action IA (Synthèse) : Création de la note de recherche [[AI-Query-[Nom]]]`
