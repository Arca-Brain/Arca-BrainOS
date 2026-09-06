---
id: "202607172327"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - rag
  - research
  - ai
---
# Process : Semantic Exploration & Research

- **Frequency** : On Trigger
- **Trigger** : Complex research question or need to synthesize scattered knowledge.

---
## Input
* Research question or topic.
* Vault notes (`AI-Distil-`, `PATH_NOTES`, `P-`).

## Steps
1. **Run Query**: Execute `arca-query "Your research topic"`.
2. **Cross-Scan & Triage**: AI crosses distilled notes, active projects, and raw Inbox sources.
3. **Map Knowledge**: AI outputs Flash Report in chat highlighting known facts, semantic bridges, and knowledge gaps.
4. **Capitalize Insights (Optional)**: Save key synthesis into `AI-Query-[Name].md`.

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Cross-Thematic Semantic Query
- **User Prompt:** `arca-query "What links Demis Hassabis's attention theory and Stiegler's organology in my notes?"`
- **Agentic Orchestration ([[Skill_arca-query]]):** Non-destructive semantic scan across vault notes and inbox, delivering conversational synthesis with wikilinks and knowledge gaps.

### 🔗 Associated Agentic Skills
- [[Skill_arca-query]], [[Skill_arca-distill]].

