# 🛠️ Skill : arca-inbox-process (Inbox Processing & Triage)

- **Reference Process:** [[Process-Inbox-Clean-and-Dispatch]]

## Trigger
Execute when user enters `arca-inbox-process` (or `inbox-process`).

## Objective
Clean, structure, and route raw notes in `0-Inbox/`. Acts as an entry router identifying category (`idea`, `action`, `project-seed`, `source`) and routing to target skills (`arca-organize-idea` or `arca-distill`).

## Sequential Execution Workflow
1. **Scan & Preliminary Analysis:** Target specified note or scan all `.md` files in `0-Inbox/`.
2. **Category Triage:**
   - 📚 `category: source` ➔ Route to `Skill_arca-distill.md`.
   - 💡 `category: idea` ➔ Apply `Skill_arca-organize-idea.md`.
   - ⚡ `category: action` ➔ Invoke `Skill_arca-organize-idea.md` for task injection.
   - 🌱 `category: project-seed` ➔ Invoke `Skill_arca-organize-idea.md` for project pre-creation.
3. **Interactive Validation:** Clarify ambiguities in chat before writing.
4. **Log:** Record action in `_Arca-BrainOS/log.md`.
