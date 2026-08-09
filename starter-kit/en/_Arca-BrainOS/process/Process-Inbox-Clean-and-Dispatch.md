---
id: "202607172326"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - inbox
  - pkm
  - ai
---
# Process : Inbox Clean & Dispatch

- **Frequency** : Daily / Weekly
- **Trigger** : Accumulation of raw notes, voice transcripts, or web captures in `0-Inbox/`.

---

## Input
* Raw files in `0-Inbox/`.
* Theme MOCs (`T-`) in `2-Ressources/Themes/` and active projects (`P-`) in `1-Projects/`.

## Steps
1. **Launch AI Triage**: Invoke `arca-inbox-process` on `0-Inbox/`.
2. **Normalize YAML**: AI cleans frontmatter (`id`, `category`, `tags`, `status`).
3. **Detect Duplicates & Route**:
   - External source (video, article) ➔ Route to `arca-distill`.
   - Personal idea ➔ Invoke `arca-organize-idea` (Preserve Raw Note + Formulate Key Idea + Link to Project).
4. **Validate Proposals**: User accepts or adjusts proposed project tasks and links.
5. **Move File**: Move completed note to permanent directory (`2-Ressources/Notes/` or `1-Projects/`).
