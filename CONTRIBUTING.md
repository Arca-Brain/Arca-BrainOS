---
date: 2026-08-09
title: "CONTRIBUTING.md : Guidelines for Contributing to Arca-BrainOS"
description: Official contribution guidelines for creating skills, methodological process guides, playbooks, and maintaining test suite compliance in Arca-BrainOS.
tags:
  - contributing
  - open-source
  - guidelines
  - developer
  - arca-brainos
status: "#completed"
---

# 🤝 CONTRIBUTING: Arca-BrainOS

Thank you for your interest in contributing to **Arca-BrainOS**! 

Arca-BrainOS is designed as a **Simondonian "Open Technical Object"**: a transparent, modular, and extensible system built by and for thinkers, builders, and knowledge workers. We welcome contributions that expand skills, refine methodological guides, or improve vault health telemetry.

---

## 🎯 1. Types of Contributions Welcome

You can contribute to Arca-BrainOS in several ways:

1. **🔌 New Agentic Skills (`Skill_arca-*.md`)** : Creating modular skills stored in `_Arca-BrainOS/skills/` to automate specific cognitive, research, or organization workflows.
2. **📚 Methodological Process Guides (`Process-*.md`)** : Writing human/AI process documentation stored in `_Arca-BrainOS/process/`.
3. **📘 Operational Playbooks (`Playbook-*.md`)** : Designing step-by-step enablement guides stored in `_Arca-BrainOS/playbooks/`.
4. **🧪 Test Suite Assertions (`_Arca-BrainOS/tests/`)** : Adding assertions and fixtures to `Skill_arca-test-suite.md` to prevent regressions.
5. **🐛 Bug Fixes & Documentation Improvements** : Clarifying guides, updating READMEs, or fixing path handling.

---

## 📏 2. Architectural Guidelines & Conventions

When creating or modifying components, adhere strictly to the following core rules:

### A. Folder-Agnostic Path Variables
Never hardcode absolute paths or fixed local folders in skills. Always reference canonical path variables defined in `AGENTS.md`:

```yaml
PATH_INBOX: "0-Inbox/"
PATH_PROJECTS: "1-Projects/"
PATH_AREAS: "3-Domaines-de-vie/"
PATH_THEMES: "2-Ressources/Themes/"
PATH_IA_GENERATED: "2-Ressources/IA-generated/"
PATH_SYSTEM: "_Arca-BrainOS/"
```

### B. Preserve Human Voice (Rule 2)
Agentic skills must **never** delete, overwrite, or silent-patch human-authored text inside project notes (`P-`), lessons (`L-`), or life areas (`3-Domaines-de-vie/`). Skills may only suggest wikilinks (`[[...]]`), update task checkboxes (`- [ ]`), or append worklog entries during session closure.

### C. Unconditional README & Index Maintenance (Rule 4)
Any addition, creation, or renaming of a skill (`Skill_arca-*.md`), process guide (`Process-*.md`), or playbook (`Playbook-*.md`) **MUST** immediately be accompanied by updates to:
1. The parent index README (`skills/README.md`, `process/README.md`, or `playbooks/README.md`).
2. The central system prompt index [`AGENTS.md`](AGENTS.md).

### D. Self-Documenting Skill Creation Rule
You can ask your AI terminal agent to build skills for you! A well-written skill should include:
- A clear **Trigger** (`## Déclencheur`).
- An **Objective** (`## Objectif`).
- A **Sequential Execution Workflow** (`## Workflow d'Exécution Séquentiel`).

### E. Creating & Contributing Custom Skills or Process Guides
If you want to create a custom skill or contribute a third-party module (e.g., voice note capture, external tool integration, custom audit workflow):
1. **Create the file:** Place your skill in `_Arca-BrainOS/skills/Skill_arca-[name].md` (or `process/Process-[name].md`) using canonical relative path variables (`PATH_*`).
2. **AI-Assisted Design:** Ask your AI assistant to generate the skill: it will write the execution logic, add command aliases, and automatically update `AGENTS.md` and the parent folder `README.md`.
3. **Validation & Non-Regression:** Add a test assertion to `Skill_arca-test-suite.md` and run `arca-test` before opening your Pull Request.

---

## 🧪 3. Testing & Recette (`arca-test`)

Before submitting a Pull Request, verify that your contribution does not break existing vault functionality:

1. Add corresponding test fixtures or assertions to `_Arca-BrainOS/skills/Skill_arca-test-suite.md` if adding new skills.
2. Run the automated test suite in your AI terminal:
   ```bash
   arca-test
   ```
3. Ensure all quality assertions pass (`PASS`).

---

## 📥 4. Pull Request (PR) Workflow

1. **Fork the Repository:** Create your own fork of [Arca-BrainOS on GitHub](https://github.com/chug/Arca-BrainOS).
2. **Create a Feature Branch:**
   ```bash
   git checkout -b feature/my-new-skill
   ```
3. **Commit Your Changes:** Keep commits atomic and descriptive:
   ```bash
   git commit -m "feat(skills): add arca-web-capture skill and update index"
   ```
4. **Push to Your Fork & Open a PR:** Push your branch to GitHub and open a Pull Request against the `main` branch of Arca-BrainOS.

---

## 📜 5. Licensing of Contributions & Contributor Grant

To maintain a healthy, transparent relationship between the project and its open-source contributors, all Pull Requests are governed by the following clear terms:

1. **Public Recognition & Attribution:** Every contributor retains copyright over their original work and will be **publicly credited and acknowledged** in the GitHub commit history, repository contributor metrics, and official release notes.
2. **Contributor Grant:** By submitting a Pull Request to Arca-BrainOS, you grant Hugues (the original project author) a non-exclusive, perpetual, worldwide, royalty-free license to include, modify, distribute, and commercialize your contribution as part of the unified Arca-BrainOS ecosystem (including the open-source GitHub repository and official Pro starter kits).
3. **Dual License Alignment:**
   - Code, skills, and scripts are contributed under **GNU AGPLv3**.
   - Playbooks, process guides, and written content are contributed under **CC BY-NC-SA 4.0**.

---

<p align="center">
  <i>Thank you for helping build a sovereign, AI-native future for human thought!</i>
</p>
