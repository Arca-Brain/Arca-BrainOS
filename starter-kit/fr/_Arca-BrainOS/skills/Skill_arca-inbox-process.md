# 🛠️ Skill : arca-inbox-process (Inbox Processing & Tri)

- **Processus de Référence :** [[Process-Inbox-Clean-et-Dispatch]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-inbox-process` (ou `inbox-process` / `brain-inbox-process`), éventuellement suivie du nom ou du lien d'une note spécifique dans l'Inbox.

## Objectif
Nettoyer, structurer et trier intelligemment les notes brutes présentes dans le dossier `0-Inbox`. Ce skill agit comme un routeur d'entrée : il identifie le type de catégorie (`category: idea`, `action`, `project-seed`, `source`), demande clarification si besoin, puis route vers la bonne compétence (`arca-organize-idea` ou `arca-distill`).

## Workflow d'Exécution Séquentiel

1. **Identification & Analyse Préliminaire :**
   - Si une note spécifique est fournie (ex: `[[Nom-de-note]]`), cible cette note dans `0-Inbox/`.
   - Si aucun argument n'est fourni, scanne le dossier `0-Inbox/` pour l'ensemble des fichiers `.md` (exclure sous-dossiers et fichiers cachés).
   - Pour chaque note, analyse son contenu brut.

2. **Gare de Triage & Identification de Category :**
   
   - **Détection des Doublons de Distillation :**
     - Scanne `/_Arca-BrainOS/log.md` pour vérifier si la source a déjà été distillée. Si oui, alerte dans le chat.

   - **Qualification de la `category` de capture :**
     - 📚 **`category: source`** (Lien vidéo/podcast, article, résumé tierce) $\rightarrow$ Aiguille vers `Skill_arca-distill.md`.
     - 💡 **`category: idea`** (Pensée volante libre OU idée d'enrichissement d'un projet cible `P-`) $\rightarrow$ Applique le workflow `Skill_arca-organize-idea.md` (Raw Note + Idée Clé + Actions & Maillage).
     - ⚡ **`category: action`** (Tâche directe à exécuter pour un projet) $\rightarrow$ Invoque `Skill_arca-organize-idea.md` pour injection dans le backlog de `target`.
     - 🌱 **`category: project-seed`** (Idée majeure destinée à créer un nouveau projet `P-`) $\rightarrow$ Invoque `Skill_arca-organize-idea.md` pour pré-créer la note `P-`.

3. **Phase Interactive & Validation :**
   - Si la catégorie ou le projet rattaché (`target`) est ambigu, présente les suggestions dans le chat et demande clarification à l'utilisateur.
   - Présente le brouillon qualifié avant écriture.
   - **Nettoyage YAML :** Retire systématiquement tout tag résiduel `inbox`, `O-Inbox`, `0-Inbox` ou `statut/inbox` du champ `tags` lors de la qualification ou du déplacement de la note.

4. **Clôture & Log :**
   - Enregistre l'action finale dans `/_Arca-BrainOS/log.md` :
     `[Date] - Action IA (Inbox) : Qualification et tri de [[Nom-de-note]]`
