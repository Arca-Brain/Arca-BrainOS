# 🛠️ Skill : arca-impact (Impact Analysis & Project Alignment)

## Trigger
Execute when user enters `arca-impact` followed by a distilled note, or automatically invoked by `arca-distill`.

## Objective
Analyze a newly distilled note to identify potential impact on active projects (`1-Projects/`) or themes (`2-Ressources/Themes/`), present interactive recommendations, and apply user-validated changes.

## Sequential Execution Workflow
1. **Context Search:** Scan `1-Projects/` for active projects (`P-[Name].md`) or lessons (`L-[Name].md`).
2. **Impact Diagnostic:** Formulate recommendations along 3 axes:
   - 💡 Strategic Alignment / Pivot
   - ⚙️ Tactical Actions / Tasks (`- [ ]`)
   - 🧠 Knowledge to Integrate
3. **Interactive Validation:** Present diagnostic in chat and ask for confirmation before modifying human project files.
4. **Application & Logging:** Apply approved changes to projects and record impact in `## Application & Impact` section of distilled note.
