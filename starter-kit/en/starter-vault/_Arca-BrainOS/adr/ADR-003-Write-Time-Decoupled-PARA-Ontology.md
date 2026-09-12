---
date: "2026-08-09"
title: "ADR-003 : Write-Time Decoupled PARA Ontology vs Rigid Folders"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-003 : Write-Time Decoupled PARA Ontology vs Rigid Folders

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Strict folder-based PARA models (Projects, Areas, Resources, Archives) suffer from classification rigidity: moving notes breaks wikilinks and creates maintenance friction. Conversely, naive RAG without ontological scaffolding produces hallucinated associations and unstructured search results.

---

## 2. Decision
Arca-BrainOS adopts a **hybrid model: loose physical storage paired with rigorous semantic write-time metadata**:

1. **Semantic Prefixes:** Fast visual identification (`P-` for Projects, `T-` for Themes/MOCs).
2. **Rigorous YAML Frontmatter:** Every note declares typed relationships (`projects`, `themes`, `areas`, `category`) at creation time.
3. **Dynamic Graph Traversal:** Dynamic MOC views and Dataview queries aggregate knowledge on the fly regardless of nested folder structure.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - High resilience against folder restructuring.
  - Rich semantic queries and precise context retrieval for LLMs.
- **Accepted Trade-offs & Constraints:**
  - Requires strict frontmatter hygiene enforced by skills like `arca-inbox-process`.

---

## 4. Alternatives Considered
- **Deep hierarchical folders:** Rejected because deep nesting causes cognitive fatigue and broken links.
- **Pure tag-only system:** Rejected due to lack of relational semantics and high tag sprawl.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
