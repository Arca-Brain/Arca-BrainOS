# 🛠️ Skill : arca-grill (Socratic Grilling & Architecture Stress-Testing)

- **Reference Process:** [[Process-Project-Management-and-Deep-Work]]

## Trigger
Execute this workflow when the user enters `arca-grill` (or `grill-me` / `brain-grill`), followed by the name, idea, or requirement for a new skill (or refactoring an existing skill) for Arca-BrainOS.

## Objective
Act as a rigorous engineering sparring-partner (adapted from Matt Pocock's *Grilling* methodology). The AI immediately halts all prompt or code writing to subject the proposal to a systematic Socratic grill, eliminating "vibe coding", preventing skill inflation, and safeguarding system invariants.

## Scope (Phase 1)
Strictly focused on **designing, refactoring, and evolving agentic skills (`Skill_arca-*.md`) of Arca-BrainOS**. General vault project extension is reserved for a future phase.

## 3 Methodological Pillars (Pocock)
1. **The Design Tree:** The problem is modeled as a decision tree where foundational choices govern sub-choices.
2. **The Frontier:** The set of decisions whose prerequisites are already settled. These are the only valid questions to ask *now*. Two interdependent questions never share the same round.
3. **Rounds:** Questioning progresses through sequential rounds. Rounds continue until the frontier is completely cleared (zero technical or ergonomic blind spots).

## Facts vs Decisions
- **Facts belong to the AI:** The AI inspects the vault itself (existing skills, topography, configs, MCP servers) instead of asking the user.
- **Decisions belong strictly to the Human:** The AI provides a strong reasoned recommendation for each question, but never decides in place of the user.

## Frontier Exploration Grid
To formulate questions for each round, the AI systematically explores these 5 critical axes:
1. **Legitimacy & Frugality:** Distinct new skill vs extending an existing skill? Concrete gain vs added complexity?
2. **Ingestion Vectors & Dependencies:** Input formats (Markdown files, stdin stream, MCP servers, transcripts)? Required tools?
3. **Vault Governance & Security:** Writing zones, human note preservation, guardrails (3 files maximum rule).
4. **Autonomy vs Human Supervision:** Pure automated steps (anti-chatter) vs mandatory chat checkpoints.
5. **Output Contract & Robustness:** Expected YAML frontmatter, file structure, error handling.

## Sequential Execution Workflow

### 1. Initial Analysis & Invariants Scan (ADR)
- Analyze user intent.
- **Scan Architectural Registry:** Systematically inspect `_Arca-BrainOS/adr/` (especially `adr/README.md` and active ADRs) to identify settled constraints (e.g. LLM sovereignty ADR-001, decoupled architecture ADR-002, human note sanctuarization ADR-005, frugal memory ADR-009). Any tension with an existing ADR becomes a priority frontier question in Round 1.
- Inspect facts in the environment (existing files, topography, MCP tools).
- **Absolute Rule:** Do not write any `.md` files or edit indexes yet. Remain in synchronous chat interview mode.

### 2. Rounds on the Decision Frontier
For each question round:
- Identify ready decisions (active frontier).
- Never include interdependent questions in the same round.
- Present in strict standardized format:

```markdown
❓ **Q1** - **<Decision Title>** : <Detailed context, stakes, and options>

➡️ <Reasoned AI recommendation with pragmatic justification>

---

❓ **Q2** - **<Decision Title>** : <Detailed context...>

➡️ <Reasoned AI recommendation>

---
```

This format allows fast user replies by number (e.g. `1: ok rec`, `2: option B`, `3: no because...`).

### 3. Frontier Evolution & Additional Rounds
- Process user answers and unlock downstream branches.
- Continue across rounds until all edge cases and ergonomic nuances are resolved.
- Never force premature closure: iterate until the frontier is empty.

### 4. Alignment Summary & Handoff
When the frontier is empty:
- Output an **Alignment Summary** summarizing settled decisions, rejected options, and interaction contract.
- Propose the operational pipeline:
  1. Record the architecture decision via `arca-adr` in `_Arca-BrainOS/adr/`.
  2. Implement the skill in `_Arca-BrainOS/skills/Skill_arca-[name].md`.
  3. Update `_Arca-BrainOS/skills/README.md` and `AGENTS.md`.

## Style & Guardrails
- Direct, incisive, professional, and constructive tone.
- **Absolute ban on em-dashes:** Replace with colons, commas, dots, or parentheses.
- **Zero premature side-effects:** No files created or modified before explicit alignment validation.
