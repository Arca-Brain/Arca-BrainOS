---
name: arca-create-note
description: Quickly instantiate a new Project (P-), Theme (T-), or Life Area with template, frontmatter, and auto-linking.
---

# 🛠️ Skill : arca-create-note (Structured Note Creation & Initialisation)

## Triggers & Direct Aliases

| Command / Alias | Immediate Action Executed |
| :--- | :--- |
| `create-project`, `arca-create-project` | 🚀 Instantiates a **Project (`P-`)** in `PATH_PROJECTS` |
| `create-theme`, `arca-create-theme` | 📜 Instantiates a **Theme (`T-`)** in `PATH_THEMES` |
| `create-area`, `arca-create-area` | 🧠 Instantiates a **Life Area** in `PATH_AREAS` |
| `create-note`, `arca-create-note` | ❓ **Interactive Mode** (Asks which note type to create) |

---

## Sequential Execution Workflow

### 1. Alias Routing:
- **If specific alias used** (e.g. `create-project`) ➔ Jump directly to targeted branch.
- **If generic command used** (`create-note`) ➔ Ask user: *"Which note type do you want to create: 1. Project (`P-`), 2. Theme (`T-`), or 3. Life Area?"*

### 2. Branch A : Project Creation (`P-[Project-Name].md`):
1. Sollicit title, area, and theme metadata.
2. Generate file using `Template-Projet.md` with clean YAML (`id`, `category: "Projet"`, `status: "active"`, `date_created`, `last_session`, `sessions_count: 0`, `total_real_duration: "0h00"`, `total_time_saved: "0h00"`).
3. Log initialization in `PATH_SYSTEM/log.md`.

### 3. Branch B : Theme Creation (`T-[Theme-Name].md`):
1. Sollicit title and area metadata.
2. Generate file using `Template-Theme.md` with clean YAML (`id`, `category: "Theme"`, `status: "active"`, `date_created`, `last_review`).
3. Log creation in `PATH_SYSTEM/log.md`.

### 4. Branch C : Life Area Creation (`[Area-Name].md`):
1. Generate file using `Template-Area.md`.
2. Update `PATH_AREAS/README.md` index.
3. Log creation in `PATH_SYSTEM/log.md`.
