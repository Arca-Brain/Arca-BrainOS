# 🛠️ Skill : arca-distill (Master Orchestration Skill)

## Trigger
Execute when the user enters `arca-distill` (or `distill` / `brain-distill`) followed by a file name or link in `0-Inbox/`.

## Sequential Execution Workflow
1. **Step 1 : Synthesis & Distillation**
   - Load raw source into memory.
   - Invoke `Skill_arca-synthesize.md` to generate structured note `AI-Distil-[Name].md` in `2-Ressources/IA-generated/`.

2. **Step 2 : Convergence & Auto-linking**
   - Apply `Skill_arca-converge.md` on newly generated note.

3. **Step 3 : Physical Archiving & Inbox Cleaning**
   - Move raw source file from `0-Inbox/` to `2-Ressources/Notes/`.

4. **Step 4 : Impact Analysis & Project Alignment**
   - Invoke `Skill_arca-impact.md` to propose integration recommendations for active projects.

## Output
Display summary in chat: "Orchestration complete: Source distilled, anchored, and archived into Vault."
