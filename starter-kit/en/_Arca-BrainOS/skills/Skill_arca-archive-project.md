---
name: arca-archive-project
description: Cleanly close and physically archive a project note to 4-Archives/Projets/, with task audits, optional learning extraction (into memory.md), Life Area updates, and worklog traceability.
---

# 🛠️ Skill: arca-archive-project (Project Final Closure & Archiving)

- **Reference Process:** [[Process-Project-Archiving]]

## Specific Triggers & Direct Aliases
This skill is triggered by any of the following commands followed by the project name/link:
- `arca-archive-project [[P-Project-Name]]`
- `archive-project [[P-Project-Name]]`
- `brain-archive-project [[P-Project-Name]]`

---

## 🏛️ Golden Rule: Interactive Validation & Frugality
1. **Prior Confirmation:** The agent never moves a project without explicit user confirmation in chat.
2. **Non-Intrusive Learning:** Learning extraction is proactive but optional. If the user wants to archive directly, the agent proceeds immediately.
3. **Constitution Sanctity:** Operational rules go to `_Arca-BrainOS/memory.md`, never into `AGENTS.md`.
4. **Natural Naming:** All concept or lesson notes are saved with natural titles in `2-Ressources/Notes/[Title].md` with tag `learning`.

---

## Sequential Execution Workflow

### 1. Load & Residual Task Audit
- Load target project note (`P-[Project-Name].md`) in `PATH_PROJECTS` (or `PATH_INCUBATION`).
- Scan for open tasks (`- [ ]`):
  - If open tasks remain, list them and ask user to:
    - Check them if completed (`[x]`).
    - Strike them out if dropped (`~[ ]~`).
    - Move them as raw seeds under `## 🌱 Backlog & Future Ideas` in the parent Life Area.
- Ask for confirmation: *"All tasks are resolved. Do you confirm final archiving of `P-[Project-Name]`?"*

---

### 2. Learning Detection & Capitalization (Optional)
- Briefly scan `## 🪵 Journal de Bord des Sessions` (or session log) for:
  - Key reusable principles, takeaways, or post-mortem lessons.
  - Practical interaction rules or preferences.
- Present concise options in chat:
  - **Knowledge Note Option:** Create a standard concept note in `PATH_NOTES` (`2-Ressources/Notes/[Title].md`, tag `learning`, linked to MOC Theme).
  - **System Rule Option:** Record a micro-rule in `_Arca-BrainOS/memory.md` (anti-pollution filtered).
  - **Direct Archive Option:** Proceed immediately to physical archiving without note creation.

---

### 3. Seal YAML Frontmatter
- Update project frontmatter:
  - `status: "completed"`
  - Replace tag `status/active` (or `status/someday`) with `status/completed`.
  - Set `last_session: "YYYY-MM-DD"` with today's date.

---

### 4. Physical Move to Archives
- Execute atomic move to archives folder:
  `mv 1-Projects/P-[Project-Name].md 4-Archives/Projets/` (or from `1-Projects/_Incubation/`).

---

### 5. Update Parent Life Area
- Identify parent Areas declared in `areas`.
- In `### 🏁 Projets & chantiers de l'année` (or annual projects section) of the parent Area, append:
  `- [[P-Project-Name]] : [Short description] (✔ Terminé)`
- Area Dataview archive table immediately reflects the archived project.
- `Home.md` dashboard updates metrics in real time (active projects decremented, archives incremented, time saved preserved).

---

### 6. System Worklog
- Append single action line in `PATH_SYSTEM/log.md`:
  `[YYYY-MM-DD HH:mm] - AI Action (Archiving): Project [[P-Project-Name]] archived to 4-Archives/Projets/ (status: completed)`
EOF && \
cp _release-github-arca-brainos/starter-kit/en/_Arca-BrainOS/skills/Skill_arca-archive-project.md _release-github-arca-brainos/starter-kit/en/starter-vault/_Arca-BrainOS/skills/Skill_arca-archive-project.md
