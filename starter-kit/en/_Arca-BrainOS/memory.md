# 🧠 Operational Memory & Learned Preferences (Arca-BrainOS)

> 🛡️ **Anti-Pollution Guardrail (Frugal Golden Rule):**
> - This file stores the agent's short/medium-term operational memory.
> - **Strict Ceiling:** Must never exceed 40 to 50 lines total to prevent context bloat.
> - **Signal Threshold:** Only record a rule or preference that resulted from explicit user feedback or a structural decision.
> - **Periodic Pruning:** Outdated, temporary, or natively codified rules must be removed.

---

## ✍️ Stylistic & Editorial Preferences
- **No Em-Dashes:** Strict replacement of em-dashes with colons (`:`), commas (`,`), or parentheses `()`.
- **Natural Note Naming:** Concept notes, takeaways, or learning notes are saved with clear natural titles in `2-Ressources/Notes/[Title].md` (tag `note`, `learning`), without artificial prefixes.
- **Direct & Conciseness:** High signal density, focused on reducing mental fatigue.

---

## 🛠️ Technical Habits & Execution
- **Atomic POSIX Commands:** Prefer direct shell operations (`mv`, `cp`, `mkdir -p`) supported by native binaries (`agy`).
- **Folder Governance:** Never invent new root folders; strictly adhere to the 5 canonical PARA folders and `1-Projects/_Incubation/`.
- **Constitution Sanctity:** `AGENTS.md` is the Vault Constitution. Operational tweaks and habits belong here in `memory.md`, never in `AGENTS.md`.

---

## 💡 Recent Project Learnings (Active Buffer)
*(Dynamic section: holds 3 to 5 recent learnings from project archiving before consolidation)*
- [2026-09-06] **GTD Incubation:** Dormant projects and ideas are parked in `1-Projects/_Incubation/` with `status: someday` to protect active focus in `Home.md`.
EOF && \
cp _release-github-arca-brainos/starter-kit/en/_Arca-BrainOS/memory.md _release-github-arca-brainos/starter-kit/en/starter-vault/_Arca-BrainOS/memory.md
