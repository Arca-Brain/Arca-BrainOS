---
date: "2026-08-09"
title: "ADR-007 : Project Dichotomy (Intellectual Research vs Real-World Practical)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-007 : Project Dichotomy (Intellectual Research vs Real-World Practical)

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Not all projects share the same nature. An intellectual project (writing a book, conducting AI research) feeds into thematic maps of content (`T-`), whereas a practical life project (home renovation, medical reimbursement) produces real-world outcomes without generating abstract conceptual knowledge. Forcing all projects into thematic MOCs pollutes conceptual maps with administrative trivia.

---

## 2. Decision
Arca-BrainOS formalizes an ontological dichotomy:

1. **Intellectual & Thematic Projects:** Declared with `themes: ["[[T-Name]]"]`. Their syntheses and insights flow into the conceptual graph.
2. **Real-World & Practical Projects:** Declared with `themes: []`. They connect exclusively to Life Areas (`3-Domaines-de-vie/`) and do not pollute knowledge MOCs.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Clean, unpolluted conceptual knowledge graph.
  - Full support for everyday practical task tracking alongside intellectual research.
- **Accepted Trade-offs & Constraints:**
  - Users must classify project nature during instantiation (`arca-create-note`).

---

## 4. Alternatives Considered
- **Single uniform model for all projects:** Rejected because administrative projects cluttered philosophical and technical MOCs.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
