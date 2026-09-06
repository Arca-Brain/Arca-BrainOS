---
date: 2026-08-09
title: "GETTING_STARTED.md : Detailed Onboarding & Operational Guide for Arca-BrainOS"
description: Operational walkthrough for setting up DataviewJS, understanding the adapted P.A.R.A methodology, configuring path variables in AGENTS.md, running Deep Work session management (arca-resume & arca-close-session), and using embedded process guides.
tags:
  - getting-started
  - onboarding
  - guide
  - obsidian
  - arca-brainos
status: "#completed"
---

# 🚀 GETTING STARTED: Detailed Onboarding & Operational Guide

🇫🇷 **[Lire la version française (GETTING_STARTED.fr.md)](GETTING_STARTED.fr.md)**

Welcome to **Arca-BrainOS**! This guide complements the high-level **[README.md](README.md)** Quickstart by providing detailed operational instructions for configuring your environment, understanding the underlying P.A.R.A architecture, running Deep Work sessions, and leveraging the 7 embedded process guides.

---

## 🧠 1. Conceptual Prerequisites & The Adapted P.A.R.A Framework

### A. Conceptual Prerequisite: Building a Second Brain (BASB)
While understanding the **Building a Second Brain (BASB)** methodology by Tiago Forte is **NOT required for software installation**, it is a **vital conceptual prerequisite** for getting the most out of Arca-BrainOS:

* **Why it matters:** Arca-BrainOS is engineered around Tiago Forte's **P.A.R.A System** (Projects, Areas, Resources, Archives) and the **C.O.D.E Framework** (Capture, Organize, Distill, Execute).
* **Cognitive Alignment:** Understanding the difference between time-bound active projects and open-ended life responsibilities ensures your AI agents route information accurately and maintain a zero-clutter vault.

---

### B. Detailed P.A.R.A Architecture & Vault Topography
Arca-BrainOS extends Tiago Forte's P.A.R.A structure into a 5-part decoupled directory hierarchy. Here is the exact structure, purpose, and concrete note examples for each folder:

```text
Your-Obsidian-Vault/
├── 0-Inbox/                      # 📥 Buffer & Raw Ingestion Zone
│   └── Youtube/                  # Raw YouTube transcript imports
├── 1-Projects/                   # 🚀 Active Projects (P-[Name].md) & Incubation (_Incubation/)
├── 2-Ressources/                 # 📚 Knowledge Base (Notes/, IA-generated/, Themes/)
├── 3-Domaines-de-vie/            # 🧠 Permanent Life Areas (README.md Index)
└── 4-Archives/                   # 📦 Completed Work & Inactive Items
```

#### 📥 `0-Inbox/` (Buffer & Ingestion Zone)
- **Purpose:** Temporary holding area for unorganized thoughts, web clips, meeting notes, and raw YouTube transcripts before processing.
- **Rule:** Maintained at "Inbox Zero" using `arca-inbox-process` or `arca-organize-idea`.
- **Examples:** `0-Inbox/raw-thought-on-ai.md`, `0-Inbox/Youtube/transcript-deepmind.md`.

#### 🚀 `1-Projects/` (Active Endeavors & Incubation)
- **Purpose:** Short to medium-term active projects with defined goals, milestones, and completion dates. Also hosts the `_Incubation/` subfolder for dormant projects (Someday/Maybe).
- **Convention:** Notes follow the `P-[Project-Name].md` format and leverage `Template-Project.md` (`status: active` or `status: someday`).
- **Examples:** `1-Projects/P-Arca-BrainOS.md`, `1-Projects/_Incubation/P-System-Migration.md`.

#### 📚 `2-Ressources/` (Knowledge Base)
Divided into 3 distinct layers to maintain total separation between human reflection and AI processing:
1. **`2-Ressources/Notes/` (Human Writing):** Personal reflections, manual summaries, and long-term reference material authored by you.  
   *Examples:* `Notes/Principles-of-Zettelkasten.md`, `Notes/Meeting-Notes-2026.md`.
2. **`2-Ressources/IA-generated/` (Autonomous AI Write Zone):** Isolated write-only container where AI agents store conceptual distillations (`AI-Distil-[Topic].md`) and synthesis guides (`AI-Synthesis-...`).  
   *Examples:* `IA-generated/AI-Distil-Hermes-Agent.md`, `IA-generated/AI-Synthesis-Workflow.md`.
3. **`2-Ressources/Themes/` (Maps of Content / MOCs):** Master index cards starting with `T-` that group wikilinks (`[[...]]`) by subject.  
   *Examples:* `Themes/T-Intelligence-Artificielle.md`, `Themes/T-PKM.md`.

#### 🧠 `3-Domaines-de-vie/` (Life Areas & Long-Term Responsibilities)
- **Purpose:** Permanent areas of life and ongoing standards of quality without an end date.
- **Convention:** Indexed via `3-Domaines-de-vie/README.md` and framed by `Template-Area.md`.
- **Examples:** `3-Domaines-de-vie/Creativite.md`, `3-Domaines-de-vie/Sante.md`, `3-Domaines-de-vie/Travail.md`.

#### 📦 `4-Archives/` (Completed & Retired Content)
- **Purpose:** Cold storage for finished projects and inactive life areas, preserving historical memory.
- **Sub-folders:** `4-Archives/Projets/` and `4-Archives/Areas/`.

---

## ⚙️ 2. Detailed Environment & Plugin Configuration

### A. Dataview Plugin Configuration (Crucial)
Arca-BrainOS powers its executive cockpit (`Home.md`) and life area focus widgets through **DataviewJS**. Without JS queries enabled, these widgets will not render.

