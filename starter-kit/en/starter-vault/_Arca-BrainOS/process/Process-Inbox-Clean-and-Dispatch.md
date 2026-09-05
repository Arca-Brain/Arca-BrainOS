---
id: "202607172326"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - inbox
  - pkm
  - ai
---
# Process : Inbox Clean & Dispatch

- **Frequency** : Daily / Weekly
- **Trigger** : Accumulation of raw notes, voice transcripts, or web captures in `0-Inbox/`.

---

## Input
* Raw files in `0-Inbox/`.
* Theme MOCs (`T-`) in `2-Ressources/Themes/` and active projects (`P-`) in `1-Projects/`.

## Steps
1. **Launch AI Triage**: Invoke `arca-inbox-process` on `0-Inbox/`.
2. **Normalize YAML**: AI cleans frontmatter (`id`, `category`, `tags`, `status`).
3. **Detect Duplicates & Route**:
   - External source (video, article) ➔ Route to `arca-distill`.
   - Personal idea ➔ Invoke `arca-organize-idea` (Preserve Raw Note + Formulate Key Idea + Link to Project).
4. **Interactive Note Creation & Chaining**: Invoke `arca-create-note` (`create-project`, `create-theme`, `create-domaine`) with explicit human validation, automatic chaining of missing themes, and area justification scan.
5. **Validate Proposals**: User accepts or adjusts proposed project tasks and links.
6. **Move File**: Move completed note to permanent directory (`2-Ressources/Notes/` or `1-Projects/`).

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Fleeting Thought or Personal Idea
- **User Prompt:** `arca-inbox-process` (or: *"Triage my Inbox and structure my latest idea"*)
- **Initial State (`0-Inbox/`):** A raw note of a few unformatted lines.
- **Agentic Orchestration ([[Skill_arca-organize-idea]]):**
  1. Detects personal reflection vs external source.
  2. Preserves 100% of original text under `## 📝 Raw Note`.
  3. Distills a concise **Key Idea**.
  4. Extracts project actions (`P-`) and suggests MOC Theme links (`T-`).
  5. Normalizes YAML (`category: idea`, `tags`, `status: #reviewed`).
- **Final State (Output):** Moved to `2-Ressources/Notes/`, inbox back to zero.

### Case 2 : Web Article or External Source
- **User Prompt:** `arca-distill 0-Inbox/Web-Article.md`
- **Agentic Orchestration ([[Skill_arca-distill]]):**
  1. Creates conceptual synthesis `AI-Distil-[Name].md` in `2-Ressources/IA-generated/` ([[Skill_arca-synthesize]]).
  2. Anchors into Theme MOC (`T-`) via [[Skill_arca-converge]].
  3. Scans active projects for concrete action tasks via [[Skill_arca-impact]].
  4. Archives the raw source note.

### 🔗 Associated Agentic Skills
- [[Skill_arca-inbox-process]] : Triage, YAML cleaning, and routing.
- [[Skill_arca-organize-idea]] : Structuring raw ideas with text preservation.
- [[Skill_arca-distill]] : Master media ingestion & distillation pipeline.
- [[Skill_arca-create-note]] : Interactive instantiation of projects, themes, and areas.

