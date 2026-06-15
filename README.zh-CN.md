# PRD Reviewer — WorkBuddy 技能

一个基于 Uber First-Pass PRD Evaluator 方法论的自动化产品需求文档（PRD）评审 WorkBuddy 技能。

## 概述

本技能围绕 **6 大核心评审维度** 提供结构化、可操作的 PRD 评审：

| 维度 | 关注重点 |
|------|---------|
| 机会与假设 | 问题清晰度、假设验证、成功定义 |
| 产品范围 | 方案清晰度、范围边界、决策就绪度 |
| 用户体验与影响 | 用户群体、边界情况、区域/无障碍考虑 |
| 指标与数据严谨性 | 成功指标、护栏指标、测量方案 |
| 关联影响与上下文 | 跨系统影响、协作方顾虑、二阶效应 |
| 决策逻辑与优先级 | 权衡取舍、决策依据、备选方案、风险缓解 |

## 功能特性

- **4 级评审深度** — 自动将 PRD 分类为轻量 / 中等 / 完整 / 专项深度
- **7 种反模式检测** — 发现无支撑假设、系统影响盲区、未检验的二阶效应等常见问题
- **结构化输出** — 上线就绪度评级 → 维度评分卡 → 详细发现与修复建议 → 优先级排序的行动项
- **可操作反馈** — 每条发现都附带具体修复建议，而非泛泛批评

## 安装

### 方式一：通过 zip 安装（WorkBuddy 桌面端）

1. 从 [Releases](../../releases) 页面下载 `prd-reviewer.zip`
2. 打开 WorkBuddy → 设置 → 技能
3. 点击"导入技能"并选择 zip 文件

### 方式二：手动安装

```bash
# 克隆到 WorkBuddy 技能目录
git clone https://github.com/SermierSu/prd-reviewer.git ~/.workbuddy/skills/prd-reviewer
```

重启 WorkBuddy 后技能将自动加载。

## 使用方式

安装完成后，通过以下话术触发技能：

- "评审这个PRD"
- "帮我评审需求文档"
- "review this PRD"
- "评估这个需求"

然后粘贴或上传你的 PRD 文档。技能将自动执行：

1. 分类 PRD 评审深度
2. 评估全部 6 个维度
3. 检测常见反模式
4. 输出带优先级行动项的结构化评审结果

## 技能结构

```
prd-reviewer/
├── SKILL.md                           # 核心工作流指令
└── references/
    └── prd-review-framework.md        # 完整评审框架参考
```

## 方法论

本技能基于 Uber 的 "First-Pass PRD Evaluator" 框架，针对 AI 辅助自动化评审进行了适配。目标是让后续的人工评审更加聚焦和高效，而非取代人类判断。

## 许可证

MIT 许可证 — 详见 [LICENSE](LICENSE)。

## 相关项目

- [prd-writer](https://github.com/SermierSu/prd-writer) — 配套技能，使用 8 节模板编写 PRD
