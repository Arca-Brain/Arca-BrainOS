---
id: "202607172325"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - project
  - deepwork
  - ai
---
# Process : Project Management & Deep Work

- **Frequency** : On Trigger (At start and end of Deep Work sessions).
- **Trigger** : Decision to open a work run on an active project `P-[Name]`.

---
## Steps
1. **Start & Frame Session**: Run `arca-resume @[Project]` to load operational memory (`memory.md`), scan project status, receive intention proposal, and log start timestamp `[HH:mm]`.
2. **Clarify Intention**: Align AI on exact focus.
3. **Execute Work**: Co-create code, documents, or methods.
4. **Close Session**: Run `arca-close-session @[Project]` to check completed tasks, log end timestamp `[HH:mm]`, calculate real duration vs manual baseline, propose optional habit capture into `memory.md`, and update cumulative YAML metadata (`total_real_duration`, `total_time_saved`).

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Starting a Work Session (Cognitive Framing)
- **User Prompt:** `arca-resume 1-Projects/P-MyProject.md`
- **Agentic Orchestration ([[Skill_arca-resume]]):** Reads recent sessions, identifies active milestone, suggests 2-3 focused actions, initializes timestamped session header in project worklog.

### Case 2 : Closing a Work Session & AI ROI Tracking
- **User Prompt:** `arca-close-session 1-Projects/P-MyProject.md`
- **Agentic Orchestration ([[Skill_arca-close-session]]):** Inventories done/remaining tasks, collects actual duration, computes net time saved vs manual benchmark, writes session summary, updates frontmatter metadata.

### 🔗 Associated Agentic Skills
- [[Skill_arca-resume]], [[Skill_arca-close-session]].

