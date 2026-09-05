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

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Non-Regression Test Harness
- **User Prompt:** `arca-test` (or `arca-test-suite`)
- **Agentic Orchestration ([[Skill_arca-test-suite]]):** Executes automated assertions on fixture notes, reports pass/fail score (target: 12/12 PASS).

### 🔗 Associated Agentic Skills
- [[Skill_arca-test-suite]].

