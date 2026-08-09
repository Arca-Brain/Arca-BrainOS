---
date: 2026-08-09
title: GETTING_STARTED.md — Detailed Onboarding & Operational Guide for Arca-BrainOS
description: Operational walkthrough for setting up DataviewJS, configuring path variables in AGENTS.md, running Deep Work session management (arca-resume & arca-close-session), and using Playbooks.
tags:
  - getting-started
  - onboarding
  - guide
  - obsidian
  - arca-brainos
status: "#completed"
---

# 🚀 GETTING STARTED: Detailed Onboarding & Operational Guide

Welcome to **Arca-BrainOS**! This guide complements the high-level **[README.md](README.md)** Quickstart by providing detailed operational instructions for configuring your environment, running Deep Work sessions, and leveraging Playbooks.

---

## ⚙️ 1. Detailed Environment & Plugin Configuration

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
PATH_AREAS: "3-Domaines-de-vie/"
PATH_THEMES: "2-Ressources/Themes/"
PATH_IA_GENERATED: "2-Ressources/IA-generated/"
PATH_SYSTEM: "_Arca-BrainOS/"
```

---

## 🪄 2. Installation Protocol

* **Assisted Installation (Recommended — 1 Min):** Prompt your AI terminal runner with the instruction from [`INSTALL.md`](INSTALL.md):
  ```text
  Read INSTALL.md and install Arca-BrainOS for me.
  ```
* **Manual Setup:** Copy `_Arca-BrainOS/` into your vault root.

---

## 🧪 3. Vault Verification (`arca-test`)

Run the automated test suite in your AI terminal to verify path resolution and frontmatter compliance:

```bash
arca-test
```

---

## 🪵 4. Deep Work Session Management (`arca-resume` & `arca-close-session`)

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

## 📘 5. Leveraging Operational Playbooks

When you need to perform high-impact structural transformations, refer to the step-by-step guides in `_Arca-BrainOS/playbooks/`:

* **[[Playbook-Retrofit-et-Migration-de-Coffre-Existant]]** — Protocol for auditing, segmenting, and retrofitting legacy vaults (600+ notes) cleanly without losing human writing style.
* **[[Playbook-Cartographie-et-Processus-de-Vie]]** — Methodology for auditing recurring life tasks and defining human vs. AI automation boundaries.

---

## 🔗 Useful Links & References
* 📜 **[The Sovereign AI Workflow Manifesto](MANIFESTO.md)**
* 🪄 **[Installer Prompt (INSTALL.md)](INSTALL.md)**
* 🤝 **[Contribution Guidelines (CONTRIBUTING.md)](CONTRIBUTING.md)**
* ⚖️ **[Dual License Agreement (LICENSE.md)](LICENSE.md)**
