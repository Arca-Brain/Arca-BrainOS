# 🛠️ Skill : arca-email-process (GTD Email Triage & Action Extraction)

- **Reference Process:** [[Process-Inbox-Clean-and-Dispatch]]
- **Reference Architecture Decision:** [[ADR-010-Skill-arca-email-process]]

## Trigger
Execute this workflow when the user enters `arca-email-process` (or `email-process` / `brain-email`), optionally followed by a limit count or specific search query (e.g. `arca-email-process 5`, `arca-email-process "from:director"`).

## Objective
Analyze incoming email flow, surgically extract tasks, follow-ups, and key knowledge into Obsidian without storing raw email bodies, then apply supervised and reversible Gmail labeling or archiving.

## Prerequisites & Hybrid Ingestion Vector
1. **Preferred Vector (Recommended):** Active `google-workspace` MCP server (`search_emails`, `get_email`, `modify_email_labels`).
2. **Fallback Vector (Local):** If MCP is not configured, the skill scans local folder `0-Inbox/Emails/` to process manually dropped `.eml` or `.md` files.

## Sequential Execution Workflow

### 1. Ingestion, Frugality & Sidecar Memory
- **Specialized Sidecar Memory:** Always load rules from `_Arca-BrainOS/skills/rules-email.md` to apply learned sender preferences.
- **Default Query (Anti-Loop Filter):** Target `in:inbox -is:starred` (read or unread, but **strictly excluding already starred emails** to avoid re-processing ongoing actions).
- **Volume Guardrail:**
  - If the Inbox contains more than 25 unhandled emails, restrict analysis to the **top 10 most recent batch**.
  - Display progress count: *"XX unhandled emails in inbox. Processing top batch (10 most recent)..."*
- **User Override:** If arguments are provided (e.g. `20` or `"from:partner"`), apply the query directly.

### 2. Analysis & GTD Qualification Grid
For each email, the AI consults `rules-email.md` first, then qualifies into 4 categories:
1. **⚡ Project Action:** Clear task linked to an existing active project `P-`.
2. **⏳ Waiting / Follow-up:** Delegated task, pending validation or external reply.
3. **📚 Information & Reference:** Useful data or insight without immediate action, mapped to a Life Area (`3-Domaines-de-vie/`) or Theme (`T-`).
4. **🗑️ Noise / Archive:** Notification, receipt, newsletter, or concluded exchange without residual cognitive value.

### 3. Mandatory Human Supervision (Checkpoint)
The AI immediately suspends vault writes and Gmail operations. It presents a complete alignment table in chat:

```markdown
| # | Sender | Subject | GTD Category | Extracted Task / Summary | Vault Destination | Planned Gmail Action |
|---|--------|---------|--------------|--------------------------|-------------------|----------------------|
| 1 | Name   | Topic   | Project Act. | Draft meeting minutes    | [[P-Project-X]]   | Star + Read          |
| 2 | Name   | Topic   | Noise        | None                     | None (ignored)    | Archive + Read       |
```

- **Absolute Rule:** The AI waits for explicit user confirmation (`ok` or adjustments on specific items) before proceeding.

### 4. Vault Routing & Execution
Upon confirmation:
- **Case A: Actions with identified Active Project (`P-`):**
  - Open project note `1-Projects/[P-Name].md`.
  - Append task under `## 🎯 Objectives & Tasks`:
    `- [ ] <Task description> (Source: [Email from Sender](Link_or_ID) on Date)`
  - *Human style rule:* Never modify or delete pre-existing user tasks.
- **Case B: Orphan Actions, Follow-ups, or Reference (No Active Project):**
  - Create a single summary note `0-Inbox/Triage-Emails-YYYY-MM-DD.md`.
  - Use standard metadata and structure sections:
    - `## 🎯 Immediate Actions (Without Project)`
    - `## ⏳ Waiting For & Delegated Follow-ups`
    - `## 📚 Reference & Notable Contacts`

### 5. Gmail Messaging Actions & Cleanup
- **Via `google-workspace` MCP:**
  - Noise / Processed Info: `removeLabelIds: ["INBOX", "UNREAD"]` (Archive and mark read).
  - Actions / Waiting: `removeLabelIds: ["UNREAD"]` and `addLabelIds: ["STARRED"]` (Star for tracking, kept in inbox).
- **Local Fallback Mode:**
  - Delete processed files from `0-Inbox/Emails/` after user consent.

### 6. Closure & Logging
Log a single line in `_Arca-BrainOS/log.md`:
`[YYYY-MM-DD HH:mm] - AI Action (Email) : Triaged [N] emails ([X] tasks injected into projects, [Y] archived)`

## Style & Guardrails
- Zero em-dashes in all generated or edited files: use colons, commas, dots, or parentheses.
- Zero destructive actions or label modifications without prior chat confirmation.
