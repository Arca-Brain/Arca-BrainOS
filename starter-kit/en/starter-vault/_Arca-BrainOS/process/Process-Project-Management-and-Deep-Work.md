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
1. **Start & Frame Session**: Run `arca-resume @[Project]` to scan status, receive intention proposal, and log start timestamp `[HH:mm]`.
2. **Clarify Intention**: Align AI on exact focus.
3. **Execute Work**: Co-create code, documents, or methods.
4. **Close Session**: Run `arca-close-session @[Project]` to check completed tasks, log end timestamp `[HH:mm]`, calculate real duration vs manual baseline, and update cumulative YAML metadata (`total_real_duration`, `total_time_saved`).
