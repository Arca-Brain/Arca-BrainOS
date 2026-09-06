---
id: "202609061828"
category: Process
date_created: "2026-09-06"
tags:
  - process
  - project
  - archiving
  - capitalization
  - gtd
---

# Process: Project Archiving & Experience Capitalization

- **Frequency:** On Trigger (Upon completion or retirement of an active or incubating project).
- **Trigger:** Decision to permanently close project `P-[Project-Name]`.
- **Current Duration:** ~5 min (instead of 20 min of manual file moves, missed area updates, and lost lessons learned).

---

## Input
* Target project note `P-[Project-Name]` located in `1-Projects/` (or `1-Projects/_Incubation/`).
* Session worklogs (`## 🪵 Journal de Bord des Sessions`).
* Parent Life Area note (`3-Domaines-de-vie/`).
* Operational memory file (`_Arca-BrainOS/memory.md`).

---

## Steps

1. **Audit & Task Resolution:**
   - Run `arca-archive-project [[P-Project-Name]]`.
   - The agent audits the note for lingering open tasks.
   - Tasks are either marked done (`[x]`), struck out (`~[ ]~`), or migrated to backlog seeds in the parent Area.

2. **Targeted Capitalization (Optional):**
   - The agent analyzes the project journey and proposes 1 or 2 high-signal learnings:
     - Standard concept note in `2-Ressources/Notes/` (tag `learning`, linked to an MOC Theme).
     - New recurring preference in `_Arca-BrainOS/memory.md` (filtered for anti-pollution, without touching `AGENTS.md`).
   - The user decides in one word (approve, reject, or archive directly).

3. **Sealing & Physical Archiving:**
   - Project metadata is sealed (`status: "completed"`, tag `status/completed`, last session date).
   - The file is physically moved to `4-Archives/Projets/` via shell command.

4. **Life Area & Dashboard Update:**
   - The project line in the parent Area note is marked with `(✔ Terminé)`.
   - Area Dataview tables and `Home.md` update immediately while preserving cumulated AI time saved.

---

## Quality Standards

* **DO:**
  * Always require human confirmation before moving files.
  * Preserve all human-written content in the archived project.
  * Keep `memory.md` strictly frugal (under 50 lines total).
* **DON'T:**
  * Never alter `AGENTS.md` to record project learnings.
  * Name reflection or learning notes naturally without artificial prefixes.
  * Do not let finished projects linger indefinitely in `1-Projects/`.

---

## Output
* Sealed project note physically moved to `4-Archives/Projets/`.
* Optional concept note created in `2-Ressources/Notes/` or rule saved in `memory.md`.
* Parent Area updated with `(✔ Terminé)`.
* `Home.md` dashboard metrics updated live.
* Single action line logged in `_Arca-BrainOS/log.md`.
EOF && \
cp _release-github-arca-brainos/starter-kit/en/_Arca-BrainOS/process/Process-Project-Archiving.md _release-github-arca-brainos/starter-kit/en/starter-vault/_Arca-BrainOS/process/Process-Project-Archiving.md
