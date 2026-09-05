---
id: "202607162356"
category: Process
date_created: "2026-07-16"
tags:
  - process
  - media
  - pkm
  - ai
---
# Process : Media Ingestion & Distillation

- **Frequency** : Daily / Weekly
- **Trigger** : Consumption of high-value YouTube video, podcast, or article.

---
## Input
* Raw transcript in `0-Inbox/`.
* Active projects `P-` and themes `T-`.

## Steps
1. **Capture Source**: Import raw transcript into `0-Inbox/` (or via `arca-youtube`).
2. **Launch Distillation**: Run `arca-distill [Filename]`.
3. **Generate Synthesis**: `arca-synthesize` creates `AI-Distil-[Name]` in `2-Ressources/IA-generated/`.
4. **Anchor Note (MOC Convergence)**: `arca-converge` updates `T-` theme MOCs.
5. **Project Impact Analysis**: `arca-impact` scans active `P-` projects and proposes tasks.
6. **Archive Raw File**: Move raw file from Inbox to `2-Ressources/Notes/`.

## 💡 Concrete Examples & Prompt Templates

### Case 1 : YouTube Video Ingestion
- **User Prompt:** `arca-youtube https://www.youtube.com/watch?v=...`
- **Agentic Orchestration ([[Skill_arca-youtube]]):** Fetches transcript, normalizes metadata (`url`, `category: media`), and creates raw note in `0-Inbox/Youtube/`.

### Case 2 : Full 4-Step Distillation Pipeline
- **User Prompt:** `arca-distill 0-Inbox/Youtube/transcript-video.md`
- **Agentic Orchestration ([[Skill_arca-distill]]):**
  1. **Conceptual Synthesis ([[Skill_arca-synthesize]]):** Drafts `AI-Distil-[Name].md` in `2-Ressources/IA-generated/`.
  2. **Theme Anchoring ([[Skill_arca-converge]]):** Updates target Theme MOC (`T-`).
  3. **Project Impact ([[Skill_arca-impact]]):** Proposes actionable tasks in active projects (`P-`).
  4. **Archiving:** Moves raw transcript to cold storage.

### 🔗 Associated Agentic Skills
- [[Skill_arca-distill]], [[Skill_arca-synthesize]], [[Skill_arca-converge]], [[Skill_arca-impact]], [[Skill_arca-youtube]].

