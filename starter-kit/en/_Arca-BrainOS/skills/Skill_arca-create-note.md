---
name: arca-create-note
description: Interactively instantiate and weave Project (P-), Theme (T-), or Area notes with human validation, detection of missing themes, and justification scan.
---

# 🛠️ Skill : arca-create-note (Creation, Chaining & Interactive Validation)

- **Reference Process:** [[Process-Inbox-Clean-and-Dispatch]] & [[Process-Cross-Project-Capitalization-and-MOC]]

## Specific Triggers & Direct Aliases

This skill is triggered by any of the following commands or aliases:

| Direct Command / Alias | Immediate Action Executed |
| :--- | :--- |
| `create-project`, `create-projet`, `arca-create-project`, `brain-create-project` | 🚀 Instantiates a **Project (`P-`)** in `PATH_PROJECTS` |
| `create-incubation`, `arca-create-incubation`, `brain-create-incubation` | 🌱 Instantiates an **Incubating Project (`P-`)** in `PATH_PROJECTS/_Incubation` |
| `create-theme`, `arca-create-theme`, `brain-create-theme` | 📜 Instantiates a **Theme (`T-`)** in `PATH_THEMES` |
| `create-domaine`, `create-area`, `arca-create-area`, `brain-create-area` | 🧠 Instantiates an **Area of Life** in `PATH_AREAS` |
| `create-note`, `arca-create-note`, `brain-create-note` | ❓ **Interactive Mode** (Asks what note type to create) |

---

## 🏛️ Golden Rule: Interactive Human Validation
Before creating or modifying any file on disk, the AI must present its diagnostic (attached Areas, existing Themes, new Themes/Areas to create, and linked Projects/Notes) and **ask for explicit user confirmation** in the chat.

---

## Sequential Execution Workflow

### 1. Routing by Invoked Alias:
- **If alias is specific** (e.g., `create-project` or `create-theme`) ➔ Skip qualification and jump directly to targeted branch.
- **If command is generic** (`create-note`) ➔ Ask user: *"Which type of note do you want to create: 1. Project (`P-`), 2. Theme (`T-`), or 3. Area of Life?"*

---

### 2. Branch A: Project Creation (`P-[Project-Name].md`)

1. **Contextual Analysis & Connection Scan:**
   - Analyze project title, context, or raw source note.
   - Determine project nature:
     - **Intellectual / research project:** Designed to connect to knowledge MOC cards (`themes`).
     - **Action-driven / practical project:** Purely operational execution, requiring no MOC Theme (`themes: []`).
   - Scan vault (`PATH_AREAS` and `PATH_THEMES`) to identify:
     - Relevant **existing Areas of Life** (`areas`).
     - **Suggested new Areas of Life** if no current area matches this life dimension.
     - Relevant **existing MOC Themes** (`themes`).
     - **Suggested new Themes** (if applicable for an intellectual project).

2. **Interactive Proposal to User:**
   Present diagnostic clearly in chat:
   - 📌 **Proposed Project Name:** `P-[Project-Name]`
   - 🚦 **Status & Location:**
     - **Active:** Created at the root of `PATH_PROJECTS` (`status: "active"`, tag `status/active`)
     - **Incubation (Someday/Maybe):** Created in `PATH_PROJECTS/_Incubation/` (`status: "someday"`, tag `status/someday`)
   - 🧠 **Area(s) of Life:**
     - Existing area: `[[Existing-Area]]`
     - New area required: `[[New-Area]]` *(Not found in `PATH_AREAS`: creation proposed)*
   - 📜 **MOC Theme(s):**
     - Intellectual project: `[[T-Existing-Theme]]` or `[[T-New-Theme]]` *(creation proposed)*
     - Practical project: *No theme needed (action-driven)* $\rightarrow$ `themes: []`
   - ⚠️ **Missing Area Safety Check:** If user requests no area, warn gently:
     > *"Note: Projects without an attached Area of Life will not appear in the Home.md dashboard focus matrix. We recommend associating at least one core life area."*
   - ❓ **Validation Request:** *"Do you approve this weaving and status (Active or Incubation)? Would you like to instantiate the new area(s) or theme(s) as well?"*

3. **Execution & Chaining (Post Explicit Validation):**
   - **If Active Project:** Instantiate `P-[Project-Name].md` in `PATH_PROJECTS` with `PATH_SYSTEM/templates/Template-Project.md` (`status: "active"`, tag `status/active`). Insert project entry under `### 🏁 Projets & chantiers de l'année` in attached Area notes (`PATH_AREAS`).
   - **If Incubating Project:** Instantiate `P-[Project-Name].md` in `PATH_PROJECTS/_Incubation/` with `PATH_SYSTEM/templates/Template-Project.md` (`status: "someday"`, tag `status/someday`). The project will automatically display in the incubation table of the attached Area.
   - **Area Chaining:** If a new area was approved, immediately instantiate `[New-Area].md` in `PATH_AREAS` with `PATH_SYSTEM/templates/Template-Area.md`, and register it in `PATH_AREAS/README.md`.
   - **Theme Chaining:** If a new theme was approved, immediately instantiate `T-New-Theme.md` in `PATH_THEMES` with `PATH_SYSTEM/templates/Template-Theme.md`.
   - Log creation and chained additions in `PATH_SYSTEM/log.md`.

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
   - Instantiate `[Area-Name].md` in `PATH_AREAS` with `PATH_SYSTEM/templates/Template-Area.md`.
   - Register entry in `PATH_AREAS/README.md`.
   - Update `areas` metadata in attached projects/themes.
   - Log action in `PATH_SYSTEM/log.md`.

---

## 🛡️ Safeguards & Safety
- **No Em Dashes:** Never use em dashes (`—`) in notes written for the user (use `:`, `,`, or `()`).
- **Mass Edit Threshold:** If creation/weaving impacts > 3 files simultaneously, request explicit confirmation in chat.
- **Transparency:** Provide concise execution report in exit message.
