---
date: "2026-10-02"
title: "ADR-011 : Adoption of a Single MIT Open-Source License"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - legal
target: "[[P-Project-Alpha]]"
---

# 📜 ADR-011 : Adoption of a Single MIT Open-Source License

---

## 1. Context & Problem Statement
At the v1.0.0-MVP release, Arca-BrainOS initially adopted a hybrid dual-licensing model: code and skills (`skills/`) were licensed under GNU AGPLv3, while playbooks, documentation, and the manifesto were licensed under Creative Commons CC BY-NC-SA 4.0.

This initial choice aimed to protect the project against commercial capture by third-party vendors (reselling closed kits or operating uncontributed SaaS platforms). However, real-world adoption feedback revealed three major points of friction:
1. **Corporate AGPLv3 aversion:** In enterprise environments, legal and security teams routinely ban AGPLv3 due to fears of viral copyleft contamination on proprietary intellectual property. This creates a barrier for employees and decision-makers wishing to use Arca-BrainOS on corporate workstations.
2. **Cognitive friction of dual licensing:** Combining two distinct licenses complicates understanding the granted rights and slows down community contributions.
3. **Alignment with the Manifesto and project ethos:** Arca-BrainOS advocates for emancipation from information monopolies and the preservation of thought in an open format. Restricting documentation via a Non-Commercial clause conflicted with the mission of spreading a universal digital commons.

---

## 2. Decision
Arca-BrainOS formally drops the hybrid dual-licensing model (AGPLv3 + CC BY-NC-SA 4.0) in favor of a **single universal MIT License**.

The entire public repository `Arca-Brain/Arca-BrainOS` (code, scripts, agentic skills, process guides, playbooks, templates, and documentation) is now distributed under the MIT License.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - **Frictionless adoption:** De facto universal standard on GitHub, across the Obsidian ecosystem, and in the CLI agent community.
  - **Full enterprise compatibility:** Immediate removal of corporate legal roadblocks (compatible with enterprises, SMBs, and independent workers).
  - **Absolute legal clarity:** A single concise `LICENSE` file, a green `License: MIT` badge, and zero ambiguity for users and contributors.
  - **Ideological alignment:** Reinforces the legitimacy of Arca-BrainOS as a free, open standard for a sovereign personal cognitive operating system.
- **Accepted Trade-offs & Constraints:**
  - **Permissive commercial reuse:** Third parties may legally integrate or redistribute system components. This risk is considered minor and acceptable, as real value lies in continuous improvements, community trust, and human guidance.

---

## 4. Alternatives Considered
- **Retaining the Hybrid Model (AGPLv3 + CC BY-NC-SA 4.0):** Rejected because it penalizes enterprise adoption and contradicts the spirit of openness promoted by the manifesto.
- **Apache 2.0 License:** Considered for its explicit patent and trademark clauses, but deemed less immediately readable and idiomatic than the MIT standard for a Markdown-centric vault.
- **Unified GPLv3:** Rejected because it maintains a copyleft requirement perceived as overly restrictive by corporate IT departments.

---

## 5. References & Links
- Master Project: [[P-Project-Alpha]]
- Reference Files: `LICENSE`, `LICENSE.md`, `README.md`, `README.fr.md`, `CONTRIBUTING.md`, `CONTRIBUTING.fr.md`
