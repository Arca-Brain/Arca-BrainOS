---
date: "2026-08-09"
title: "ADR-009 : Four-Layer Frugal CoALA Memory Model (_Arca-BrainOS/memory.md)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-009 : Four-Layer Frugal CoALA Memory Model (_Arca-BrainOS/memory.md)

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
AI agent memory often suffers from two extremes: total amnesia between sessions, or bloated vector memory databases that hallucinate, degrade token windows, and introduce heavy technical dependencies.

---

## 2. Decision
Arca-BrainOS implements a **4-tier frugal memory architecture inspired by the CoALA framework**:

1. **Level 1 (Working Memory):** Current chat context and active scratch files.
2. **Level 2 (Episodic Memory):** Single-line chronological ledger in `_Arca-BrainOS/log.md` and project worklogs.
3. **Level 3 (Operational Semantic Memory):** `_Arca-BrainOS/memory.md`, strictly kept under 50 lines. Stores cross-project learnings, current focus, and behavioral preferences.
4. **Level 4 (Constitutional Invariants):** `AGENTS.md` (topography, rules, skill declarations) and `_Arca-BrainOS/adr/` (architectural decisions).

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Token-frugal, lightning-fast context loading.
  - 100% human-editable in plain Markdown.
  - Zero database dependency.
- **Accepted Trade-offs & Constraints:**
  - Requires active curation to keep `memory.md` under 50 lines (pruning via `arca-audit`).

---

## 4. Alternatives Considered
- **Vector database (Chroma, Pinecone, LanceDB):** Rejected due to setup friction, opacity, and token cost.
- **No persistent memory:** Rejected because the agent repeatedly made the same procedural mistakes.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
