# 🛠️ Skill : arca-converge (MOC Integration & Convergence)

- **Reference Process:** [[Process-Media-Ingestion-and-Distillation]] & [[Process-Cross-Project-Capitalization-and-MOC]]

## Trigger
Execute when the user enters `arca-converge` (or `brain-converge`), typically followed by a distilled note or list of notes.

## Objective
Anchor newly distilled synthesis notes into the global Second Brain structure by updating Maps of Content (`T-` Theme MOCs) and ensuring bi-directional wikilink connections.

## Sequential Execution Workflow

1. **Theme Identification (MOC):**
   - Analyze source note (`AI-Distil-...`) and identify associated `T-` themes in `2-Ressources/Themes/`.
   - Create `T-[Theme].md` if it does not already exist.

2. **MOC Update (Top-Down Anchor):**
   - Open identified `T-[Theme].md`.
   - Add link to the new distilled note under `## 🧪 Synthèses & Distillations IA`.
   - Write a single-line micro-description next to the link.

3. **Note Linking (Bottom-Up Anchor):**
   - In the source distilled note, convert text suggestions in `## Connexions Suggérées` into active Obsidian wikilinks `[[T-[Theme]]]`.

4. **Indexing & System Logging:**
   - Add entry to central index `_Arca-BrainOS/index.md`.
   - Log execution line in `_Arca-BrainOS/log.md`: `[Date] - Convergence OK : [[AI-Distil-...]] anchored into [[T-[Theme]]]`.

## Guardrails
- **3-File Safety Rule:** If total modified files outside `IA-generated/` exceed 3, present plan in chat and ask for explicit confirmation before proceeding.
