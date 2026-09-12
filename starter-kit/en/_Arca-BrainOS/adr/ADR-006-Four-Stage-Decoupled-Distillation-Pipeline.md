---
date: "2026-08-09"
title: "ADR-006 : Four-Stage Decoupled Distillation Pipeline (arca-distill)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-006 : Four-Stage Decoupled Distillation Pipeline (arca-distill)

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Monolithic distillation prompts that try to summarize, link, archive, and extract project tasks in a single LLM turn frequently hallucinate links, drop key concepts, or fail mid-execution.

---

## 2. Decision
The distillation process is decomposed into **4 atomic, sequentially orchestrated skills**:

1. **Synthesis (`arca-synthesize`):** Extracts core mental models into `2-Ressources/IA-generated/AI-Distil-[Name].md`.
2. **Convergence (`arca-converge`):** Anchors the new note into relevant Theme MOCs (`T-`) and activates reciprocal wikilinks.
3. **Archiving (`mv`):** Physically moves the raw source out of `0-Inbox/`.
4. **Impact Analysis (`arca-impact`):** Interactively checks active projects (`P-`) to propose concrete next actions derived from the new knowledge.

The master skill `arca-distill` coordinates the pipeline while each sub-skill remains callable independently.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - High reliability and clean error recovery.
  - Reusability of individual pipeline stages.
- **Accepted Trade-offs & Constraints:**
  - Slightly longer execution time across sequential steps.

---

## 4. Alternatives Considered
- **Single monolithic prompt:** Rejected due to cognitive degradation and frequent incomplete outputs.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
