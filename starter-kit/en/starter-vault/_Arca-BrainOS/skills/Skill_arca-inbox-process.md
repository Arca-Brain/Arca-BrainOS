# 🛠️ Skill : arca-inbox-process (Inbox Processing & Triage)

- **Reference Process:** [[Process-Inbox-Clean-and-Dispatch]]

## Trigger
Execute when user enters `arca-inbox-process` (or `inbox-process` / `brain-inbox-process`), optionally followed by a note title or wikilink.

## Objective
Clean, structure, and route raw notes and documents in `0-Inbox/`. Acts as an entry router: identifies the category (`category: idea`, `action`, `project-seed`, `source`, `note`), enforces factual link and action verification in the target project, requests clarification if ambiguous, then routes to the appropriate skill (`arca-organize-idea`, `arca-distill`, or project linkage).

## Sequential Execution Workflow

1. **Identification & Preliminary Analysis:**
   - If a specific note is provided (e.g. `[[Note-Title]]`), target that note in `0-Inbox/`.
   - If no argument is provided, scan all `.md` files in `0-Inbox/` (excluding subfolders, hidden files, and the staging buffer `Emails-Actions-Todo.md` reserved for `arca-task-process`).
   - Analyze raw content and YAML frontmatter for each note.

2. **Triage & Category Qualification:**
   - **Distillation Duplicate Check:** Check `/_Arca-BrainOS/log.md` to ensure source was not already distilled.
   - **Category Mapping:**
     - 📚 **`category: source`** (Web article, video/podcast link, external document) ➔ Route to `Skill_arca-distill.md`.
     - 💡 **`category: idea`** (Fleeting thought or project idea) ➔ Apply `Skill_arca-organize-idea.md` (Raw Note + Key Idea + Actions & Links).
     - ⚡ **`category: action`** (Direct task to execute) ➔ Invoke `Skill_arca-organize-idea.md` with destination routing:
       - *Case A (Project Action):* If linked to an active project `1-Projects/P-*.md`, propose injecting it into the backlog of `target: "[[P-...]]"`.
       - *Case B (Stand-alone Action outside projects):* If the action is a standalone task unrelated to any active `P-` project (administrative errand, health, finance, reminder), propose appending it to the central buffer `0-Inbox/Emails-Actions-Todo.md` (for downstream processing by `arca-task-process` into Todoist), followed by deleting (`rm`) the ephemeral action note (or moving it to `2-Ressources/Notes/` if it contains reference material worth keeping).
     - 🌱 **`category: project-seed`** (Major idea aimed at becoming a full project `P-`) ➔ Invoke `Skill_arca-organize-idea.md` to pre-create project note.
     - 📝 **`category: note`** (Session deliverable, strategic analysis, working document) ➔ Verify project linkage (see rule below) then move to `2-Ressources/Notes/`.

3. **Factual Link & Action Verification (Anti-Orphan Rule):**
   - **Never Presume:** Never assume a note is already linked or processed simply because it appears in `log.md`. `log.md` is only a chronological execution journal.
   - **Factual Anomaly Check:** Systematically perform a text search (`grep`) to verify if the wikilink `[[Note-Title]]` actually exists in the target project note (`target: "[[P-...]]"`) or theme (`themes: [...]`).
   - **Mandatory Double-Linking for Deliverables and Working Notes:**
     1. *Working Documents:* If the note is not referenced under `## 🗺️ Working Documents` in the target project, propose adding it with a clear label.
     2. *Residual Actions:* Scan the note for uncompleted decisions, experiments, technical recommendations, or operational tasks not yet tracked in the project backlog. Formulate and propose a concrete `- [ ]` task: either in `## Actions todo next` of the target project `[[P-...]]` (project action), or in `0-Inbox/Emails-Actions-Todo.md` if it is a standalone action outside any project.
   - **Move Condition:** No file may be moved (`mv`) out of `0-Inbox/` into `2-Ressources/Notes/` until this double-linking (Working Documents link + todo action if applicable) is formally confirmed and applied.

4. **Interactive Phase & Validation:**
   - If category or target project is ambiguous, present suggestions in chat and ask user for confirmation.
   - Present the detailed triage plan before modifying files.
   - **YAML Cleanup:** Systematically strip any residual `inbox`, `O-Inbox`, `0-Inbox`, or `statut/inbox` tags from the `tags` list.

5. **Completion & Log:**
   - Record the final action in `/_Arca-BrainOS/log.md`:
     `[Date] - Action IA (Inbox) : Qualification et tri de [[Note-Title]]`
