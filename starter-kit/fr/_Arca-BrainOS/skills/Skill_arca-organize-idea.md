# 🛠️ Skill : arca-organize-idea (Organisation & Typage par Category)

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-organize-idea` (ou `arca-idea` / `organize-idea` / `brain-organize-idea`), éventuellement suivie du nom ou du lien d'une note spécifique dans l'Inbox.

## Objectif
Analyser, qualifier et structurer les notes brutes issues de l'Inbox. Le skill traite soit une note spécifique fournie en argument, soit l'ensemble des notes brutes en attente dans `0-Inbox/`. Il identifie la valeur du champ `category` (`idea`, `action`, `project-seed`, `source`), demande confirmation en cas d'ambiguïté, puis applique le traitement adapté.

## Workflow d'Exécution Séquentiel

1. **Périmètre & Scan des Contenus :**
   - **Mode Note Unique :** Si une note spécifique est fournie (ex: `[[Nom-de-note]]`), cible uniquement cette note dans `0-Inbox/`.
   - **Mode Batch (Inbox complète) :** Si aucun argument n'est fourni, scanne le dossier `0-Inbox/` pour l'ensemble des fichiers `.md` bruts non qualifiés.

2. **Diagnostic de Categorie & Analyse :**
   - Pour chaque note ciblée, analyse le contenu brut et détermine la `category` d'intention :
     - 💡 **`category: idea`** : 
       - *Pensée volante libre* : Réflexion conceptuelle sans projet cible immédiat (rattachée à un Thème MOC `[[T-...]]`).
       - *Idée d'enrichissement de projet* : Réflexion spécifique destinée à alimenter un projet existant (`target: "[[P-...]]"`).
     - ⚡ **`category: action`** : Tâche directe à effectuer ou à injecter dans un backlog de projet (`P-`).
     - 🌱 **`category: project-seed`** : Idée majeure destinée à devenir un projet à part entière (`P-`).
     - 📚 **`category: source`** : Ressource brute externe (article, vidéo) à distiller via `arca-distill`.

3. **Phase Interactive & Clarification (Synthèse dans le Chat) :**
   - **En Mode Note Unique :** Présente le diagnostic précis de la note avec la catégorie et la cible proposée.
   - **En Mode Batch :** Présente un tableau récapitulatif dans le chat de l'ensemble des notes analysées avec leur `category` et `target` suggérés.
   - Si une catégorie ou un projet cible est ambigu, demande clarification à l'utilisateur avant d'écrire les modifications.

4. **Exécution & Application des Changements :**

   - **Si `category: idea` :**
     - Applique `/_Arca-BrainOS/templates/Template-Idea.md`.
     - Insère `category: idea`, et `target: "[[Nom-Cible]]"`.
     - Conserve 100% de la saisie d'origine dans `## 📝 Note Brute`.
     - Formule la synthèse dans `## 🎯 Idée Clé & Synthèse`.
     - Génère les propositions d'enrichissement dans `## 🚀 Actions & Projets Impactés`.
     - Injecte les actions `- [ ]` dans le projet cible `[[P-...]]` si applicable.
     - Ajoute le maillage dans `## 🔗 Connexions & Maillage Sémantique`.

   - **Si `category: action` :**
     - Isole la tâche exacte à accomplir.
     - Injecte la tâche `- [ ]` directement dans la section `## 🚀 Actions Prochaines Étapes` du projet cible `[[P-...]]`.
     - Marque la note Inbox avec `category: action` et propose son archivage ou sa suppression.

   - **Si `category: project-seed` :**
     - Prépare l'amorce de la note de projet `P-[Nom-Projet].md` dans `1-Projects/` via `Template-Projet.md` en qualifiant obligatoirement l'Area rattachée (`areas: ["[[Nom-Domaine]]"]`) et le Thème MOC (`themes: ["[[T-Nom]]"]`).

   - **Si `category: source` :**
     - Redirige le traitement vers `Skill_arca-distill.md`.

5. **Clôture & Log :**
   - Enregistre chaque action dans `/_Arca-BrainOS/log.md` :
     `[Date] - Action IA (Idée) : Qualification [category] pour [[Nom-de-note]]`
