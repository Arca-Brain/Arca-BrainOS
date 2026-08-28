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
