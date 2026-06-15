# PRD Review Framework

Based on Uber's First-Pass PRD Evaluator methodology. This reference defines the complete evaluation framework for automated PRD review.

---

## 1. Core Evaluation Dimensions (6 Dimensions)

For each PRD, evaluate across these 6 dimensions. Each dimension receives a rating of "表现良好" (Strong) or "需要优化" (Needs Improvement).

### Dimension 1: 机会与假设 (Opportunity & Assumptions)

**Checklist:**
- [ ] Is the problem statement clearly defined? Is it a real, validated problem?
- [ ] Are target users/personas explicitly identified?
- [ ] What assumptions underlie the opportunity? Are they validated or untested?
- [ ] Is the success definition clear, measurable, and verifiable?
- [ ] Are there any unsupported "headroom assumptions" (incremental projections without evidence)?
- [ ] Has the team validated whether this hypothesis has already been tested before?

**Red Flags:**
- Problem stated as a solution ("We need feature X" without explaining why)
- No evidence of user research or data backing the problem
- Assumptions presented as facts without qualification
- "If we build it, they will come" mentality without evidence

### Dimension 2: 产品范围 (Product Scope)

**Checklist:**
- [ ] Is the proposed solution easy to understand? Can a new team member follow it?
- [ ] Is the scope clearly bounded? What is explicitly IN and OUT of scope?
- [ ] Is the PRD at a "decision-ready" state — can reviewers make go/no-go decisions?
- [ ] Are dependencies on other teams/systems explicitly called out?
- [ ] Is the MVP vs. future iteration split clear?

**Red Flags:**
- Scope creep — trying to solve too many problems at once
- Vague boundaries ("we'll figure out the details later")
- Missing dependency analysis
- No clear MVP definition

### Dimension 3: 用户体验与影响 (User Experience & Impact)

**Checklist:**
- [ ] Is the experience designed for different user segments/cohorts?
- [ ] Is the experience designed for different regions/markets (if applicable)?
- [ ] Are edge cases covered? (empty states, error states, loading states, extreme inputs)
- [ ] Are accessibility considerations addressed?
- [ ] Is the user journey flow documented (happy path + sad paths)?

**Red Flags:**
- One-size-fits-all UX without segment consideration
- No edge case analysis
- Missing error/empty/loading state designs
- Ignoring regional differences when the product is multi-market

### Dimension 4: 指标与数据严谨性 (Metrics & Data Rigor)

**Checklist:**
- [ ] Are success metrics (North Star / primary KPI) clearly defined?
- [ ] Are guardrail metrics defined? (metrics that must NOT degrade)
- [ ] Is there a credible measurement/validation plan?
- [ ] Are metric definitions specific (formula, data source, aggregation method)?
- [ ] Is there a plan for A/B testing or phased rollout with success criteria?

**Red Flags:**
- Vague metrics ("improve user satisfaction")
- No guardrail metrics
- No measurement methodology
- Metrics that can't be measured with existing instrumentation

### Dimension 5: 关联影响与上下文 (Cross-Functional Impact & Context)

**Checklist:**
- [ ] Are impacts on related systems/features documented?
- [ ] Have partner team concerns been incorporated?
- [ ] Are historical experiment results referenced where relevant?
- [ ] Are hidden dependencies surfaced?
- [ ] Are second-order effects considered? (What happens after this ships?)
- [ ] Would a senior reviewer's likely questions be pre-addressed?

**Red Flags:**
- Blind spots — no mention of related systems
- Re-exploring previously tested hypotheses without referencing past results
- Missing second-order effect analysis
- No cross-team alignment documented

### Dimension 6: 决策逻辑与优先级 (Decision Logic & Prioritization)

**Checklist:**
- [ ] Are trade-off decisions documented with rationale?
- [ ] Is there a clear prioritization framework for what ships first?
- [ ] Are alternatives considered and rejected with reasoning?
- [ ] Is the "why" behind key decisions clear, not just the "what"?
- [ ] Are risks documented with mitigation plans?

**Red Flags:**
- All items marked as "P0 / critical" — no real prioritization
- Decisions stated without rationale
- No alternatives considered section
- Well-written prose but lacking decision framework

---

## 2. Review Depth Classification

Before reviewing, classify the PRD into one of these tiers to determine review intensity:

| Tier | Applicable Scenarios | Review Intensity |
|------|---------------------|------------------|
| **轻量审查 (Light)** | UX consistency fixes, discoverability improvements, minor copy changes | Focus on UX & Impact (Dim 3) only; skip deep cross-functional analysis |
| **中等审查 (Medium)** | Incremental workflow changes, internal tool migrations, feature enhancements | Cover all 6 dimensions but with lighter scrutiny on cross-functional impact |
| **完整审查 (Full)** | New capability launches, major feature additions | Full deep-dive on all 6 dimensions |
| **专项深度审查 (Specialized Deep)** | Policy changes, pricing rule changes, platform rule changes, compliance updates | Full review + extra scrutiny on Dimension 5 (Cross-functional) and regulatory/compliance aspects |

