---
id: "202607172329"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - capitalization
  - moc
  - pkm
  - ai
---
# Process : Cross-Project Capitalization & MOC Synthesis

- **Frequency** : Monthly / On Milestone
- **Trigger** : Project completion or major milestone reached.

---
## Steps
1. **Analyze Knowledge Assets**: Scan `1-Projects/` for key learnings and deliverables.
2. **Execute Cross-Synthesis**: Run `compound` or `knowledge` skill to extract recurring ideas across projects.
3. **Update Theme MOCs**: Run `moc-update` to anchor new learnings into `T-` themes.
4. **Index & Log**: Refresh `_Arca-BrainOS/index.md` and log entry.

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Cross-Project Knowledge Synthesis
- **User Prompt:** *"Analyze my completed projects and extract key architecture principles into a synthesis note"*
- **Agentic Orchestration:** Scans project worklogs, extracts universal lessons, drafts `AI-Synthesis-[Topic].md`.

### 🔗 Associated Agentic Skills
- [[Skill_arca-converge]], [[Skill_arca-create-note]], [[Skill_arca-close-session]].

