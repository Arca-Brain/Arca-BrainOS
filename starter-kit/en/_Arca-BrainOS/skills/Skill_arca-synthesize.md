# 🛠️ Skill : arca-synthesize (Synthesis & Distillation)

- **Reference Process:** [[Process-Media-Ingestion-and-Distillation]]

## Trigger
Invoked by user (`arca-synthesize [file]`) or automatically by `arca-distill`.

## Execution Workflow
1. **Analyze & Merge:** Analyze source and check for existing `AI-Distil-` note to merge.
2. **Draft Synthesis:** Write synthesis into `2-Ressources/IA-generated/AI-Distil-[Name].md`.
3. **Strict Frontmatter:** Enclose all text YAML values in double quotes `" "`. Set `status: "#new"`.

```yaml
---
date_created: "YYYY-MM-DD"
title: "Clear Title"
description: "One-sentence summary"
tags: [ai-generated, theme/...]
status: "#new"
---
```

## Structure
- **Synthetic Summary**
- **The Core:** Ideas, Beliefs, Models, Strategies
- **Application & Impact**
- **Suggested Connections**
- **Source History**
