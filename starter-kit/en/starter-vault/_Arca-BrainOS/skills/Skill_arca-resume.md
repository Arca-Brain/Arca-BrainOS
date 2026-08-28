# 🛠️ Skill : arca-resume (Deep Work Session Framing)

## Trigger
Execute when user enters `arca-resume` followed by target project note.

## Objective
Re-immerse user into project context before starting a work session. Review recent 2-3 sessions, highlight next milestone, and propose focused session intention.

## Sequential Execution Workflow
1. **Context Analysis:** Load project note and linked Working Documents. Read last 2-3 session log entries.
2. **Framing Diagnostic:** Draft briefing covering recent dynamics, next target milestone, and proposed session focus.
3. **Interactive Framing:** Present briefing in chat and confirm focus with user.
4. **Log Initialization:** Append active session block in project session journal with opening timestamp `[HH:mm]`. Log event in `_Arca-BrainOS/log.md`.
