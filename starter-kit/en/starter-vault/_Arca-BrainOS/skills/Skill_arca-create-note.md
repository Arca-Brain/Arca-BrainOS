---
name: arca-create-note
description: Interactively instantiate and weave Project (P-), Theme (T-), or Area notes with human validation, detection of missing themes, and justification scan.
---

# 🛠️ Skill: arca-create-note (Interactive Creation, Chaining & Validation)

## Triggers & Specific Aliases

This skill is triggered by any of the following commands or aliases:

| Direct Command / Alias | Action Executed |
| :--- | :--- |
| `create-project`, `create-projet`, `arca-create-project`, `brain-create-project` | 🚀 Instantiates a **Project (`P-`)** in `PATH_PROJECTS` |
| `create-theme`, `arca-create-theme`, `brain-create-theme` | 📜 Instantiates a **Theme (`T-`)** in `PATH_THEMES` |
| `create-domaine`, `create-area`, `arca-create-area`, `brain-create-area` | 🧠 Instantiates an **Area of Life** in `PATH_AREAS` |
| `create-note`, `arca-create-note`, `brain-create-note` | ❓ **Interactive Mode** (Prompts for note type) |

---

## 🏛️ Golden Rule: Interactive Human Validation
Before writing or modifying any file on disk, the AI MUST present its proposed analysis (attached Areas of Life, existing MOC Themes, new Themes to create, and linked Projects/Notes) and **request explicit user confirmation** in the chat.

---

## Sequential Execution Workflow

### 1. Routing by Alias:
- **If alias is specific** (e.g. `create-project` or `create-theme`) ➔ Skip qualification prompt and run the target branch.
- **If command is generic** (`create-note`) ➔ Ask user: *"Which type of note do you want to create: 1. Project (`P-`), 2. Theme (`T-`), or 3. Area of Life?"*

---

### 2. Branch A: Project Creation (`P-[Project-Name].md`)

1. **Contextual Analysis & Connection Scan:**
   - Analyze project title, context, or raw source note.
   - Scan vault (`PATH_AREAS` and `PATH_THEMES`) to identify:
     - Relevant **Areas of Life** (`areas`).
     - Relevant **existing MOC Themes** (`themes`).
     - **Suggested new Themes** that do not exist yet in `PATH_THEMES`.

2. **Interactive Proposal to User:**
   Present diagnostic clearly in chat:
   - 📌 **Proposed Project Name:** `P-[Project-Name]`
   - 🧠 **Suggested Attached Area(s):** `[[Area-1]]`, `[[Area-2]]`
   - 📜 **Suggested Existing Theme(s):** `[[T-Existing-Theme]]`
   - 🆕 **Suggested New Theme(s) to Create:** `[[T-New-Theme]]` *(Not found in `PATH_THEMES`)*
   - ❓ **Validation Request:** *"Do you approve this weaving? Would you like to instantiate the new theme(s) `[[T-New-Theme]]` as well?"*

3. **Execution & Chaining (Post Explicit Validation):**
   - Instantiate `P-[Project-Name].md` in `PATH_PROJECTS` with [`Template-Projet.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Projet.md).
   - If approved, **immediately chain creation** of new theme `T-New-Theme.md` in `PATH_THEMES` with [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md).
   - **Bidirectional Link:** Insert project entry under `### 🏁 Projets & chantiers de l'année` in attached Area notes (`PATH_AREAS`).
   - Log creation in `PATH_SYSTEM/log.md`.

---

### 3. Branch B: Theme Creation (`T-[Theme-Name].md`)

1. **Contextual Analysis & Connection Scan:**
   - Analyze theme scope and vision.
   - Scan `PATH_AREAS` for parent **Area(s) of Life** (`areas`).
   - Scan `PATH_PROJECTS`, `PATH_ARCHIVES`, and `PATH_NOTES` for **existing Projects and Notes** that belong to this theme.

2. **Interactive Proposal to User:**
   Present diagnostic clearly in chat:
   - 📜 **Proposed Theme Name:** `T-[Theme-Name]`
   - 🧠 **Suggested Parent Area(s):** `[[Parent-Area]]`
   - 🔗 **Existing Projects & Notes to Link:** `[[P-Project-1]]`, `[[Note-1]]`
   - ❓ **Validation Request:** *"Do you confirm creating this theme and linking these existing notes/projects?"*

3. **Execution (Post Explicit Validation):**
   - Instantiate `T-[Theme-Name].md` in `PATH_THEMES` with [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md).
   - Update `themes` metadata in validated projects/notes.
   - Link theme to parent Area notes.
   - Log action in `PATH_SYSTEM/log.md`.

---

### 4. Branch C: Area Creation (`[Area-Name].md`)

1. **Justification Scan & Vault Audit:**
   - Scan entire vault (`PATH_PROJECTS`, `PATH_ARCHIVES`, `PATH_THEMES`, `PATH_NOTES`) to build a **justification report**: identify active/archived projects, themes, and orphan notes that justify opening a new Area of responsibility.

2. **Interactive Proposal & Justification Report:**
   Present to user:
   - 🧠 **Proposed Area Name:** `[Area-Name]`
   - 📊 **Justification Analysis (Relevant Vault Content):**
     - Active & archived projects to group: `[[P-Project-A]]`, `[[P-Project-B]]`
     - Associated themes: `[[T-Theme-X]]`
   - 🎯 **Proposed scope & standard of excellence.**
   - ❓ **Validation Request:** *"Do you confirm creating this Area of Life and grouping these projects/themes?"*

3. **Execution (Post Explicit Validation):**
   - Instantiate `[Area-Name].md` in `PATH_AREAS` with [`Template-Area.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Area.md).
   - Register entry in `PATH_AREAS/README.md`.
   - Update `areas` metadata in attached projects/themes.
   - Log action in `PATH_SYSTEM/log.md`.

---

## 🛡️ Safeguards & Safety
- **No Em Dashes:** Never use em dashes (`—`) in notes written for the user (use `:`, `,`, or `()`).
- **Mass Edit Threshold:** If creation/weaving impacts > 3 files simultaneously, request explicit confirmation in chat.
- **Transparency:** Provide concise execution report in exit message.
