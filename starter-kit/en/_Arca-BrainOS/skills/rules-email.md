# 📬 Business Rules & Triage Preferences: arca-email-process

> *This file serves as the specialized Sidecar Memory for the `arca-email-process` skill.*
> *It stores learned sender routing rules and triage preferences to automate future recommendations without cluttering `memory.md`.*

---

## 👤 Sender Rules & Routing Preferences (Customizable Examples)

- **Banking & Administrative Statements (`*@my-bank.com`, statement notices):**
  - GTD Category: 📚 Administrative Information.
  - Vault Action: Do not create single notes (unless explicitly requested).
  - Gmail Action: Archive out of inbox and mark read (`removeLabelIds: ["INBOX", "UNREAD"]`).

- **Travel Tickets, Bookings & Vouchers (`*@airline.com`, train delays, receipts):**
  - GTD Category: 🎫 Booking / Voucher Follow-up.
  - Vault Action: Record reference and date in summary note `0-Inbox/Triage-Emails-YYYY-MM-DD.md` linked to Area `[[Travel]]` or `[[Personal]]`.
  - Gmail Action: Keep in inbox with Star (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

- **Healthcare & Appointments (`*@doctor.com`, reminder notices):**
  - GTD Category: ⚡ Health Action.
  - Vault Action: Record in summary note `0-Inbox/Triage-Emails-YYYY-MM-DD.md` linked to Area `[[Health]]`.
  - Gmail Action: Keep in inbox with Star (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

- **Executive & Project Stakeholders (`lead@company.com`, strategic milestones):**
  - GTD Category: ⚡ Project Action.
  - Vault Action: Inject task directly into the active project note (`1-Projects/P-...`).
  - Gmail Action: Keep in inbox with Star (`addLabelIds: ["STARRED"]`, `removeLabelIds: ["UNREAD"]`).

---

## 🛡️ General Filtering Rules
- **Newsletters, Promos & Commercial Noise:** Always archive out of inbox and mark as read (`removeLabelIds: ["INBOX", "UNREAD"]`).
