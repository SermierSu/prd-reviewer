# PRD Reviewer — WorkBuddy Skill

A WorkBuddy skill for automated Product Requirements Document (PRD) review and evaluation, based on Uber's First-Pass PRD Evaluator methodology.

## Overview

This skill provides structured, actionable PRD reviews across **6 core evaluation dimensions**:

| Dimension | Focus Area |
|-----------|------------|
| 机会与假设 (Opportunity & Assumptions) | Problem clarity, assumption validation, success definition |
| 产品范围 (Product Scope) | Solution clarity, scope boundaries, decision-readiness |
| 用户体验与影响 (UX & Impact) | User segments, edge cases, regional/accessibility considerations |
| 指标与数据严谨性 (Metrics & Data Rigor) | Success metrics, guardrail metrics, measurement plan |
| 关联影响与上下文 (Cross-Functional Impact) | Cross-system impact, partner concerns, second-order effects |
| 决策逻辑与优先级 (Decision Logic) | Trade-offs, rationale, alternatives, risk mitigation |

## Features

- **4-tier review depth** — automatically classifies PRD as Light / Medium / Full / Specialized Deep
- **7 anti-pattern detection** — catches unsupported assumptions, cross-system blind spots, unexamined second-order effects, and more
- **Structured output** — Launch readiness rating → dimension scorecard → detailed findings & fix suggestions → prioritized action items
- **Actionable feedback** — every finding comes with a concrete fix suggestion, not vague criticism

## Installation

### Option 1: Install from zip (WorkBuddy Desktop)

1. Download `prd-reviewer.zip` from the [Releases](../../releases) page
2. Open WorkBuddy → Settings → Skills
3. Click "Import Skill" and select the zip file

### Option 2: Manual install

```bash
# Clone into WorkBuddy skills directory
git clone https://github.com/SermierSu/prd-reviewer.git ~/.workbuddy/skills/prd-reviewer
```

Restart WorkBuddy and the skill will be automatically loaded.

## Usage

Once installed, trigger the skill by saying:

- "评审这个PRD"
- "帮我评审需求文档"
- "review this PRD"
- "评估这个需求"

Then paste or upload your PRD document. The skill will:

1. Classify the PRD review depth
2. Evaluate across all 6 dimensions
3. Detect common anti-patterns
4. Output a structured review with prioritized action items

## Skill Structure

```
prd-reviewer/
├── SKILL.md                           # Core workflow instructions
└── references/
    └── prd-review-framework.md        # Complete evaluation framework
```

## Methodology

This skill is based on Uber's "First-Pass PRD Evaluator" framework, adapted for automated AI-assisted review. The goal is to make human review more focused and efficient, not to replace human judgment.

## License

MIT License — see [LICENSE](LICENSE) for details.

## Related

- [prd-writer](https://github.com/SermierSu/prd-writer) — The companion skill for writing PRDs using the 8-section template
