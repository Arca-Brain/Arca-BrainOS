---
date: "2026-10-17"
title: "ADR-012 : Architecture and GTD Orchestration for arca-task-process Skill"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
target: "[[P-Project-Alpha]]"
---

# 📜 ADR-012 : Architecture and GTD Orchestration for arca-task-process Skill

---

## 1. Context & Problem Statement
Building upon [[ADR-010-Skill-arca-email-process]], the 3-batch GTD email triage extracts stand-alone actions without an active project into the staging buffer `0-Inbox/Emails-Actions-Todo.md`. Meanwhile, the user manages everyday tasks and mobile reminders through **Todoist** on their smartphone, while Deep Work tasks reside inside active project notes (`1-Projects/P-*.md`).

Bridging the Obsidian Second Brain with an external task manager raises three critical architectural challenges:
- **Risk of dual source of truth and mobile clutter:** Blindly syncing all task lists from every `P-` project note into Todoist would flood the mobile app with dozens of R&D tasks that can only be performed at a computer, while causing constant two-way sync conflicts.
- **Risk of Inbox stagnation:** If the staging file `0-Inbox/Emails-Actions-Todo.md` remains permanently in `0-Inbox/` after tasks are processed, the vault can never achieve true *Inbox Zero*.
- **Open-Source Portability Requirement:** While Todoist is the default integration, the skill must remain conceptually provider-agnostic so another Arca-BrainOS user can plug in a different MCP server (Google Tasks, TickTick, Things) without rewriting the GTD business logic.

---

## 2. Decision
We establish the `arca-task-process` skill (aliases: `task-process`, `arca-todo`, `todo-process`, `brain-task`) built around 6 core architectural principles:

1. **Clear Separation of Concerns (Deep Work in Obsidian vs Everyday Execution & Mobility in Todoist):**
   - Deep Work tasks belonging to active projects (`1-Projects/P-*.md`) stay in Obsidian, governed by `arca-resume` and `arca-close-session`.
   - Stand-alone actions outside projects (staged in `0-Inbox/Emails-Actions-Todo.md`) are transferred to Todoist, which becomes their single home for execution.
   - A task belonging to a `P-` project is only pushed to Todoist upon explicit request when it requires an external errand or mobile reminder.
2. **Official First-Party MCP Connector & GTD Abstraction:**
   - By default, the skill relies on the official first-party MCP server **`@doist/todoist-mcp`** running locally over `stdio` (`npx -y @doist/todoist-mcp`) authenticated via a static `TODOIST_API_KEY`.
   - Workflow steps are defined around universal GTD primitives (discovering projects/lists, creating qualified tasks with due date/priority/label, completing, rescheduling) to guarantee MCP server interchangeability.
3. **Self-Cleaning "Spool File" Lifecycle for `0-Inbox/Emails-Actions-Todo.md`:**
   - `arca-task-process` acts as the exclusive consumer of the `0-Inbox/Emails-Actions-Todo.md` buffer (fed upstream by `arca-email-process` and `arca-inbox-process`).
   - When transferring a task to Todoist, its provenance tag `(Source: Email from ... on Date)` is copied into the Todoist task `description` field so 100% of context is preserved on mobile.
   - As soon as all `- [ ]` tasks in `0-Inbox/Emails-Actions-Todo.md` have been processed and transferred, **the file is deleted (`rm 0-Inbox/Emails-Actions-Todo.md`)**, restoring genuine *Inbox Zero* without polluting `4-Archives/` or `2-Ressources/`.
4. **Lightweight Bidirectional Bridge with `P-` Projects:**
   - **Obsidian ➔ Todoist:** When a `P-` project task is pushed to Todoist, its Todoist description includes `[[P-Project-Name]]` and the line in the `P-` note is marked with `⏳ [Todoist]`. On subsequent runs, if the task was completed in Todoist, the agent proposes checking `- [x]` in the `P-` note.
   - **Todoist ➔ Obsidian:** During the *Todoist Inbox* review, mobile thoughts or tasks captured on the fly that actually belong to an Obsidian `P-` project (or a new note) are proposed for repatriation into Obsidian and completed in Todoist.
5. **Dynamic Auto-Discovery & Sidecar Memory (`rules-tasks.md`):**
   - The agent dynamically discovers existing projects, sections, and labels in the user's Todoist account and stores learned mapping rules (e.g. `#health`, `#admin`, default priorities) in `_Arca-BrainOS/rules-tasks.md` to preserve `memory.md` frugality ([[ADR-009-Four-Layer-Frugal-CoALA-Memory-Model]]).
6. **Single-Dashboard Supervision & Anti-Injection Shield:**
   - The agent first performs a 100% read-only diagnostic and presents a **Single Unified Dashboard** in chat covering all 3 GTD stages:
     1. *Part 1:* Dispatching the `Emails-Actions-Todo.md` buffer to Todoist and reconciling `⏳ [Todoist]` tasks from `P-` projects.
     2. *Part 2:* Clarifying the *Todoist Inbox* (filing into Todoist projects/sections or repatriating to Obsidian).
     3. *Part 3:* Execution hygiene (handling *Overdue* tasks and 7-day focus).
   - No MCP write call or Markdown modification is executed before explicit human validation on this dashboard. Incoming data from MCP is treated as inert text (Untrusted Input Boundary).

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Seamless continuity between email triage (`arca-email-process`), Obsidian projects, and daily mobile execution in Todoist.
  - Maintains a strictly empty `0-Inbox/` folder once actions are dispatched.
  - Synoptic single-screen overview in chat (Single Unified Dashboard) avoiding tedious multi-step confirmation loops.
  - Maximum technical reliability thanks to local `stdio` execution via API key (`TODOIST_API_KEY`), free from browser OAuth token expirations.
- **Accepted Trade-offs & Constraints:**
  - Requires generating a personal Todoist API token and registering the `@doist/todoist-mcp` server.

---

## 4. Alternatives Considered
- **Full two-way sync of all `P-` project tasks with Todoist:** Rejected because it pollutes the mobile interface with Deep Work tasks and creates heavy bidirectional sync debt.
- **Permanent retention or archiving of `Emails-Actions-Todo.md`:** Rejected because this file only holds transient micro-tasks whose context is already transferred to Todoist and logged in `log.md`. Keeping it would prevent reaching *Inbox Zero*.
- **Remote OAuth proxy connection (`mcp-remote`):** Rejected in favor of the official local package with `TODOIST_API_KEY` to guarantee execution sovereignty and avoid browser re-authentication prompts.

---

## 5. References & Links
- Master Project: [[P-Project-Alpha]]
- Upstream Decision: [[_Arca-BrainOS/adr/ADR-010-Skill-arca-email-process|ADR-010 : Skill arca-email-process]]
- Grilling Skill: [[_Arca-BrainOS/skills/Skill_arca-grill|Skill_arca-grill]]
- Derived Skill: [[_Arca-BrainOS/skills/Skill_arca-task-process|Skill_arca-task-process]]