If PRD type is unclear, default to **完整审查 (Full)**.

---

## 3. Anti-Pattern Detection

Actively scan the PRD for these common failure patterns:

| Anti-Pattern | Detection Signal | Fix Suggestion |
|-------------|-----------------|----------------|
| 无支撑的增量假设 (Unsupported Headroom Assumption) | Growth projections without baseline data or methodology | Provide baseline data, methodology, and conservative/best-case ranges |
| 系统影响盲区 (Cross-System Blind Spot) | No mention of upstream/downstream system impacts | Map all touchpoints: data flows, API calls, UI overlaps, notification triggers |
| 未检验的二阶效应 (Unexamined Second-Order Effects) | Only primary outcomes considered; no "what then?" analysis | Add second-order analysis: user behavior changes, system load shifts, team maintenance burden |
| 政策兜底缺失 (Missing Policy Guardrails) | Policy/rule changes without fallback mechanisms | Define rollback criteria, monitoring thresholds, escalation paths |
| 重复造轮子 (Reinventing the Wheel) | Exploring hypotheses already tested by the team | Search and reference past experiments, documents, and oral knowledge |
| 文笔优美但空心 (Well-Written but Hollow) | Fluent prose but missing context, framework, or decision logic | Add decision rationale, alternatives considered, data backing claims |
| 无优先级区分 (No Priority Differentiation) | Every item marked as critical/P0 | Force-rank items; distinguish "must have for launch" vs "nice to have post-launch" |

---

## 4. Output Format

Every PRD review MUST produce the following structured output in Chinese:

### 4.1 上线就绪度评级 (Launch Readiness Rating)

| Rating | Criteria |
|--------|----------|
| ✅ 就绪 (Ready) | No critical gaps; all dimensions rated "表现良好" |
| ⚠️ 有条件就绪 (Conditionally Ready) | Minor gaps in 1-2 non-critical dimensions; can proceed with documented follow-ups |
| ❌ 未就绪 (Not Ready) | Critical gaps in any dimension; significant rework needed before review |

### 4.2 维度评分卡 (Dimension Scorecard)

Table format with each dimension rated:

```
| 维度 | 评级 | 关键发现 |
|------|------|----------|
| 机会与假设 | 表现良好 / 需要优化 | 1-2 sentence summary |
| 产品范围 | ... | ... |
| 用户体验与影响 | ... | ... |
| 指标与数据严谨性 | ... | ... |
| 关联影响与上下文 | ... | ... |
| 决策逻辑与优先级 | ... | ... |
```

### 4.3 详细发现与修复建议 (Detailed Findings & Fix Suggestions)

For each issue found, provide:
1. **问题描述**: What is missing or insufficient (be specific)
2. **影响**: Why this matters for the PRD quality
3. **修复建议**: Actionable replacement text or concrete next steps the PM can take
4. **证据支撑**: Reference related documents, historical experiments, or industry standards where applicable

### 4.4 行动项清单 (Action Items)

Organized by priority:

**🔴 关键必做项 (Critical Requirements)** — Must resolve before PRD can proceed to formal review

**🟡 优化建议项 (Optimizations)** — Should address to improve quality, but not blocking

**🟢 参考建议项 (Nice-to-Have)** — Optional improvements

At the end of the Critical Requirements section, explicitly call out:
> **建议优先从这里开始修改**: [the single most impactful change to make first]

---

## 5. Guiding Principles

When conducting reviews, follow these principles:

1. **框架优先于通用批评**: Don't give generic feedback. Tie every finding to a specific dimension and standard.
2. **上下文与文笔同等重要**: A well-written PRD can still be hollow. Look beyond prose quality to substance.
3. **明确边界确保客观**: Apply clear defect standards. Don't pass a PRD that's missing fundamental content.
4. **优先级是产物的一部分**: The most valuable output is telling the PM what to fix FIRST, not listing everything wrong.
5. **AI评审服务于人类对话**: The goal is to make subsequent human review more focused and efficient, not to replace human judgment.

---

## 6. Known Limitations

- This framework evaluates PRD structural quality and completeness, not the business validity of the product idea itself
- Domain-specific nuances (e.g., hardware products, regulated industries) may require additional criteria beyond this framework
- The review is a supplement to, not a replacement for, human expert review
- Senior leadership judgment and domain expert decisions remain authoritative
