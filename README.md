# PRD Reviewer

An automated Product Requirements Document (PRD) review and evaluation framework, based on Uber's First-Pass PRD Evaluator methodology.

## Overview

This framework provides structured, actionable PRD reviews across **6 core evaluation dimensions**:

| Dimension | Focus Area |
|-----------|------------|
| Opportunity & Assumptions | Problem clarity, assumption validation, success definition |
| Product Scope | Solution clarity, scope boundaries, decision-readiness |
| UX & Impact | User segments, edge cases, regional/accessibility considerations |
| Metrics & Data Rigor | Success metrics, guardrail metrics, measurement plan |
| Cross-Functional Impact | Cross-system impact, partner concerns, second-order effects |
| Decision Logic | Trade-offs, rationale, alternatives, risk mitigation |

## Features

- **4-tier review depth** — classifies PRD as Light / Medium / Full / Specialized Deep
- **7 anti-pattern detection** — catches unsupported assumptions, cross-system blind spots, unexamined second-order effects, and more
- **Structured output** — Launch readiness rating → dimension scorecard → detailed findings & fix suggestions → prioritized action items
- **Actionable feedback** — every finding comes with a concrete fix suggestion, not vague criticism

## Usage

2. Copy the repository link, and then use any AI tool to help you create a skill.
3. Trigger by saying: "Review this PRD",  "Evaluate this requirement"

### Manual / Framework Usage

The core evaluation framework is also available as standalone reference documentation. See [`references/prd-review-framework.md`](references/prd-review-framework.md) for the complete checklist, anti-pattern catalog, and output templates. You can use this directly for manual PRD review or integrate it into your own tooling.

```bash
# Clone for manual use or integration
git clone https://github.com/SermierSu/prd-reviewer.git
```

## Repository Structure

```
prd-reviewer/
├── SKILL.md                           # AI agent workflow instructions
├── references/
│   └── prd-review-framework.md        # Complete evaluation framework
├── README.md                          # This file
└── README.zh-CN.md                    # Chinese version
```

## Methodology

This framework is based on Uber's "First-Pass PRD Evaluator" methodology(https://www.uber.com/us/en/blog/first-pass-prd/), adapted for both automated AI-assisted review and manual evaluation. The goal is to make human review more focused and efficient, not to replace human judgment.

## License

MIT License — see [LICENSE](LICENSE) for details.
