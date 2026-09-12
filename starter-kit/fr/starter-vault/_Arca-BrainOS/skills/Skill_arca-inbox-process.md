# 🛠️ Skill : arca-inbox-process (Inbox Processing & Tri)

- **Processus de Référence :** [[Process-Inbox-Clean-et-Dispatch]]

## Déclencheur
Exécute ce workflow lorsque l'utilisateur tape la commande `arca-inbox-process` (ou `inbox-process` / `brain-inbox-process`), éventuellement suivie du nom ou du lien d'une note spécifique dans l'Inbox.

## Objectif
Nettoyer, structurer et trier intelligemment les notes brutes et documents présents dans le dossier `0-Inbox`. Ce skill agit comme un routeur d'entrée : il identifie la catégorie (`category: idea`, `action`, `project-seed`, `source`, `note`), effectue une vérification factuelle des liens et actions dans le projet cible, demande clarification si besoin, puis route vers la bonne compétence (`arca-organize-idea`, `arca-distill`, ou maillage projet).

## Workflow d'Exécution Séquentiel

1. **Identification & Analyse Préliminaire :**
   - Si une note spécifique est fournie (ex: `[[Nom-de-note]]`), cible cette note dans `0-Inbox/`.
   - Si aucun argument n'est fourni, scanne le dossier `0-Inbox/` pour l'ensemble des fichiers `.md` (exclure sous-dossiers et fichiers cachés).
   - Pour chaque note, analyse son contenu brut et ses métadonnées YAML.

2. **Gare de Triage & Qualification de Category :**
   
   - **Détection des Doublons de Distillation :**
     - Scanne `/_Arca-BrainOS/log.md` pour vérifier si la source a déjà été distillée. Si oui, alerte dans le chat.

   - **Qualification de la `category` de capture :**
     - 📚 **`category: source`** (Lien vidéo/podcast, article web, document externe) $\rightarrow$ Aiguille vers `Skill_arca-distill.md`.
     - 💡 **`category: idea`** (Pensée volante libre ou idée d'enrichissement) $\rightarrow$ Applique le workflow `Skill_arca-organize-idea.md` (Raw Note + Idée Clé + Actions & Maillage).
     - ⚡ **`category: action`** (Tâche directe à exécuter pour un projet) $\rightarrow$ Invoque `Skill_arca-organize-idea.md` pour injection dans le backlog de `target`.
     - 🌱 **`category: project-seed`** (Idée majeure destinée à créer un nouveau projet `P-`) $\rightarrow$ Invoque `Skill_arca-organize-idea.md` pour pré-créer la note `P-`.
     - 📝 **`category: note`** (Livrable de session, analyse stratégique, note de cadrage) $\rightarrow$ Vérifier le maillage projet (voir règle ci-dessous) puis déplacer vers `2-Ressources/Notes/`.

3. **Vérification Factuelle des Liens et Actions (Règle Anti-Orphelin) :**
   - **Interdiction de présomption :** Ne JAMAIS supposer qu'une note est déjà maillée ou traitée simplement parce qu'elle figure dans `log.md`. `log.md` n'est qu'un journal d'exécution chronologique.
   - **Contrôle d'ancrage factuel :** Effectuer systématiquement une recherche textuelle (`grep`) pour vérifier si le wikilink `[[Nom-de-note]]` est réellement présent dans la note cible (`target: "[[P-...]]"` ou dans les thèmes `T-`).
   - **Double maillage obligatoire pour tout livrable / note de travail :**
     1. *Working Documents :* Si la note n'est pas référencée dans la section `## 🗺️ Working Documents` du projet cible, proposer son ajout avec un libellé clair.
     2. *Actions résiduelles :* Scanner le contenu de la note pour détecter si elle contient des arbitrages, expérimentations, recommandations techniques ou étapes opérationnelles non encore inscrites au backlog. Si oui, formuler et proposer une tâche `- [ ]` explicite dans `## Actions todo next` du projet cible.
   - **Condition de déplacement :** Aucun fichier ne doit être déplacé (`mv`) hors de `0-Inbox/` vers `2-Ressources/Notes/` tant que ce double maillage (lien Working Documents + action todo si requise) n'est pas formellement acté.

4. **Phase Interactive & Validation :**
   - Si la catégorie ou le projet rattaché (`target`) est ambigu, présente les suggestions dans le chat et demande clarification à l'utilisateur.
   - Présente le plan de triage détaillé (catégorie, projet cible, liens et actions à ajouter, destination) avant toute modification de fichier.
   - **Nettoyage YAML :** Retire systématiquement tout tag résiduel `inbox`, `O-Inbox`, `0-Inbox` ou `statut/inbox` du champ `tags` lors de la qualification ou du déplacement de la note.

5. **Clôture & Log :**
   - Enregistre l'action finale dans `/_Arca-BrainOS/log.md` :
     `[Date] - Action IA (Inbox) : Qualification et tri de [[Nom-de-note]]`
