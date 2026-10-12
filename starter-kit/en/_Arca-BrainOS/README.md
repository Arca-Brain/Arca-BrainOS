# 🧠 Arca-BrainOS Cognitive Engine

> *Welcome to the core of the Arca-BrainOS Second Brain. This directory contains the complete software infrastructure, agentic skills, macro-processes, templates, memories, and system logs.*

---

### 📂 Subdirectory Architecture

- **`[[_Arca-BrainOS/skills/README|skills/]]`** : *Agentic Skills*
  Houses all AI-executable workflows (`Skill_arca-*.md`) for inbox triage, distillation, health audits, and Deep Work.
- **`[[_Arca-BrainOS/process/README|process/]]`** : *Macro-Process Specifications*
  Contains documentation of cognitive thinking workflows and Human/AI collaboration role matrices.
- **`[[_Arca-BrainOS/templates/README|templates/]]`** : *Standard Obsidian Note Templates*
  Provides normalized templates for projects, processes, ideas, and session logs.
- **`[[_Arca-BrainOS/scripts/README|scripts/]]`** : *Scripts & Automated Registries*
  Houses shell utilities (YouTube ingestion) and duplicate prevention registries.
- **`[[_Arca-BrainOS/adr/README|adr/]]`** : *Architecture Decision Records*
  Official registry of foundational architectural decisions and structural trade-offs (ADR-001 to ADR-011).
- **`tests/`** : *Agentic Test Bench & Fixtures*
  Contains test fixtures (`fixtures/`) and the automated non-regression evaluation suite (`arca-test`).

---

### 📄 Engine System Files & Memories

- **[[memory]]** : *Operational Memory & Learned Preferences*
  Short/medium-term learning buffer for the AI agent, strictly capped under 50 lines (style guidelines, technical habits, project REX).
- **[[rules-email]]** : *Business Rules & Email Triage Preferences*
  Specialized memory for `arca-email-process` storing learned sender rules across the 3 GTD batches (noise, reference, actions).
- **[[log]]** : *Chronological System Log*
  Records every system and AI-executed action on a single timestamped line.
- **[[audit-log]]** : *Audit History & ROI Executive Summary*
  Tracks temporal vault health trends, project productivity gains, and long-term metrics.
- **[[index]]** : *RAG Index & Centralized Semantic Map*
  Indexes distilled knowledge and MOC themes to empower contextual semantic retrieval.
