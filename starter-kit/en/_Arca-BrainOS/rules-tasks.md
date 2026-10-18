# ✅ Business Rules & GTD Mapping: arca-task-process

> *This file serves as the specialized Sidecar Memory for the `arca-task-process` (`arca-todo`) skill.*
> *It stores the mapping between the Obsidian PARA ontology and the user's Todoist structure (Projects, Sections, Labels, Priorities) to automate future proposals without cluttering `memory.md`.*

---

## 🗺️ 1. Obsidian Domains ➔ Todoist Structure Mapping (Customizable Examples)

On first run, the agent automatically discovers your Todoist account hierarchy via the `get-overview` MCP tool and adapts these mappings to your own lists:

- **Todoist Inbox:** Mobile capture airlock to be clarified and emptied during Part 2.
- **Todo ❎ (or Next Actions):**
  - Section **Todo List**: Default primary target for stand-alone actions outside projects (administrative errands, health, registrations, finance, work).
  - Section **Someday / Maybe**: Ideas or wishes without a firm deadline.
- **Home 🏡 (or Personal Life):**
  - Sections: `Routines 🔁`, `2nd brain 🧠`, `Movies / Series 📽️`, `Books 📖`, `Travel 🚂`, `Read later 📖`.
- **Shopping 🛒 (or Errands):**
  - Sections: `Supermarket`, `Downtown`, `Gifts`, `Online Shopping`.
- **Make / DIY 🛠️:**
  - Sections: `Woodworking`, `Hardware Purchases`, `Home Improvement`.

---

## 🔄 2. Boundary Rules: Obsidian (`P-`) ⇄ Todoist

1. **Sanctuarizing Deep Work:**
   - Writing, architecture, coding, or research tasks belonging to active projects (`1-Projects/P-*.md`) are **never** automatically exported to Todoist.
   - If a task or thought captured on mobile inside the *Todoist Inbox* belongs to an Obsidian `P-` project, the agent proposes in Part 2 to **repatriate it into the corresponding `1-Projects/P-*.md` note** (or `0-Inbox/`) and complete it in Todoist.
2. **One-off External Errands Linked to a `P-` Project:**
   - When a task from a `P-` project requires an external or mobile action (phone call, mailing a letter, in-store purchase) and is pushed to Todoist, its Todoist description must include `[[P-Project-Name]]` and the `P-` note retains the `⏳ [Todoist]` marker until completion.
3. **Source Preservation in Todoist:**
   - Every action originating from `0-Inbox/Emails-Actions-Todo.md` carries its `(Source: ...)` provenance tag into the Todoist task `description` field before the staging buffer file is removed.

---

## ⚡ 3. Tool & Priority Conventions (`@doist/todoist-mcp`)

- **Priority format:** The `add-tasks` tool directly accepts strings `"p1"` (highest priority, red), `"p2"` (high, orange), `"p3"` (medium, blue), and `"p4"` (normal default, grey).
- **Rescheduling dates:** Always use the dedicated **`reschedule-tasks`** tool (and never `update-tasks`) when changing a task's due date so recurring schedules (`Routines 🔁`) are preserved.

---

## 🧠 Incremental Learning Protocol
1. Whenever the user adjusts a Todoist project/section mapping, priority, or scheduling habit while validating the Single Unified Dashboard, the agent asks whether to store the rule here.
2. No changes are made to this file without explicit user confirmation in chat.
