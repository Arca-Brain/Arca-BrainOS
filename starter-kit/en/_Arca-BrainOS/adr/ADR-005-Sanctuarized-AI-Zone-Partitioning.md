---
date: "2026-08-09"
title: "ADR-005 : Sanctuarized AI Writing Zone (2-Ressources/IA-generated/) and Human Text Inviolability"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-005 : Sanctuarized AI Writing Zone (2-Ressources/IA-generated/) and Human Text Inviolability

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Autonomous AI agents can inadvertently overwrite personal notes, destroy nuanced human reflections, or flood the vault with machine prose, eroding user trust in their Second Brain.

---

## 2. Decision
Arca-BrainOS establishes **strict territorial separation and human text inviolability**:

1. **Autonomous AI Writing Sandbox:** The agent may create, synthesize, and merge files autonomously *only* within `2-Ressources/IA-generated/` (prefixed with `AI-Distil-`).
2. **Inviolability of Human Notes:** The agent is strictly prohibited from deleting or rewriting human-authored text in project notes (`P-`), personal notes (`2-Ressources/Notes/`), or life areas.
3. **Supervised Operations Outside Sandbox:** Any write operation in other vault areas requires chat confirmation or strict append-only rules (e.g. session logs).
4. **Three-File Modification Cap:** Never modify or create more than 3 files per run without explicit confirmation.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - High user safety and complete trust.
  - Clear provenance: human writing vs machine distillation is instantly distinguishable.
- **Accepted Trade-offs & Constraints:**
  - Slightly more chat friction for multi-file operations.

---

## 4. Alternatives Considered
- **Unrestricted Agent Access across entire vault:** Rejected due to catastrophic risk of silent data distortion.
- **Zero Agent Writes (Read-only Assistant):** Rejected because automated synthesis is essential to relieve cognitive load.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
