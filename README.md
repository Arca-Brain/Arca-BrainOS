---
date: 2026-08-08
title: "Arca-BrainOS : Official GitHub Open-Source Release"
description: "Official README for the open-source release of Arca-BrainOS on GitHub."
tags:
  - readme
  - github
  - open-source
  - arca-brainos
status: "#completed"
---

# 🧠 Arca-BrainOS

> *"My ark is not a refuge, it is an engine... Dream conceives, but action alone accomplishes."*  
> **Fernando Pessoa**  
>  
> *(Inspired by Fernando Pessoa's legendary wooden trunk, "A Arca", holding thousands of unorganized fragments, manuscripts, and heteronyms waiting to become a universe. Arca-BrainOS is that execution engine for your digital mind.)*

---

**Sovereign agentic workflow & local co-pilot for Obsidian**

🇫🇷 **[Lire la version française (README.fr.md)](README.fr.md)**

[![Obsidian](https://img.shields.io/badge/Obsidian-Vault%20Ready-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md)
[![License: Dual AGPLv3 / CC BY-NC-SA 4.0](https://img.shields.io/badge/License-Dual%20AGPLv3%20%2F%20CC%20BY--NC--SA%204.0-blue?style=flat-square)](LICENSE)
[![LLM Agnostic](https://img.shields.io/badge/LLM-Agnostic%20%26%20Portable-emerald?style=flat-square)](#-key-design-principles)
[![ROI Speed](https://img.shields.io/badge/ROI-Speed%20x3%20⚡-orange?style=flat-square)](#-proven-field-roi--metrics)
[![Built with Google Antigravity](https://img.shields.io/badge/Built_with-Google%20Antigravity-4285F4?style=flat-square&logo=google&logoColor=white)](https://github.com/chug/Arca-BrainOS)

**[Quickstart](#-quickstart-1-minute-onboarding)** · **[Getting Started](GETTING_STARTED.md)** · **[Manifesto](MANIFESTO.md)** · **[Agentic Skills](#-the-agentic-skills-arsenal)** · **[Architecture](#-architecture--vault-topography-2-part-decoupled-design)** · **[Contributing](CONTRIBUTING.md)** · **[FAQ](#-faq)**


---

> 🎯 **Core Concept:** Move from scattered thoughts and fragmented AI tools to a persistent, AI-native operating system that executes cognitive workflows directly inside your local Obsidian Markdown vault.


### ⭐ If Arca-BrainOS is useful to you, star the repository!

Stars help more thinkers and builders find the project and keep it moving forward.

[![Star Arca-BrainOS on GitHub](https://img.shields.io/badge/Star%20Arca--BrainOS%20on%20GitHub-⭐-8B5CF6?style=for-the-badge&logo=github&logoColor=white)](https://github.com/chug/Arca-BrainOS)


---

## 💥 The Problem: Why Most Second Brains Rot

Building a Second Brain (PKM) often turns into a friction and maintenance trap:

* **Fragmented Ecosystems & Walled-Garden SaaS:** Your thoughts, documents, and workflows are scattered across multiple repositories, web tabs, and SaaS platforms which increasingly act as proprietary guardians of your personal data, locking your context in cloud silos.
* **Heavy Administrative Note Maintenance:** Constant mental fatigue from manual vault housekeeping, sorting inboxes, moving files around, formatting notes, and maintaining link structures.
* **The Configuration Trap:** Wasting dozens of hours trying to configure an "effective system" inside your vault (tweaking Dataview scripts, CSS snippets, and complex folder structures) rather than executing real-world projects.

---

## 🛡️ The Solution: Arca-BrainOS

**Arca-BrainOS** is an open-source, AI-native operating system built for **Obsidian**. It equips your vault with a fleet of **autonomous agentic skills (`Skill_arca-*.md`)** that execute routine cognitive tasks, structure your knowledge, and co-pilot your Deep Work sessions.

> 📜 **Philosophy & Vision:** Want to understand the anthropological mutation, and motivation behind this architecture? Read **[The Sovereign AI Workflow Manifesto (MANIFESTO.md)](MANIFESTO.md)**.

```
       [ External Inputs: Videos, Books, Web, Transcripts ]
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │  1. Capture & Triage (0-Inbox/ & Youtube)    │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 2. Distillation & Theme Anchor (T- & Distil) │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 3. Exploration & Vault Health (RAG & Audit)  │
        └──────────────────────────────────────────────┘
                                │
                                ▼
        ┌──────────────────────────────────────────────┐
        │ 4. Deep Work & Execution (Projects & ROI)    │
        └──────────────────────────────────────────────┘
                                │
                                ▼
            [ High-Impact Outcomes & 3x Speed Gain ]
```

---

## ⚡ Proven Field ROI & Metrics

Arca-BrainOS is built on **empirical field data**, continuously tracked across real engineering, research, and writing projects.

> 💡 **Crucial Context:** These metrics were not measured on a clean, empty starter vault. They were achieved on a **real, pre-existing vault** containing hundreds of legacy notes. Once convinced of the system's power, AI co-pilots executed a progressive retrofit of legacy notes, YAML frontmatter, and Theme cards cleanly.

| Metric                           |       Measured Value        | Field Significance                            |
| :------------------------------- | :-------------------------: | :-------------------------------------------- |
| **Vault Baseline**               | **Pre-existing Real Vault** | Tested on real legacy notes, not a blank demo |
| **Completed Deep Work Sessions** |       **62 sessions**       | Real-world engineering & knowledge work       |
| **Real Time Invested with AI**   |          **80h40**          | Tracked session time with Arca-BrainOS        |
| **Estimated Time Without AI**    |         **~258h00**         | Harvard / MIT knowledge work baseline         |
| **Net Time Saved**               |       **🚀 +177h20**        | Direct cognitive effort liberated             |
| **Speed Multiplier**             |          **⚡ x3**          | **3x faster project execution**               |

---

## 🧩 The 3 Phases of AI Adoption

Most knowledge workers get stuck in Phase 1 or 2:

1. **Phase 1: Opportunistic Usage (Ad-hoc Prompting):** Asking one-off questions in isolated ChatGPT/Claude web interfaces. High friction, zero memory.
2. **Phase 2: Fragmented Usage (Custom Gems & Projects):** Creating silos inside proprietary AI platforms (ChatGPT Projects, Claude Projects). Context is locked in third-party clouds.
3. **Phase 3: Systemic Integration (Arca-BrainOS):** Your AI agents operate directly on your local Markdown vault with full, real-time context. **Zero lock-in, infinite memory.**

---

## 💎 Key Design Principles

1. **LLM & Model Agnostic:** Works seamlessly with Claude 3.5 Sonnet, Gemini 1.5 Pro, GPT-4o, or local LLMs.
2. **Open Markdown Standard:** 100% human-readable Markdown files. No proprietary databases or lock-in.
3. **Preserve Human Voice:** AI agents never delete or rewrite human-authored text; they enrich metadata and sylvan wikilinks.
4. **Self-Documenting AI Extension:** When creating a new skill or process, **simply ask your LLM agent to create it**. Your co-pilot will handle the skill logic and automatically perform all systemic updates (`AGENTS.md`, `skills/README.md`, `process/README.md`) while maintaining test suite compliance (`arca-test`).

---

## 🔌 The Agentic Skills Arsenal

All agentic capabilities are modular Markdown skills stored inside `_Arca-BrainOS/skills/` and executable via terminal AI runners (**Antigravity**, **Claude Code**, **OpenCode**, **Cursor**):

### 📥 1. Capture & Triage
* `arca-inbox-process`: Normalizes YAML frontmatter, cleans raw notes, and routes inputs.
* `arca-organize-idea`: Structures raw thoughts into actionable notes while preserving 100% of human text.
* `arca-youtube`: Extracts YouTube transcripts and creates structured inbox notes.

### 🧪 2. Distillation & Theme Anchoring (*The Killer Feature*)
* `arca-distill`: Master orchestrator for media ingestion (Synthesis $\rightarrow$ Anchoring $\rightarrow$ Archive $\rightarrow$ Impact).
* `arca-synthesize`: Drafts concept-dense summaries (`AI-Distil-...`) in `/2-Ressources/IA-generated/`.
* `arca-converge`: Anchors AI distillations into human-curated Theme cards (`T-`) via wikilinks.
* `arca-impact`: Scans active projects (`P-`) to propose concrete, actionable next steps.

### 🔍 3. Exploration & Vault Maintenance
* `arca-query`: Conversational RAG co-pilot that bridges distant ideas across notes.
* `arca-audit`: Health diagnostic checking PARA compliance, orphan notes, broken links, and ROI metrics.
* `arca-test-suite`: Automated agentic test harness running quality assertions for non-regression.

### 🪵 4. Deep Work & Execution
* `arca-resume`: Cognitively frames Deep Work sessions by scanning recent progress and defining focus.
* `arca-close-session`: Closes Deep Work sessions, updates project worklogs, and calculates real ROI metrics.
* `arca-create-note`: Fast direct instantiation via shortcuts (`create-project`, `create-theme`, `create-domaine`).

---

## 📂 Architecture & Vault Topography (2-Part Decoupled Design)

Arca-BrainOS leverages a **strictly decoupled 2-part architecture**:

1. **Part A: The OS Engine (`_Arca-BrainOS/`)**: A single, 100% portable core container containing skills, processes, templates, test suite, and `AGENTS.md`.
2. **Part B: Your 2nd Brain Content (Existing or New Vault)**: Your personal Obsidian notes, projects, and folders. **Arca-BrainOS is 100% folder-agnostic**: if you have a pre-existing vault structure, simply adapt the path variables in `AGENTS.md` (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`) to connect Arca-BrainOS to your custom folder hierarchy!

```text
Your-Obsidian-Vault/
├── _Arca-BrainOS/                # 🧠 PART A: The OS Core Container (100% Portable)
│   ├── AGENTS.md                 # Universal System Prompt & Path Variables (PATH_PROJECTS, etc.)
│   ├── log.md                    # Single-line append audit log
│   ├── skills/                   # 🔌 Modular Agentic Skills (Skill_arca-*.md)
│   ├── process/                  # 📚 Human/AI Methodological Guides (Process-*.md)
│   ├── templates/                # 📄 Standardized Templates (Project, Theme, Area)
│   └── tests/                    # 🧪 Automated Test Suite & Fixtures
│
├── Home.md                       # Optional Executive Cockpit (Included in starter-vault)
├── 0-Inbox/                      # 🧠 PART B: Your 2nd Brain Content (Configurable Paths)
├── 1-Projects/                   # Active Projects (P-...)
├── 2-Ressources/                 # Knowledge Base
│   ├── Notes/                    # Human notes & journal entries
│   ├── IA-generated/             # AI Write-Only Zone (AI-Distil-...)
│   └── Themes/                   # Curated Theme Cards (T-...)
├── 3-Domaines-de-vie/            # Life Areas (README.md canonical index)
└── 4-Archives/                   # Completed Projects & Inactive Areas
```

---

## ⚡ Quickstart (1-Minute Onboarding)

> 💡 **Step-by-Step Walkthrough:** Looking for an in-depth onboarding guide? Check out **[GETTING_STARTED.md](GETTING_STARTED.md)**.

### 1. Prerequisites
* **[Obsidian](https://obsidian.md)** (v1.5+)
* **Conceptual Mindset (Recommended):**
  * Basic familiarity with the **Second Brain (BASB)** philosophy and **P.A.R.A Method** (Projects, Areas, Resources, Archives) by Tiago Forte. Arca-BrainOS supercharges this methodology, so understanding active projects vs. long-term areas helps you get the most out of your AI co-pilot.
* **Required Obsidian Community Plugins:**
  * **[Dataview Plugin](https://github.com/blacksmithgu/obsidian-dataview):** Powering the `Home.md` executive cockpit and active areas focus widgets.
    * *Required Settings:* Toggle ON **"Enable JavaScript Queries"** (`dataviewjs`) and **"Enable Inline JavaScript Queries"** under `Dataview > Settings`.
* **AI Terminal CLI Runner:**
  * An AI CLI runner executed locally inside your Obsidian vault directory (e.g. **Google Antigravity**, **Claude Code**, **OpenCode**, or **Cursor**).

### 2. Installation (2 Options)

#### 📁 Option A: Add to an Existing Vault (Dossier `_Arca-BrainOS/`)
Copy the `_Arca-BrainOS/` engine directory into the root of your existing Obsidian vault. Open your AI CLI runner (Antigravity / Claude Code / OpenCode) inside your vault and prompt your co-pilot with the bootstrap instruction from [`INSTALL.md`](INSTALL.md):

```text
Read https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.md (or local INSTALL.md) and install Arca-BrainOS for me.
```

*Your Installer Agent will automatically scan your existing vault arborescence, detect custom folder paths, deploy `_Arca-BrainOS/`, configure path variables in `AGENTS.md`, and execute `arca-test` verification without overwriting your existing notes.*

#### 📦 Option B: Fresh Start / Ready-to-Use Vault (Dossier `starter-vault/`)
Copy or clone the pre-configured `starter-vault/` directory and open it directly as a new vault inside Obsidian. Everything is pre-configured out-of-the-box (`AGENTS.md` at root, `Home.md` cockpit, clean PARA folder structure).

> 💡 **Recommended Tip:** Rename the `starter-vault/` directory to a custom name that makes sense for you (e.g. `ArcaBrain`, `2ndBrain`, `MyVault`, `MyNotes`, etc.) before or after opening it in Obsidian!

### 3. Run Verification Test
Open your AI terminal inside your Obsidian vault and run:

```bash
arca-test
```
*Your agent will run automated quality assertions to verify full vault health and path configuration.*

---

## 🎬 Your First 2-Minute Workflow (Concrete Example)

Here is how Arca-BrainOS turns raw information into active project execution in 4 automated steps:

### 1. Capture (Drop an input into `0-Inbox/`)
Drop a YouTube video URL or paste an article transcript into `0-Inbox/video-transcript.md`.

### 2. Distill (Run 1 Agent Command)
Open your AI terminal and type:
```bash
arca-distill 0-Inbox/video-transcript.md
```

### 3. Watch the Magic Happen (30 Seconds)
Your AI co-pilot executes 4 sequential actions automatically:
1. 🧪 **Drafts Synthesis:** Creates a concept-dense summary `AI-Distil-Video-Transcript` inside `/2-Ressources/IA-generated/`.
2. 📜 **Anchors to Themes:** Connects wikilinks into relevant Theme cards (e.g., `[[T-Intelligence-Artificielle]]`).
3. 📦 **Archives Inbox File:** Moves the raw file out of `0-Inbox/` into archives to maintain Inbox Zero.
4. 🚀 **Proposes Project Tasks:** Scans your active projects (`P-`) and asks in the chat: *"Would you like me to add these 2 actionable tasks to project `P-MyProject`?"*

### 4. Result
Zero manual formatting, zero context switching, and immediate project momentum!

---

## ❓ FAQ & Risk Management

### How is Arca-BrainOS different from using raw Obsidian or isolated AI chats?
Raw Obsidian gives you local Markdown files, but requires manual organization. Isolated AI web chats (ChatGPT, Claude) lack real-time context of your past notes. Arca-BrainOS bridges the two: your AI agents operate directly on your local vault files with full context, automating routine tasks while keeping 100% of your data local and human-readable.

### What if an AI agent makes a mistake or I want to roll back changes?
Arca-BrainOS is engineered for **zero data loss, transparency, and instant recovery**:
* **In-Session Agentic Rollback:** In the worst-case scenario where an agent misinterprets an instruction during a session, simply tell your AI co-pilot in the chat: *"Rollback the last edit on file X"* or *"Restore the previous version of file Y"*. Your agent will inspect its transcript and revert the file immediately.
* **Strict 3-File Guardrail:** Agents are prohibited from creating or modifying more than 3 files outside `/2-Ressources/IA-generated/` in a single workflow without explicit confirmation in the chat.
* **Single-Line Audit Log:** Every action executed by an agent is appended to `_Arca-BrainOS/log.md` (1 line per action with timestamp).
* **Git Version Control & Backups:** We strongly recommend initializing Git on your vault (`git init`). Rollbacks can be executed instantly via `git checkout` or your local Obsidian sync/backup system.
* **Interactive AI Help:** You can ask your AI co-pilot at any time: *"What files were modified in the last session?"* or run `arca-audit` to diagnose vault health.

### Will AI agents overwrite or modify my human-written notes?
**No.** Arca-BrainOS operates under strict safety guardrails defined in `AGENTS.md`:
* **AI Write-Only Zone:** Autonomous AI writing is isolated inside `/2-Ressources/IA-generated/` (for `AI-Distil-...` notes).
* **Supervised Zone:** For human notes (`1-Projects/`, `2-Ressources/Notes/`, `3-Domaines-de-vie/`), agents never overwrite human text. They only suggest sylvan wikilinks `[[...]]` or append worklog entries during `arca-close-session`.

### Can I use Arca-BrainOS with my existing folder structure?
**Yes.** Arca-BrainOS is 100% folder-agnostic. The core engine lives inside `_Arca-BrainOS/`. All folder references are configured via path variables in `AGENTS.md` (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`). You can map these variables to any custom arborescence.

### Which AI runners are supported?
Arca-BrainOS is **LLM- and runner-agnostic**. It works seamlessly with **Google Antigravity**, **Claude Code**, **OpenCode**, **Cursor**, or any AI agent that can read Markdown files and execute terminal commands.

---

## 🙏 Acknowledgments & Inspiration

Arca-BrainOS stands on the shoulders of giants across Personal Productivity, Knowledge Management (PKM), and AI Agentic Engineering:

* **[David Allen](https://gettingthingsdone.com)**: The grandfather of modern productivity and author of **Getting Things Done (GTD)**, who taught us to clear cognitive load by capturing everything into trusted external systems.
* **[Sönke Ahrens](https://takesmartnotes.com)**: Author of ***How to Take Smart Notes***, who demystified Niklas Luhmann's Zettelkasten method and turned atomic note-taking into a lifelong compounding asset.
* **[Tiago Forte](https://fortelabs.com)**: For pioneering the **Building a Second Brain (BASB)** methodology, the C.O.D.E framework, and the P.A.R.A organizational system that provided the structural baseline for modern PKM.
* **[Ryder Carroll](https://bulletjournal.com)**: Creator of **The Bullet Journal Method**, inspiring rapid logging, daily intentionality, and mindful review routines.
* **[Daniel Miessler](https://danielmiessler.com)**: For the **Personal AI Infrastructure (PAI)** framework, **LifeOS**, and flat container modularity principles (`_Arca-BrainOS/`).
* **[Eliott Meunier](https://www.youtube.com/@eliottmeunier)**: French PKM pioneer and educator who popularized Obsidian, digital organization, and modern knowledge management for the French-speaking community.
* **[Jeff Su](https://www.youtube.com/@JeffSu)**: For insightful productivity tutorials, actionable workflow optimization, and practical digital organization strategies.
* **[Obsidian.md](https://obsidian.md)**: For creating the gold-standard, open-format, local-first Markdown canvas for human thought.
* **[Blacksmithgu & Dataview Community](https://github.com/blacksmithgu/obsidian-dataview)**: For the Dataview plugin that makes real-time vault telemetry and JS-powered executive cockpits possible.
* **Google Antigravity & Claude Code Teams**: For pioneering terminal-first, agentic co-pilot execution directly on local codebases and knowledge vaults.

---

## 📜 License & Strategic Protection

Arca-BrainOS is released under a **Dual / Hybrid License** model (see [`LICENSE`](LICENSE) for complete legal terms):

* **Code, Skills & Scripts (`_Arca-BrainOS/skills/`, `tests/`, `scripts/`):** Licensed under **GNU Affero General Public License v3.0 (GNU AGPLv3)**. Free for personal and open-source community use; requires derivative cloud services or software modifications to be open-sourced under AGPLv3.
* **Playbooks, Methodologies & Manifestos (`playbooks/`, `process/`, `MANIFESTO.md`):** Licensed under **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)**. Free for individual learning; commercial reuse, corporate reselling, or paid consulting usage by third-party companies is prohibited without explicit commercial agreement.

> 💡 **Why This Dual License Choice?**  
> We believe in 100% open, sovereign access for individual thinkers, researchers, and community builders. However, we explicitly choose **NOT** to use a permissive MIT license to prevent large corporations or commercial vendors from silently capturing this open-source work, closing it into proprietary SaaS products, or reselling our methodologies for corporate profit without contributing back.

---

<p align="center">
  <i>Built with ❤️ for thinkers, builders, and lifelong learners.</i>
</p>
