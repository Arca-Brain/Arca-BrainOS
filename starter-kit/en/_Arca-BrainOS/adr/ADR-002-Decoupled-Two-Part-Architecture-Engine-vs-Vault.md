---
date: "2026-08-09"
title: "ADR-002 : Decoupled Two-Part Architecture (Engine _Arca-BrainOS/ vs User Vault)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-002 : Decoupled Two-Part Architecture (Engine _Arca-BrainOS/ vs User Vault)

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Integrating an autonomous AI into a knowledge vault often causes contamination: system prompts, scripts, temporary files, and user notes become tangled together, preventing clean updates and increasing user cognitive load.

---

## 2. Decision
The system enforces a **strict physical and logical boundary in two distinct parts**:

1. **Part 1: The Sovereign User Vault:** Houses user content (`0-Inbox/`, `1-Projects/`, `2-Ressources/`, `3-Domaines-de-vie/`, `4-Archives/`). The user remains master of their intellectual space.
2. **Part 2: The Self-Contained Engine (`_Arca-BrainOS/`):** Encapsulates all agentic logic, skills, templates, process guides, scripts, and logs. It can be dropped into an existing vault or updated via Git subtree/submodule without altering user files.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Safe, painless updates of the cognitive engine.
  - Zero accidental exposure of user personal notes in public open-source forks.
  - Clear architectural mental model.
- **Accepted Trade-offs & Constraints:**
  - Requires relative path resolution via canonical path variables (`PATH_*`).

---

## 4. Alternatives Considered
- **Scattering prompts across notes:** Rejected due to cognitive clutter and maintenance impossibility.
- **Pure external daemon outside the vault:** Rejected because storing prompts as vault markdown files allows bidirectional linking and transparency.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
