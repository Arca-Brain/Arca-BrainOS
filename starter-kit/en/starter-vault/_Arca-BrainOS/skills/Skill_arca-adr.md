# 🛠️ Skill : arca-adr (Architecture Decision Record Sealing)

- **Reference Process:** [[Process-Project-Management-and-Deep-Work]]

## Trigger
Execute this workflow when the user enters `arca-adr` (or `create-adr` / `brain-adr`), followed by the title or topic of the architecture decision. This skill is also naturally invoked at the conclusion of an `arca-grill` session.

## Objective
Formalize, number, and seal structural technical and conceptual decisions of Arca-BrainOS in the dedicated registry `_Arca-BrainOS/adr/` (inspired by software engineering ADRs). The ADR prevents regressions and ensures future AI sessions do not re-question settled foundational choices.

## Sequential Execution Workflow

### 1. Registry Scan, Numbering & Impact
- Scan `_Arca-BrainOS/adr/` to list existing records (`ADR-001`, `ADR-002`, etc.) and analyze their scope.
- Determine the next sequential 3-digit number (e.g. `001`, `002`, `011`...).
- **Impact & Supersession Check:** Check if the new decision replaces, amends, or deprecates an existing ADR. If so, update the earlier ADR's frontmatter (`status: superseded by [[ADR-XXX]]`).

### 2. Formal Drafting
- Load template `_Arca-BrainOS/templates/Template-ADR.md`.
- Draft the record faithfully reflecting recent discussions or the preceding `arca-grill` session:
  - Context & Problem Statement
  - Decision Adopted
  - Consequences & Trade-offs
  - Alternatives Considered

### 3. Registration & Linking
- Save the file under canonical path:
  `_Arca-BrainOS/adr/ADR-[Number]-[Normalized-Title].md`
- Add link in `P-Arca-BrainOS.md` under Working Documents (Architecture cluster).
- Log single line in `_Arca-BrainOS/log.md`:
  `[YYYY-MM-DD HH:mm] - AI Action (Architecture) : Created [[ADR-[Number]-[Normalized-Title]]]`

## Output
Present the summary of the sealed decision and direct link to the user.