1. Open Obsidian **Settings $\rightarrow$ Community Plugins**.
2. Install and enable **Dataview**.
3. Under **Dataview Settings**, verify that:
   - ✅ **Enable JavaScript Queries** (`dataviewjs`) is **ON**.
   - ✅ **Enable Inline JavaScript Queries** is **ON**.

### B. Configuring Custom Vault Paths in `AGENTS.md`
Arca-BrainOS is 100% folder-agnostic. The core engine lives inside `_Arca-BrainOS/`. If your vault uses custom folder names (for example `Inbox/` instead of `0-Inbox/`), update the top variables in `_Arca-BrainOS/AGENTS.md`:

```yaml
# 🌐 Vault Topography Variables (AGENTS.md)
PATH_INBOX: "0-Inbox/"
PATH_PROJECTS: "1-Projects/"
PATH_INCUBATION: "1-Projects/_Incubation/"
PATH_AREAS: "3-Domaines-de-vie/"
PATH_THEMES: "2-Ressources/Themes/"
PATH_IA_GENERATED: "2-Ressources/IA-generated/"
PATH_SYSTEM: "_Arca-BrainOS/"
```

### C. Web Ingestion with Official Obsidian Web Clipper Extension
To capture articles, web pages, and documentation directly from your browser into your vault with zero manual friction:
1. Install the official **[Obsidian Web Clipper](https://obsidian.md/clipper)** extension (`https://obsidian.md/clipper`) on your browser (Chrome, Firefox, Safari, Brave).
2. Set the default destination folder to `0-Inbox/`.
3. Captured web pages are automatically formatted into clean Markdown with frontmatter (`title`, `url`, `date`), ready for qualification by `arca-inbox-process` or distillation by `arca-distill`.

---

## 🪄 3. Installation Protocol (2 Options)

* **📁 Option A: Add to an Existing Vault (Directory `starter-kit/en/_Arca-BrainOS/`)**  
  Copy `starter-kit/en/_Arca-BrainOS/` into your existing vault root and prompt your AI terminal runner:
  ```text
  Read https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.md (or local INSTALL.md) and install Arca-BrainOS for me.
  ```
* **📦 Option B: Fresh Start with Ready-to-Use Vault (Directory `starter-kit/en/starter-vault/`)**  
  Open `starter-kit/en/starter-vault/` directly in Obsidian. Upon opening, read the welcome note **`00-START-HERE.md`** at the root to test your first 3 agentic commands in under 5 minutes.  
  > 💡 **Tip:** Rename `starter-vault/` to a custom name (`ArcaBrain`, `2ndBrain`, `MyVault`) before or after opening it!

---

## 🧪 4. Vault Verification (`arca-test`)

Run the automated test suite in your AI terminal to verify path resolution and frontmatter compliance:

```bash
arca-test
```

---

## 🪵 5. Deep Work Session Management (`arca-resume` & `arca-close-session`)

Arca-BrainOS introduces a structured, two-step session management protocol for project execution:

### Step 1: Cognitive Session Framing (`arca-resume`)
Before starting a Deep Work session on a project note (e.g., `1-Projects/P-MyProject.md`), type:

```bash
arca-resume 1-Projects/P-MyProject.md
```

**What your AI co-pilot does:**
1. Scans recent session entries in the project worklog.
2. Identifies current milestones and open tasks.
3. Formulates a proposed **Session Intention** (2-3 focused actions).
4. Opens an active session entry with timestamp in the project's `## 🪵 Journal de Bord des Sessions` and logs the event in `_Arca-BrainOS/log.md`.

### Step 2: Session Closure & ROI Logging (`arca-close-session`)
When you finish your work session, type:

```bash
arca-close-session 1-Projects/P-MyProject.md
```

**What your AI co-pilot does:**
1. Tallies completed tasks and checks remaining items.
2. Prompts you for real session duration.
3. Calculates net time saved and speed multiplier metrics.
4. Finalizes the session entry in the project worklog and appends a single-line audit record to `_Arca-BrainOS/log.md`.

---

## 📚 6. Leveraging Embedded Process Guides (`process/`)

To understand the core logic of each step and guide your AI co-pilot, refer to the 7 embedded process guides in `_Arca-BrainOS/process/`:

* **`Process-Inbox-Clean-et-Dispatch.md`**: Inbox qualification, YAML cleaning, and dispatching.
* **`Process-Ingestion-et-Distillation-de-Medias.md`**: Media transcript synthesis and theme anchoring.
* **`Process-Exploration-Semantique-et-Recherche.md`**: Semantic RAG search and cognitive bridging.
* **`Process-Audit-et-Maintenance-du-Vault.md`**: PARA vault health diagnostics and link health audit.
* **`Process-Pilotage-de-Projets-et-Deep-Work.md`**: Deep Work session framing and logging.
* **`Process-Capitalisation-et-Synthese-MOC.md`**: Knowledge synthesis and Theme MOC updates.
* **`Process-Test-et-Evaluation-Agentique.md`**: Test harness suite and automated assertions.

---

## 🔗 Useful Links & References
* 📜 **[The Sovereign AI Workflow Manifesto](MANIFESTO.md)**
* 🪄 **[Installer Prompt (INSTALL.md)](INSTALL.md)**
* 🤝 **[Contribution Guidelines (CONTRIBUTING.md)](CONTRIBUTING.md)**
* ⚖️ **[Dual License Agreement (LICENSE.md)](LICENSE.md)**
