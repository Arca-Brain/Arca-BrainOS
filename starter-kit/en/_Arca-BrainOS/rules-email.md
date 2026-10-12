# 📬 Business Rules & Triage Preferences: arca-email-process

> *This file serves as the specialized Sidecar Memory for the `arca-email-process` skill.*
> *It stores learned sender routing rules and triage preferences to automate future recommendations without cluttering `memory.md`.*

---

## 🗑️ Batch 1: Noise & Bulk Archiving (Customizable Examples)

These senders or email categories are automatically grouped into Batch 1 for immediate archiving out of the inbox (`removeLabelIds: ["INBOX", "UNREAD"]`) without creating notes in the vault:

- **Carsharing, mobility & rental alerts (`*@carsharing-service.com`, safety alerts, receipts):**
  - Action: Archive out of inbox and mark as read.
- **Bank statements & automated accounting (`*@my-bank.com`, monthly notices):**
  - Action: Archive out of inbox and mark as read.
- **Newsletters & marketing promotions (`*@newsletter-example.com`, promotional emails):**
  - Action: Always archive and mark as read.
- **E-commerce & routine delivery tracking (shipping confirmations):**
  - Action: Archive once notification is reviewed.

---

## 📚 Batch 2: Reference & Knowledge (Active Projects, Incubation & Areas)

These emails contain useful insights, documents, or contacts without immediate action:

- **Project Documentation & References:**
  - Technical summaries, specifications, or agreements directly relevant to an active project (`1-Projects/P-...`) or incubation project (`1-Projects/_Incubation/P-...`).
  - Action: Append under the project's documentation or resources section, then archive the email (`removeLabelIds: ["INBOX", "UNREAD"]`).
- **Cross-cutting Knowledge & MOCs:**
  - Deep-dive articles, benchmarks, or domain notes ➔ Link to a Theme (`2-Ressources/Themes/T-...`) or Life Area (`3-Domaines-de-vie/...`).

---

## 🎯 Batch 3: Next Actions & Commitments (GTD Focus)

These emails demand a concrete action, reply, or follow-up:

- **Tickets, bookings & refund vouchers (`*@transport-booking.com`, credit vouchers):**
  - Qualification: ⚡ Stand-alone action without project.
  - Routing: Append to `0-Inbox/Emails-Actions-Todo.md`.
  - Gmail Action: Star (`STARRED`) and mark as read.
- **Medical & administrative appointments (`office@medical-appointments.com`):**
  - Qualification: ⚡ Health / administrative stand-alone action.
  - Routing: Append to `0-Inbox/Emails-Actions-Todo.md`.
  - Gmail Action: Star (`STARRED`) and mark as read.
- **Club, association, or sports recurring activities:**
  - Qualification: ⚡ Stand-alone lifestyle action (e.g. workshop signup).
  - Routing: Append to `0-Inbox/Emails-Actions-Todo.md`.
  - Gmail Action: Star (`STARRED`) and mark as read.
- **Active Project Actions (`P-`):**
  - Whenever an email concerns a milestone or deliverable for an active project, propose direct injection into that `[[P-...]]`.

---

## 🧠 Incremental Learning Protocol
1. When encountering an unlisted recurring sender or a custom user preference during a run, the agent asks whether to store this rule here.
2. Upon user confirmation, the agent appends the rule under the appropriate section (Batch 1, Batch 2, or Batch 3) without modifying `memory.md`.
