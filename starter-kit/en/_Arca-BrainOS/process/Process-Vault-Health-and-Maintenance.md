---
id: "202607172328"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - audit
  - pkm
  - maintenance
  - ai
---
# Process : Vault Health & Maintenance Audit

- **Frequency** : Monthly / Seasonal
- **Trigger** : Monthly maintenance schedule or navigation friction.

---
## Steps
1. **Run Diagnostic**: Execute `arca-audit`.
2. **Review Metrics**: Analyze PARA Health Index, Project ROI, orphan notes, and ghost links.
3. **Fix Friction**: Anchor orphans into Theme MOCs and fix broken links.
4. **Update Index**: Refresh `_Arca-BrainOS/index.md`.
5. **Archive Audit**: Record timestamped report into `_Arca-BrainOS/audit-log.md`.

## 💡 Concrete Examples & Prompt Templates

### Case 1 : Monthly Vault Health Audit
- **User Prompt:** `arca-audit`
- **Agentic Orchestration ([[Skill_arca-audit]]):** Computes PARA health ratio, consolidates project ROI metrics, detects orphan notes and ghost links, appends audit report to `_Arca-BrainOS/audit-log.md`.

### 🔗 Associated Agentic Skills
- [[Skill_arca-audit]], [[Skill_arca-converge]], [[Skill_arca-test-suite]].

