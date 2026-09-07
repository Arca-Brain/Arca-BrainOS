# 🛠️ Skill : arca-close-session (Session Closure & Memory)

- **Reference Process:** [[Process-Project-Management-and-Deep-Work]] & [[Process-Cross-Project-Capitalization-and-MOC]]

## Trigger
Execute when the user enters `arca-close-session` (or `close-session` / `brain-close-session`) followed by the target project note link.

## Sequential Execution Workflow

1. **Session Analysis & End Timestamp:**
   - Review recent console history and `_Arca-BrainOS/log.md` to list actions performed during this run.
   - Open target project note and locate active session block at top of `## 🪵 Journal de Bord des Sessions`.
   - Calculate real duration ($\Delta t_{\text{real}}$) and estimate manual baseline without AI ($T_{\text{manual}}$).

2. **Main Task List Update (Single Source of Truth):**
   - Locate top task section (`## 🚀 Actions Prochaines Étapes`).
   - Check (`[x]`) completed tasks.
   - Append new identified tasks as active checkboxes (`- [ ]`).

3. **Session Log Finalization:**
   - Replace temporary pending block at top of `## 🪵 Journal de Bord des Sessions` with finalized report.
   - **Absolute Rule:** Do NOT use active checkboxes (`- [ ]`) inside the log section. Use simple bullet points (`-`).

4. **Project Cumulative Metadata Update (Frontmatter YAML):**
   - Read existing metadata: `sessions_count`, `total_real_duration`, `total_estimated_manual`, `total_time_saved`.
   - Increment sessions (`sessions_count: +1`).
   - Update last session date (`last_session: "YYYY-MM-DD"`).
   - Recalculate totals and net time saved (`total_time_saved`).

5. **Habit Detection & Frugal Memory (`memory.md`):**
   - Review session interactions to detect recurring user corrections or strong workflow preferences.
   - If a high-signal rule is detected, suggest adding it to `_Arca-BrainOS/memory.md` in chat (never edit without explicit user consent).

6. **Global System Logging:**
   - Append log line in `_Arca-BrainOS/log.md`:
     `[YYYY-MM-DD HH:mm] - Session closed for [[Project-Name]] (Duration: XhYY | Manual: ~AhBB | Saved: +ChDD)`

7. **Adaptive & Resilient Git Snapshot & Backup:**
   - Verify if the vault is a valid Git repository (`git rev-parse --is-inside-work-tree 2>/dev/null`).
     - *If false (or Git not installed):* Silently skip this step without error (zero friction for beginners).
   - *If the vault is a valid Git repository:*
     - Check for pending changes across the vault (`git status --porcelain`).
     - If modifications exist, stage all files and seal the session commit:
       ```bash
       git add .
       git commit -m "Session Deep Work [YYYY-MM-DD]: [Session Title]"
       ```
     - **Adaptive Remote Push:**
       - If remote `nas` exists (`git remote | grep -q "^nas$"`), attempt `git push nas`. If unreachable (e.g., disconnected network mount), proceed without error and notify gracefully: *"Local commit sealed. NAS unreachable (push deferred to next connection)."*
       - Else if remote `origin` exists (`git remote | grep -q "^origin$"`), attempt `git push origin`.
       - If no remote is configured (100% local Git), simply confirm the local commit.

