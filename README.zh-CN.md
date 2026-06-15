# PRD Reviewer

一个基于 Uber First-Pass PRD Evaluator 方法论的自动化产品需求文档（PRD）评审与评估框架。

## 概述

本框架围绕 **6 大核心评审维度** 提供结构化、可操作的 PRD 评审：

| 维度 | 关注重点 |
|------|---------|
| 机会与假设 | 问题清晰度、假设验证、成功定义 |
| 产品范围 | 方案清晰度、范围边界、决策就绪度 |
| 用户体验与影响 | 用户群体、边界情况、区域/无障碍考虑 |
| 指标与数据严谨性 | 成功指标、护栏指标、测量方案 |
| 关联影响与上下文 | 跨系统影响、协作方顾虑、二阶效应 |
| 决策逻辑与优先级 | 权衡取舍、决策依据、备选方案、风险缓解 |

## 功能特性

- **4 级评审深度** — 将 PRD 分类为轻量 / 中等 / 完整 / 专项深度
- **7 种反模式检测** — 发现无支撑假设、系统影响盲区、未检验的二阶效应等常见问题
- **结构化输出** — 上线就绪度评级 → 维度评分卡 → 详细发现与修复建议 → 优先级排序的行动项
- **可操作反馈** — 每条发现都附带具体修复建议，而非泛泛批评

## 使用方式

1. 复制仓库链接，然后使用任意AI工具让它帮你创建这个skill
2. 通过以下话术触发："评审这个PRD"、"review this PRD"、"评估这个需求"

### 手动使用 / 框架参考

核心评审框架也可作为独立参考文档直接使用。详见 [`references/prd-review-framework.md`](references/prd-review-framework.md)，内含完整的检查清单、反模式目录和输出模板。你可以直接用于人工 PRD 评审，或集成到自己的工具中。

```bash
# 克隆后手动使用或集成
git clone https://github.com/SermierSu/prd-reviewer.git
```

## 仓库结构

```
prd-reviewer/
├── SKILL.md                           # AI 智能体工作流指令
├── references/
│   └── prd-review-framework.md        # 完整评审框架
├── README.md                          # 英文版说明
└── README.zh-CN.md                    # 本文件
```

## 方法论

本框架基于 Uber 的 "First-Pass PRD Evaluator" 方法论（https://www.uber.com/us/en/blog/first-pass-prd/），同时适配了自动化 AI 辅助评审和人工评审两种场景。目标是让后续的人工评审更加聚焦和高效，而非取代人类判断。

## 许可证

MIT 许可证 — 详见 [LICENSE](LICENSE)。

