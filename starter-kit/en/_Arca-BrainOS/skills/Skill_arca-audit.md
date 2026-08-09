# 🛠️ Skill : arca-audit (Maintenance, Vault Health & Time Audit)

## Trigger
Execute this workflow when the user enters `arca-audit` (or `audit` / `brain-audit`).

## Objective
Scan the vault structure to detect friction, orphan notes, maintain graph integrity (Inbox, MOCs, `IA-generated/`), and establish AI ROI metrics for active and archived projects.

## Sequential Execution Workflow

1. **Impact Ratio Calculation (PARA Health Index):**
   - Scan `2-Ressources/IA-generated/` for all `AI-Distil-` notes.
   - Analyze the `## Application & Impact` section of each note.
   - Calculate the percentage of notes linked to a project (`[[P-` or `[[T-`) versus total notes.
   - If unlinked notes exceed 35%, trigger an alert against the "Collector's Fallacy".

2. **Orphan Note Detection (Inbox & IA-generated):**
   - Scan `0-Inbox/Youtube/` and `2-Ressources/IA-generated/`.
   - Identify notes not listed in any `T-` theme MOC or `Home.md`.

3. **Broken Link Analysis (Ghost Links):**
   - Detect `[[Non-Existent-File]]` syntax across recent distilled notes.
   - List missing concepts that warrant creating a new note or MOC.

4. **Documentation & README Coverage Check:**
   - Scan all `Skill_arca-*.md` in `skills/` and `Process-*.md` in `process/`.
   - Verify every file is referenced as a wikilink in `skills/README.md` and `process/README.md` as well as `AGENTS.md`.

5. **Project Time & ROI Consolidation (Active & Archived):**
   - Scan all project files in `1-Projects/` and `4-Archives/Projets/`.
   - Extract YAML metadata: `sessions_count`, `total_real_duration`, `total_estimated_manual`, `total_time_saved`.
   - Calculate total sessions, real Deep Work hours, manual estimate, net time saved, and overall speed multiplier.

6. **Logging & Audit Log Archiving:**
   - Update `_Arca-BrainOS/audit-log.md` with timestamps and executive summary.
   - Log execution line in `_Arca-BrainOS/log.md`: `[YYYY-MM-DD HH:mm] arca-audit -> Vault health diagnostic complete`.

## Output Format (Dashboard)
Display a clean Flash Report in console:
- **📊 Impact Ratio:** [Percentage]% of notes linked to active projects (Target: > 65%)
- **⏱️ Time & Productivity Summary:**

| Category | Projects | Sessions | Real Time | Manual Est. | Time Saved | Speed |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 🟢 **Active** | [N_active] | [S_active] | [T_real_active] | [T_manual_active] | 🚀 **+[Gain_active]** | **x[Speed_active]** |
| 📦 **Archived** | [N_arch] | [S_arch] | [T_real_arch] | [T_manual_arch] | 🚀 **+[Gain_arch]** | **x[Speed_arch]** |
| 🏁 **TOTAL** | **[N_total]** | **[S_total]** | **[T_real_total]** | **[T_manual_total]** | 🚀 **+[Gain_total]** | **x[Speed_total]** |
