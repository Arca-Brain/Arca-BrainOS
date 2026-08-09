# ⚙️ Process : Agentic Testing & Quality Evaluation (Arca Test Suite)

## Metadata
- **ID :** `Process-Agentic-Testing-and-Evaluation`
- **Title :** Non-Regression & Agentic Quality Protocol
- **Status :** `🟢 Active`
- **Frequency :** Upon skill refactoring, prompt updates, or LLM model upgrades.

---
## Steps
1. **Launch**: Run `arca-test` or `arca-test-suite`.
2. **Isolated Execution**: Agent runs 13 assertions on `_Arca-BrainOS/tests/fixtures/`.
3. **Report**: Agent outputs PASS/FAIL Flash Report in chat (Target: 13/13 PASS).
