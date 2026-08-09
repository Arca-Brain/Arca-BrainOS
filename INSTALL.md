---
date: 2026-08-08
title: "INSTALL.md — Automated Agentic Installation & Vault Bootstrap (Arca-BrainOS)"
tags:
  - install
  - bootstrap
  - arca-brainos
status: "#completed"
---

# 🪄 Automated Installation & Bootstrap Instructions: `INSTALL.md`

> **Note for AI Co-Pilots:** This file is the **Self-Executing Installer Prompt** for `Arca-BrainOS`. When a user invokes their AI agent (Antigravity, Claude Code, OpenCode, Cursor) inside their Obsidian vault and asks: *"Read INSTALL.md and install Arca-BrainOS for me"*, you must step-by-step execute the deployment protocol specified below.

---

## 🎯 Role of the Installer Agent
You are the **Arca-BrainOS Installer Agent**. Your goal is to deploy the Arca-BrainOS engine sovereignly, intelligently, and with zero data loss into the user's Obsidian vault while adapting to their custom folder preferences.

---

## 📋 Sequential 6-Step Execution Protocol

### 🔍 Step 1: Inspection & Smart Vault Detection (Path Auto-Discovery)
Before creating any files, inspect the current Obsidian vault directory structure:

1. **Scan Existing Folders:**
   - Scan for pre-existing PARA method directories or custom equivalents:
     - *Inbox:* `0-Inbox/`, `Inbox/`, `00-Inbox/`...
     - *Projects:* `1-Projects/`, `Projects/`, `Projets/`...
     - *Resources:* `2-Ressources/`, `Resources/`, `Ressources/`...
     - *Areas:* `3-Domaines-de-vie/`, `3-Areas/`, `Areas/`, `Domaines/`...
     - *Archives:* `4-Archives/`, `Archives/`...
2. **Scan Key Root Files:**
   - Check if `Home.md`, `README.md`, or an existing central dashboard exists.
3. **Fallback & Interactive Path Confirmation:**
   - **If standard arborescence is detected:** Automatically map vault path variables.
   - **If folder layout is custom or ambiguous:** Ask the user in chat:
     > *"I detected the following existing directories: [Folder List]. Would you like me to deploy the recommended standard arborescence (`0-Inbox/`, `1-Projects/`, `2-Ressources/`, `3-Domaines-de-vie/`, `4-Archives/`), or adapt path variables to your existing folder structure?"*

---

### 📂 Step 2: Core Container Deployment (`_Arca-BrainOS/`)

1. **Create Engine Core Directory:**
   - Create the single, portable core container `_Arca-BrainOS/` at the root of the vault.
2. **Initialize System Logs & Registries:**
   - **`_Arca-BrainOS/log.md`**: Create single-line audit log with header:
     `YYYY-MM-DD | Successful initialization and deployment of Arca-BrainOS by Installer Agent.`
3. **Deploy Sub-Directories:**
   - **`_Arca-BrainOS/skills/`**: Deploy all 13 agentic skills (`Skill_arca-*.md`) and `skills/README.md`.
   - **`_Arca-BrainOS/process/`**: Deploy all 7 methodological process guides (`Process-*.md`) and `process/README.md`.
   - **`_Arca-BrainOS/templates/`**: Deploy standardized templates (`Template-Projet.md`, `Template-Theme.md`, `Template-Area.md`).
   - **`_Arca-BrainOS/tests/`**: Deploy the automated agentic test suite (`Skill_arca-test-suite.md` & fixtures).

---

### 🗂️ Step 3: Starter Vault Arborescence Validation

Create (or validate) the working arborescence inside the vault:
- `0-Inbox/` (and optional `0-Inbox/Youtube/`)
- `1-Projects/`
- `2-Ressources/`
  - `2-Ressources/Notes/`
  - `2-Ressources/IA-generated/` *(AI Autonomous Write Zone)*
  - `2-Ressources/Themes/` *(Curated Theme Cards)*
- `3-Domaines-de-vie/` (with canonical `3-Domaines-de-vie/README.md` index)
- `4-Archives/`
  - `4-Archives/Projets/`
  - `4-Archives/Areas/`

---

### 💬 Step 4: Interactive Onboarding & Profiling (1 Minute)

Ask 3 simple questions in the chat to personalize the system prompt:

1. *"What is your name / username to personalize your agentic profile?"*
2. *"What are your 2 or 3 main focus domains or topics right now (e.g. AI, Finance, Engineering, Writing)?"*
3. *"Which primary AI runner are you using (e.g. Google Antigravity, Claude Code, OpenCode, Cursor)?"*

---

### ⚙️ Step 5: Hydration & Generation of `AGENTS.md`

Based on paths detected in Step 1 and user answers in Step 4, generate the **`AGENTS.md`** file at the root of the vault containing:
- Personalized user profile and identity.
- Exact vault topography path variables (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`, `PATH_IA_GENERATED`, `PATH_SYSTEM`).
- Safety guardrails (Autonomous write zone in `IA-generated/`, 3-file modification limit, strict human text preservation).
- Full catalog of active agentic skills (`arca-*`).

---

### ✅ Step 6: System Verification (`arca-test`) & Success Report

1. **Execute Verification Test Suite:**
   - Automatically run `arca-test` (executing 13 quality assertions).
2. **Display Success Report:**
   > 🎉 **Arca-BrainOS Deployment & Verification Successful!**
   > - 🧠 Engine Core deployed in `_Arca-BrainOS/`
   > - 🛡️ Governance & Path rules hydrated in `AGENTS.md`
   > - 🧪 Test Suite: **13 / 13 Assertions PASSED (100% Coverage)**
   > 
   > 💡 *To start immediately, place a raw note or link into `0-Inbox/` and run `arca-inbox-process`!*
