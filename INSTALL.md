---
date: 2026-08-08
title: "INSTALL.md : Automated Agentic Installation & Vault Bootstrap (Arca-BrainOS)"
tags:
  - install
  - bootstrap
  - arca-brainos
status: "#completed"
---

# 🪄 Automated Installation & Bootstrap Instructions: `INSTALL.md`

> **Note for AI Co-Pilots:** This file is the **Self-Executing Installer Prompt** for `Arca-BrainOS`. When a user invokes their AI agent (Antigravity, Claude Code, OpenCode, Cursor) inside their Obsidian vault and asks: *"Read https://github.com/Arca-Brain/Arca-BrainOS/blob/main/INSTALL.md (or local INSTALL.md) and install Arca-BrainOS for me"*, you must step-by-step execute the deployment protocol specified below.

---

## 🎯 Role of the Installer Agent
You are the **Arca-BrainOS Installer Agent**. Your goal is to deploy the Arca-BrainOS engine sovereignly, intelligently, and with zero data loss into the user's Obsidian vault while adapting to their custom folder preferences.

---

## 🚀 Choose Your Installation Mode

Before starting, choose the option that matches your setup:

* **📁 Option A: Add to an EXISTING Obsidian Vault (Dossier `_Arca-BrainOS/`)**  
  Copy only the `_Arca-BrainOS/` directory into the root of your existing Obsidian vault. Run `INSTALL.md` with your AI agent. Your 500+ existing notes and folder structure are 100% preserved; path variables will automatically adapt to your custom layout without overwriting your existing `AGENTS.md`.
* **📦 Option B: Fresh Start with Ready-to-Use Vault (Dossier `starter-vault/`)**  
  Download/copy the `starter-vault/` directory and open it directly as a new vault inside Obsidian. Everything is pre-configured out-of-the-box (`AGENTS.md` at root, `Home.md` cockpit, and clean PARA folder structure).
  > 💡 **Recommended Tip:** Rename the `starter-vault/` folder to a custom name that makes sense for you (e.g. `ArcaBrain`, `2ndBrain`, `MyVault`, `MyNotes`, etc.) before or after opening it in Obsidian!

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
2. **Initialize System Logs & Core Constitution:**
   - **`_Arca-BrainOS/AGENTS.md`**: Deploy the master system constitution, governance rules, and skills catalog.
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

### ⚙️ Step 5: Engine Hydration & AI Runner Bridge (Universal Bridge)

1. **Hydration of Core Constitution (`_Arca-BrainOS/AGENTS.md`):**
   Based on paths discovered in Step 1 and answers from Step 4, directly hydrate `_Arca-BrainOS/AGENTS.md` (the Single Source of Truth) with:
   - Personalized user identity and profile.
   - Exact vault topography path variables (`PATH_INBOX`, `PATH_PROJECTS`, `PATH_THEMES`, `PATH_AREAS`, `PATH_IA_GENERATED`, `PATH_SYSTEM`).
   - Governance rules and full catalog of active agentic skills (`arca-*`).

2. **Non-Destructive AI Runner Bridging (Bridge Files):**
   Depending on the AI runner used (detected in Step 4):
   - **For Google Antigravity / Gemini CLI / OpenCode:**
     - If a root `AGENTS.md` already exists, simply append the include directive at the end without overwriting user content:
       ```markdown
       # 🧠 Arca-BrainOS Cognitive Engine
       For Second Brain notes, workflows, and agentic skills, follow the instructions in:
       @_Arca-BrainOS/AGENTS.md
       ```
     - If no root file exists, create a minimal root `AGENTS.md` pointing to `@_Arca-BrainOS/AGENTS.md`.
   - **For Claude Code:**
     - If a root `CLAUDE.md` already exists, append `@_Arca-BrainOS/AGENTS.md` at the end.
     - If no file exists, create a minimal root `CLAUDE.md` pointing to `@_Arca-BrainOS/AGENTS.md`.
   - **For Cursor / Windsurf:**
     - Create or complete `.cursorrules` at root to load `_Arca-BrainOS/AGENTS.md`.

---

### ✅ Step 6: System Verification (`arca-test`) & Success Report

1. **Execute Verification Test Suite:**
   - Automatically run `arca-test` (executing 13 quality assertions).
2. **Display Success Report:**
   > 🎉 **Arca-BrainOS Deployment & Verification Successful!**
   > - 🧠 Engine Core & Constitution deployed in `_Arca-BrainOS/`
   > - 🔗 AI Runner Bridge configured without overwriting existing root files
   > - 🧪 Test Suite: **13 / 13 Assertions PASSED (100% Coverage)**
   > 
   > 💡 *To start immediately, place a raw note or link into `0-Inbox/` and run `arca-inbox-process`!*
