---
date: 2026-08-08
title: "Arca-BrainOS: Official GitHub Release"
description: "Official English README for Arca-BrainOS open-source GitHub release."
tags:
  - readme
  - github
  - open-source
  - arca-brainos
status: "#completed"
---

# 🧠 Arca-BrainOS

<p align="center">
  <img src="assets/arcabrain_banner.jpg" alt="Arca-BrainOS Panoramic Banner" width="100%">
</p>

> *"My ark is not a refuge, it is an engine... Dreams conceive, but only action accomplishes."*  
> **Fernando Pessoa**  
>  
> *(Inspired by Fernando Pessoa's famous wooden trunk, "A Arca", containing thousands of fragments, manuscripts, and heteronyms waiting to become a universe. Arca-BrainOS is that execution engine for your digital mind.)*

---

**Sovereign agentic workflow & local co-pilot for Obsidian**

🇫🇷 **[Lire la version française (README.fr.md)](README.fr.md)**

[![Obsidian](https://img.shields.io/badge/Obsidian-Vault%20Ready-7C3AED?style=flat-square&logo=obsidian&logoColor=white)](https://obsidian.md)
[![License: Dual AGPLv3 / CC BY-NC-SA 4.0](https://img.shields.io/badge/License-Dual%20AGPLv3%20%2F%20CC%20BY--NC--SA%204.0-blue?style=flat-square)](LICENSE)
[![LLM Agnostic](https://img.shields.io/badge/LLM-Agnostic%20%26%20Portable-emerald?style=flat-square)](#-key-design-principles)
[![ROI Speed](https://img.shields.io/badge/ROI-Speed%20x3-orange?style=flat-square)](#-proven-field-roi--metrics)
[![Built with Google Antigravity](https://img.shields.io/badge/Built_with-Google%20Antigravity-4285F4?style=flat-square&logo=google&logoColor=white)](https://github.com/Arca-Brain/Arca-BrainOS)

**[Quickstart](#-quickstart-1-minute-onboarding)** · **[Getting Started](GETTING_STARTED.md)** · **[Manifesto](MANIFESTO.md)** · **[Agentic Skills](#-the-agentic-skills-arsenal)** · **[Architecture](#-architecture--vault-topography-2-part-decoupled-design)** · **[Contributing](CONTRIBUTING.md)** · **[FAQ](#-faq)**


---

> 🎯 **Core Concept:** Move from scattered thoughts and fragmented AI tools to a sovereign, AI-native operating system executing your cognitive workflows directly inside your local Obsidian vault.


### ⭐ If you find Arca-BrainOS helpful, star the repository on GitHub!

Stars help other thinkers and builders discover the project and move it forward.

[![Star Arca-BrainOS on GitHub](https://img.shields.io/badge/Star%20Arca--BrainOS%20on%20GitHub-⭐-8B5CF6?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Arca-Brain/Arca-BrainOS)


---

## 💥 The Problem: Why Most Second Brains Die Out

Building a Second Brain (PKM) often turns into a maintenance nightmare:

* **Fragmented ecosystems & proprietary SaaS:** Your thoughts, documents, and workflows are scattered across multiple repositories, web tabs, and SaaS platforms that increasingly become proprietary gatekeepers of your personal data, locking your context into cloud silos.
* **Heavy administrative maintenance overhead:** Constant mental fatigue spent on manual vault housekeeping: sorting the inbox, moving files around, formatting notes, and maintaining links.
* **The configuration trap:** Spending dozens of hours trying to configure a perfect system in your vault (tweaking Dataview scripts, CSS snippets, and complex folder structures) instead of executing actual projects and getting real outcomes.

---

## 🛡️ The Solution: Arca-BrainOS

**Arca-BrainOS** is an open-source, AI-native operating system designed for **Obsidian** (and fully compatible with any plain-text Markdown note editor). It equips your vault with a fleet of **autonomous agentic skills (`Skill_arca-*.md`)** that execute routine cognitive tasks, structure your knowledge, and co-pilot your Deep Work sessions.

The system is designed to seamlessly articulate two complementary dimensions of your projects:
- **Intellectual & digital projects:** Software engineering, systems architecture, research, writing, and business strategy.
- **Real-world planning & life projects:** Preparing home renovation work, organizing a trek or travel expedition, tracking health and rehabilitation routines, or mastering a craft (watercolor, poetry...).

By dynamically linking every active project to your **Life Areas (`3-Domaines-de-vie/`)**, Arca-BrainOS delivers a truly holistic overview of your life: it powers seasonal and annual reviews, balances your energy across domains, and turns accumulated knowledge into real-world action.

> 📜 **Philosophy & Vision:** Want to understand the anthropological mutation and motivation behind this architecture? Read **[The Sovereign AI Workflow Manifesto (MANIFESTO.md)](MANIFESTO.md)**.

```text
     [ Raw Inputs: YouTube Videos, Articles, Transcripts, Notes ]
                                │
                                ▼
 ┌─────────────────────────────────────────────────────────────┐
 │ 1. Ingestion & Distillation (Capture & AI Syntheses)        │ 🤖 100% Automated
 └─────────────────────────────────────────────────────────────┘
                                │
                                ▼
 ┌─────────────────────────────────────────────────────────────┐
 │ 2. Organization & Weaving (Themes T-, Areas & Links)        │ 🤝 AI-Assisted
 └─────────────────────────────────────────────────────────────┘
                                │
                                ▼
 ┌─────────────────────────────────────────────────────────────┐
 │ 3. Deep Work & Execution (Projects P- & Production)         │ 🧠 Human Focus
 └─────────────────────────────────────────────────────────────┘
                                │
                                ▼
 ┌─────────────────────────────────────────────────────────────┐
 │ 4. Audit & Maintenance (Vault Health & RAG Search)          │ ⚙️ AI Supervision
 └─────────────────────────────────────────────────────────────┘
                                │
                                ▼
          [ Sustainable Long-Term System & 3x Speed Gain ⚡ ]
```

#### 🎯 Why This System Never Rots (The Arca-BrainOS Difference):

- **📥 1. Ingestion & Distillation (Automated):** Raw inputs (videos, articles, podcasts) are automatically captured and distilled into dense, actionable inbox notes.
- **🗂️ 2. Organization & Weaving (Assisted):** AI handles tedious vault housekeeping. It weaves wikilinks (`[[...]]`), populates Theme cards (`T-`), and updates Life Areas. **Zero organizational fatigue**: your vault stays clean, structured, and sustainable over the long term without manual overhead.
- **🚀 3. Deep Work & Execution (Human Focus):** Tedious project management is delegated. You focus 100% on high-value creation and decision-making for active projects (`P-`). During Deep Work sessions, you freely choose your level of AI assistance (co-writing, structuring, or 100% human authorship).
- **🩺 4. Audit & Maintenance (Supervised):** AI monitors vault health (broken links, orphaned notes, semantic RAG search via `arca-query`), subject only to your approval of structural choices.

---

## ⚡ Proven Field ROI & Metrics

Arca-BrainOS is grounded in **real empirical data**, continuously tracked across actual engineering, research, and writing projects.

> 💡 **Crucial Context:** These metrics were NOT measured on a clean, empty demo vault. They were obtained on an **actual pre-existing vault** containing hundreds of legacy notes. Once convinced of the system's power, the AI co-pilots execute a progressive, clean retrofit of historical notes, YAML, and Theme MOCs.

| Metric                           |       Measured Value        | Field Significance                                 |
| :------------------------------- | :-------------------------: | :------------------------------------------------- |
| **Vault Baseline**               |  **Actual Pre-existing Vault** | Tested on real historical notes, not a sandbox    |
| **Completed Deep Work Sessions** |       **62 sessions**       | Real engineering & intellectual production        |
| **Real Time Invested with AI**   |          **80h40**          | Actual session time tracked with Arca-BrainOS      |
| **Estimated Time Without AI**     |         **~258h00**         | Knowledge work benchmark (MIT/Harvard estimates)   |
| **Net Time Saved**               |       **🚀 +177h20**        | Direct cognitive effort saved                      |
| **Speed Multiplier**             |          **⚡ x3**          | **3x faster project execution**                    |

---

## 🧩 The 3 Phases of AI Adoption

Most knowledge workers remain trapped in Phase 1 or 2:

1. **Phase 1: Opportunistic Usage (Ad-hoc Prompting):** Asking isolated questions in ChatGPT/Claude web interfaces. High friction, zero memory.
2. **Phase 2: Fragmented Usage (Gems & Projects):** Creating silos in proprietary platforms (ChatGPT Projects, Claude Projects). Context is locked into third-party clouds.
3. **Phase 3: Systemic Integration (Arca-BrainOS):** Your AI agents operate directly on your local Markdown vault with full real-time context. **Zero lock-in, infinite memory.**

---

## 💎 Key Design Principles

1. **🔒 Sovereign & Offline-First:** Your knowledge lives in local plain-text Markdown (`.md`). You own your data forever.
2. **🤖 LLM-Agnostic & Portable:** Works with Google Antigravity, Claude Code, OpenCode, ChatGPT, or local LLMs.
3. **🤝 Organological Symbiosis:** AI handles administrative friction; humans retain intentional friction and creative vision.
4. **📦 Decoupled Architecture:** Core engine (`_Arca-BrainOS/`) is isolated from user content (`0-Inbox/`, `1-Projects/`, etc.).

### 🎨 Template Adaptability & Custom Skills Extension

Arca-BrainOS is not a rigid framework: you are completely free to adapt note templates (`Template-Projet.md`, `Template-Area.md`, `Template-Theme.md`) or create custom agentic skills (`Skill_arca-*.md`) to match your actual workflows.

* **Preserving YAML Compatibility:** Simply make sure to preserve the minimal required frontmatter keys used by Dataview queries and system scripts (`target`, `tags`, `areas`, `themes`, `date_created`).
* **💡 Golden Recommendation (Leverage Your AI Agent):** Avoid editing templates and skills manually. Instead, ask your AI coding assistant (Antigravity, Claude Code, OpenCode):
  > *"Update my Project template to add section X, while preserving compatibility with YAML metadata and existing agentic skills."*
  
  Your AI assistant will format the structure cleanly, update parent index files (`skills/README.md`, `AGENTS.md`), and verify compliance with `arca-test`.

---

## ⚡ Quickstart (1-Minute Onboarding)

> 💡 **Detailed Operational Guide:** Looking for a step-by-step onboarding walkthrough? Read **[GETTING_STARTED.md](GETTING_STARTED.md)**.

### 1. Prerequisites
* **[Obsidian](https://obsidian.md)** (v1.5+)
* **Dataview Plugin** (Enabled with JS queries turned ON in Obsidian settings)
* **[Obsidian Web Clipper](https://obsidian.md/clipper)** (Official browser extension to capture articles and web pages into `0-Inbox/`)
* An AI coding assistant (Google Antigravity CLI, Claude Code, OpenCode, Cursor, etc.)

### 2. Which AI Runner Should You Choose to Get Started?

Arca-BrainOS runs seamlessly with any agentic CLI or coding assistant. Here is a quick comparison to guide your choice:

| AI Runner | Key Strengths | Recommended For | Recommended Models |
| :--- | :--- | :--- | :--- |
| **Google Antigravity** | **Free to start**, generous rate limits, huge context window (1M+ tokens), native agentic workflow | Immediate frictionless start with zero setup cost | Gemini 1.5 Pro / Flash |
| **Claude Code** | Premier reasoning capabilities, high fidelity Markdown note editing, concise synthesis | Users with an active Anthropic API account | Claude 3.5 Sonnet |
| **OpenCode** | 100% open-source terminal CLI, supports local inference servers | Total data sovereignty and offline setups | Local models (Ollama) or API |
| **Cursor / Windsurf** | Full IDE experience pairing chat, terminal, and live file tree navigation | Users who prefer a graphic UI over a standalone CLI | Claude 3.5 Sonnet, GPT-4o |

---

### 3. Installation (Choose Option A or Option B)

- **📁 Option A: Add to an Existing Vault (Directory `starter-kit/en/_Arca-BrainOS/`)**  
  Copy `starter-kit/en/_Arca-BrainOS/` into your existing Obsidian vault root. Then tell your AI assistant:
  ```text
  Read https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.md (or local INSTALL.md) and install Arca-BrainOS for me.
  ```

- **📦 Option B: Fresh Start (Starter Vault: Directory `starter-kit/en/starter-vault/`)**  
  Download or copy the `starter-kit/en/starter-vault/` folder and open it directly as a new vault in Obsidian. Everything is pre-configured out-of-the-box (`AGENTS.md` at root, `Home.md` cockpit, clean PARA structure).
  
  > 💡 **Recommended First Step:** Upon opening the vault in Obsidian, open the welcome note **`00-START-HERE.md`** at the root. It walks you through your first 3 practical hands-on experiments in under 5 minutes!
  > 
  > *(Tip: Feel free to rename the `starter-vault/` folder to your preferred vault name like `ArcaBrain`, `2ndBrain`, or `MyNotes`)*.

### 4. Verification Test
In your AI terminal runner, run:
```bash
arca-test
```
*Your agent will execute automated assertions to verify vault health and path resolution.*

---

## 🔌 The Agentic Skills Arsenal

All agentic capabilities are modular Markdown skills stored in `_Arca-BrainOS/skills/` and executable via your AI coding assistants (**Antigravity**, **Claude Code**, **OpenCode**, **Cursor**):

### 📥 1. Capture & Triage
* `arca-inbox-process`: Cleans YAML frontmatter, formats raw notes, and dispatches incoming files.
* `arca-organize-idea`: Formats raw ideas into actionable notes without losing original human text.
* `arca-youtube`: Extracts transcripts and metadata from YouTube videos to create structured inbox notes.

### 🧪 2. Distillation & Theme Anchoring (*The Killer Feature*)
* `arca-distill`: Master media ingestion skill (Synthesize $\rightarrow$ Anchor $\rightarrow$ Archive $\rightarrow$ Impact Analysis).
* `arca-synthesize`: Writes conceptual syntheses (`AI-Distil-...`) into `/2-Ressources/IA-generated/`.
* `arca-converge`: Anchors distillations into Theme MOC cards (`T-`) via wikilinks.
* `arca-impact`: Scans active projects (`P-`) to propose concrete tasks stemming from new knowledge.

### 🔍 3. Exploration & Vault Maintenance
* `arca-query`: Conversational RAG co-pilot creating cognitive bridges across distant ideas.
* `arca-audit`: Vault health diagnostic, orphan note detection, broken link repair, and ROI tracking.
* `arca-test-suite`: Automated test harness executing non-regression assertions.

### 🪵 4. Deep Work & Execution
* `arca-resume`: Cognitive framing for work sessions (progress summary and intent setting).
* `arca-close-session`: Closes Deep Work sessions, updates project worklog, and calculates AI ROI.
* `arca-create-note`: Fast instantiation via direct shortcuts (`create-project`, `create-theme`, `create-domaine`).

---

## 🏗️ Architecture & Vault Topography

Arca-BrainOS uses a 2-part decoupled architecture:

```text
Your-Obsidian-Vault/
├── AGENTS.md                     # Universal system prompt & vault topography config
├── Home.md                       # Optional Executive Cockpit (Included in starter-vault)
├── _Arca-BrainOS/                # 🧠 Core Agentic Engine (100% Portable & Self-Contained)
│   ├── log.md                    # Single-line audit log
│   ├── skills/                   # Agentic skills (Skill_arca-*.md)
│   ├── process/                  # Methodological process guides (Process-*.md)
│   ├── templates/                # Standardized note templates
│   └── tests/                    # Test harness fixtures & assertions
├── 0-Inbox/                      # Ingestion & raw captures
├── 1-Projects/                   # Active projects (P-*.md) & Incubation (_Incubation/)
├── 2-Ressources/                 # Knowledge base (Notes/, IA-generated/, Themes/)
├── 3-Domaines-de-vie/            # Permanent life areas (README.md index)
└── 4-Archives/                   # Completed projects & dormant areas
```

### 🌐 Deployment Principles & Possibilities: A System That Grows With You

Arca-BrainOS imposes no rigid boundaries: it adapts naturally to your lifestyle and priorities. Three flexible possibilities are available to support how you think and work:

1. **Immediate Simplicity (The Desktop Workspace)**  
   *Who is it for?* To get started right away with zero setup friction.  
   *The principle:* You run the system directly on your computer with your preferred AI models. In under a minute, you have an intelligent assistant inside your notes to organize ideas, frame projects, and power your Deep Work sessions.

2. **Mobile Freedom (Capturing Thought on the Move)**  
   *Who is it for?* For thinkers who get their best insights while walking, travelling, or away from their desk.  
   *The principle:* Unshackle thought capture from your computer screen. Dictate a voice note or share a link from your smartphone (via a messaging app like Telegram): AI receives your thoughts, formats them, and places them in the right spot in your vault so everything is waiting for you when you return to your desk.

3. **Total Sovereignty & Privacy (Your 100% Private Mindspace)**  
   *Who is it for?* For those who require absolute ownership over their sensitive thoughts and intellectual property.  
   *The principle:* You decide your level of cognitive sovereignty. The system can operate either through privacy-first providers guaranteeing Zero Data Retention (ZDR), or run 100% offline on your own hardware without ever sending data to external clouds.

---

## 🤝 Contributing

Contributions are welcome! Read **[CONTRIBUTING.md](CONTRIBUTING.md)** to learn how to add skills, process guides, or test assertions.

---

## 📜 License

Arca-BrainOS uses a Dual Open-Source License:
- **Code, Skills & Scripts:** [GNU AGPLv3](LICENSE)
- **Playbooks, Process Guides & Documentation:** [Creative Commons CC BY-NC-SA 4.0](LICENSE)

---

<p align="center">
  <i>Built with passion by Hugues & the Arca-BrainOS Community.</i>
</p>
