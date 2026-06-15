---
name: prd-reviewer
description: "This skill should be used when a user provides a PRD (Product Requirement Document) for automated review and evaluation. It applies Uber's First-Pass PRD evaluation framework to assess PRD quality across 6 core dimensions, detect common anti-patterns, classify launch readiness, and generate structured, actionable feedback with prioritized action items. Trigger phrases include: 评审PRD, review this PRD, 帮我评审需求文档, PRD评审, review PRD document, 评估这个需求, 审查产品需求文档, or any request to evaluate/assess a product requirement document."
agent_created: true
---

# PRD Reviewer — 自动化 PRD 评审

## Purpose

Provide structured, actionable PRD reviews based on Uber's First-Pass PRD Evaluator methodology. The skill reads a PRD document, classifies its review depth, evaluates it across 6 core dimensions, detects anti-patterns, and outputs a comprehensive review with prioritized fixes.

## When to Use

Trigger this skill when:
- User provides a PRD document (text, markdown, or file) and asks for review/evaluation
- User uses phrases like "评审PRD", "review PRD", "帮我看看这个需求文档", "评估需求质量"
- User wants to know if a PRD is "review-ready" before sending to formal review
- User asks for feedback on product requirement document quality

## Workflow

### Step 1: Load the Review Framework

Before starting any review, load the detailed evaluation framework:

```
Read: references/prd-review-framework.md
```

This file contains the complete criteria, anti-patterns, and output templates. Keep it loaded as reference throughout the review process.

### Step 2: Read and Classify the PRD

Read the PRD document provided by the user (text, file, or URL). Classify it into one of four review depth tiers based on its content and scope:

| Tier | Applicable Scenarios |
|------|---------------------|
| 轻量审查 (Light) | UX consistency fixes, minor discoverability tweaks, copy changes |
| 中等审查 (Medium) | Incremental workflow changes, internal tool migrations, feature enhancements |
| 完整审查 (Full) | New capability launches, major feature additions |
| 专项深度审查 (Specialized Deep) | Policy changes, pricing/rule changes, platform rule changes, compliance |

If the PRD type is ambiguous, default to **完整审查 (Full)**. State the chosen tier at the beginning of the review.

### Step 3: Evaluate Each Dimension

For each of the 6 core dimensions, rate as "表现良好" or "需要优化" with specific evidence from the PRD:

1. **机会与假设** — Problem clarity, assumption validation, success definition
2. **产品范围** — Solution clarity, scope boundaries, decision-readiness
3. **用户体验与影响** — User segments, edge cases, regional/accessibility considerations
4. **指标与数据严谨性** — Success metrics, guardrail metrics, measurement plan
5. **关联影响与上下文** — Cross-system impact, partner concerns, second-order effects, historical references
6. **决策逻辑与优先级** — Trade-offs, rationale, alternatives, risk mitigation

Apply the review intensity matching the tier from Step 2. For Light review, focus primarily on Dimension 3 (UX & Impact). For Full review, deep-dive all dimensions.

### Step 4: Detect Anti-Patterns

Scan the PRD for the 7 documented anti-patterns from the framework. For each detected anti-pattern, provide:
- The specific anti-pattern name
- Evidence from the PRD that triggered the detection
- A concrete fix suggestion

### Step 5: Generate Structured Output

Output the complete review in Chinese using the exact format from the framework:

1. **上线就绪度评级** — One of: ✅ 就绪 / ⚠️ 有条件就绪 / ❌ 未就绪
2. **维度评分卡** — Table with dimension + rating + key finding for each
3. **详细发现与修复建议** — For each issue: problem description, impact, fix suggestion, supporting evidence
4. **行动项清单** — Organized as 🔴 关键必做项 / 🟡 优化建议项 / 🟢 参考建议项

At the end of the Critical Requirements section, always include the guidance line:
> **建议优先从这里开始修改**: [the single most impactful fix]

### Step 6: Deliver

Present the review as a clear, well-formatted message. If the PRD was provided as a file, offer to write the review back as a markdown file in the same directory.

## Important Rules

1. **Never skip dimensions** — even if a dimension seems irrelevant, briefly note its applicability (e.g., "该PRD不涉及多区域，本维度不适用")
2. **Always provide concrete fixes** — never give vague feedback like "improve metrics." Instead: "将'提升用户满意度'替换为'7日留存率从当前基线 X% 提升至 Y%，通过 A/B 实验验证，统计显著性 p<0.05'"
3. **Tie every finding to the framework** — reference which dimension and checklist item each finding relates to
4. **Respect review depth** — don't apply Full review intensity to a Light-tier PRD
5. **Be objective** — evaluate structural quality, not business viability. Don't pass judgment on whether the product idea is "good" — only on whether the PRD is well-constructed
6. **Default language is Chinese** — unless the PRD itself is purely in English, output the review in Chinese with Chinese headers
