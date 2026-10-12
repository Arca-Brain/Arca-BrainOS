---
date: "2026-09-12"
title: "ADR-010 : Architecture and Ingestion Gateway for arca-email-process Skill"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
target: "[[P-Project-Alpha]]"
---

# 📜 ADR-010 : Architecture and Ingestion Gateway for arca-email-process Skill

---

## 1. Context & Problem Statement
Daily handling of personal and professional emails represents a primary source of cognitive fragmentation. User and beta-tester feedback highlighted the high value of bridging email inboxes with the Obsidian Second Brain.

However, connecting an AI agent directly to an inbox introduces critical architectural risks:
- **Vault Bloat Risk:** Storing entire raw email bodies pollutes the vault, slows Git history, and dilutes semantic vector search (RAG).
- **Destructive Deletion Risk:** Blind automated archiving or deletion by an AI agent risks losing essential communications.
- **Vendor Lock-in Risk:** Requiring proprietary email label hierarchies or exclusive tools breaks system portability.

---

## 2. Decision
The `arca-email-process` skill is designed around the following principles:

1. **Non-Intrusive Value Extraction:** The exclusive purpose of the skill in the vault is extracting actionable tasks, follow-ups, and concise summaries. Zero raw email bodies are retained in Obsidian.
2. **Resilient Hybrid Ingestion:** Priority given to `google-workspace` MCP server (recommended), with graceful fallback to local directory `0-Inbox/Emails/` for non-MCP users.
3. **Direct Project Routing and Daily Triage Note:**
   - Clear project tasks are injected directly into active project notes (`1-Projects/P-...`) with traceable provenance: `- [ ] [Task] (Source: [Email from Sender](URL_or_ID) on Date)`.
   - Orphan actions and references without an active project are grouped in a single daily note `0-Inbox/Triage-Emails-YYYY-MM-DD.md`.
4. **Universal Native Gmail Actions:**
   - No custom label hierarchy required.
   - Processed noise is archived out of inbox and marked read.
   - Actionable emails are starred and marked read while remaining visible in the inbox.
5. **Mandatory Human Supervision:** Strict two-step execution. The AI presents an alignment table and halts until explicit user approval (`ok`).
6. **Volume Cap & Frugality:** Standard query on `in:inbox -is:starred`. Batches capped at the top 10 most recent if total exceeds 25 emails.
7. **Anti-Loop Filter & Sidecar Memory (`rules-email.md`):**
   - Excluding `-is:starred` prevents reprocessing active flagged tasks on recurring runs.
   - To preserve `memory.md` frugality (< 50 lines per ADR-009), sender-specific routing preferences reside in a specialized sidecar file: `_Arca-BrainOS/rules-email.md`.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Significant cognitive relief with zero risk of information loss.
  - Clean vault hygiene without ephemeral markdown garbage.
  - Zero required prior Gmail label setup.
- **Accepted Trade-offs & Constraints:**
  - Two-step supervision requires user presence during execution.
  - Non-MCP fallback requires manual file deposit in `0-Inbox/Emails/`.

---

## 4. Alternatives Considered
- **Archiving full email bodies as single notes:** Rejected because it turns Obsidian into an email mirror and degrades vector search.
- **Unsupervised autonomous Inbox Zero:** Rejected due to obvious security and liability risks.

---

## 5. References & Links
- Master Project: [[P-Project-Alpha]]
- Curation Note: [[2-Ressources/Notes/e-mail batch|e-mail batch.md]]
- Grilling Skill: [[_Arca-BrainOS/skills/Skill_arca-grill|Skill_arca-grill]]
- Derived Skill: [[_Arca-BrainOS/skills/Skill_arca-email-process|Skill_arca-email-process]]

---

## 6. Addendum v2: 3-Batch GTD Pipeline, Action Buffer & Cybersecurity Shield (2026-10-12)

Following user feedback on real-world email volumes (> 20 emails), the architecture of `arca-email-process` has been updated with significant robustness enhancements:

### 6.1. Transition from Monolithic Table to 3 Sequential GTD Batches
The previous 7-column table created cognitive friction when handling large inboxes. Triage now operates in 3 distinct waves:
1. **Batch 1 (Noise & Bulk Archiving):** Groups 70 to 80% of volume (newsletters, receipts, notifications). Validated in bulk with a single response (`ok archive`).
2. **Batch 2 (Reference & Knowledge):** Retains actionable insights and technical documents without immediate tasks. Routes to active projects (`1-Projects/`), incubation projects (`1-Projects/_Incubation/`), or Themes and Life Areas.
3. **Batch 3 (Next Actions & Commitments):** Concentrated focus on genuine action items (typically 3 to 8 emails).

### 6.2. Action Routing: Direct Project Injection vs Idempotent Central Buffer
- **Actions linked to an Active Project (`P-`):** Injected directly into the project's task list.
- **Stand-alone actions without project:** Centralized in a single persistent file in the inbox: **`0-Inbox/Emails-Actions-Todo.md`**, structured by timestamped sections (`### 📅 Triage: YYYY-MM-DD [HH:mm]`). The agent runs an idempotence scan across all prior sections to prevent duplicate tasks. This file acts as a staging queue for external task integration skills (e.g. Todoist MCP).

### 6.3. Strict Google Workspace MCP Prerequisite
To eliminate unnecessary complexity and code divergence, the skill formally relies on the `google-workspace` MCP server as a strict prerequisite.

### 6.4. Cybersecurity Shield (Indirect Prompt Injection)
To protect against prompt injection attacks via external emails:
- **Untrusted Input Boundary:** Email content is strictly parsed as inert data, forbidding any execution as agent instructions.
- **Detection & Alerts:** Suspicious prompt injection patterns trigger immediate security warnings in chat and neutralize action extraction.
- **Output Sanitization & Air-Gap:** Stripping of executable commands, combined with mandatory human verification before any vault write or Gmail API call.
