# 🛠️ Skill : arca-organize-idea (Idea Structuring & Category Typing)

- **Reference Process:** [[Process-Inbox-Clean-and-Dispatch]]

## Trigger
Execute when user enters `arca-organize-idea` (or `arca-idea` / `organize-idea` / `brain-organize-idea`), optionally followed by a specific note title or wikilink in the Inbox.

## Objective
Analyze, qualify, and structure raw notes from `0-Inbox/` while preserving 100% of the original raw text under `## 📝 Raw Note`. Identifies the `category` (`idea`, `action`, `project-seed`, `source`), asks for confirmation when ambiguous, and routes tasks either to an active project `[[P-...]]` or to the central action buffer `0-Inbox/Emails-Actions-Todo.md`.

## Sequential Execution Workflow

1. **Target Note or Batch Scan:**
   - **Single Note Mode:** If a specific note is provided (e.g. `[[Note-Title]]`), target only that note in `0-Inbox/`.
   - **Batch Mode:** If no argument is provided, scan `0-Inbox/` for unqualified raw `.md` files (excluding subfolders and already qualified notes).

2. **Category & Target Diagnostic:**
   - Classify each note's intent:
     - 💡 **`category: idea`**: Free-floating conceptual thought (linked to a Theme MOC `[[T-...]]`) or project enrichment idea (`target: "[[P-...]]"`).
     - ⚡ **`category: action`**: Direct task to execute, either attached to an active project backlog (`target: "[[P-...]]"`) or qualified as a *stand-alone action* outside projects (destined for `0-Inbox/Emails-Actions-Todo.md`).
     - 🌱 **`category: project-seed`**: Major idea intended to become a full project (`P-`).
     - 📚 **`category: source`**: External raw resource (article, video) to be distilled via `arca-distill`.

3. **Interactive Validation (Chat Summary):**
   - Present the diagnostic with the proposed category and destination (`[[P-...]]` for a project action, or `0-Inbox/Emails-Actions-Todo.md` for a stand-alone action) and wait for user confirmation before writing.

4. **Execution & Application:**
   - **If `category: idea`:**
     - Apply `/_Arca-BrainOS/templates/Template-Idea.md`, strip residual `inbox` tags, preserve 100% of original text under `## 📝 Note Brute (Raw Note)`, synthesize key idea, and inject any resulting `- [ ]` actions into `[[P-...]]` (or `0-Inbox/Emails-Actions-Todo.md` for stand-alone actions).
   - **If `category: action`:**
     - Isolate the exact task to perform.
     - **Case A (Project Action):** Inject `- [ ]` directly into `## Actions todo next` of the target project `[[P-...]]`.
     - **Case B (Stand-alone Action outside projects):** Append `- [ ] <Description> (Source: Inbox Note [[Title]] on YYYY-MM-DD) #<domain>` under a timestamped section in `0-Inbox/Emails-Actions-Todo.md` (creating the file if it was previously purged).
     - Once injected, propose deleting (`rm`) the ephemeral action note in `0-Inbox/` (or moving it to `2-Ressources/Notes/` if it holds reference context worth keeping).
   - **If `category: project-seed`:**
     - Instantiate `P-[Project-Name].md` in `1-Projects/` using `Template-Project.md` with required `areas` and `themes`.
   - **If `category: source`:**
     - Route to `Skill_arca-distill.md`.

5. **Log:**
   - Record action in `/_Arca-BrainOS/log.md`:
     `[Date] - Action IA (Idea) : Qualification [category] for [[Note-Title]]`
