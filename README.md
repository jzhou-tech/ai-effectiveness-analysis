# AI-Native Engineering Effectiveness Analysis

基于 **AI-Native Engineering Effectiveness Evaluation Framework** 分析工程师与 AI Agent 的交互对话，识别效能模式、短板与培训方向。

## 工作流

```
cursor-chat-export (姐妹项目)          本项目
┌──────────────────────┐        ┌───────────────────────────┐
│  export_new.py       │        │  Cursor Agent +           │
│  导出 transcript     │──────→ │  evaluation-framework     │
│  为 Markdown 文件    │        │  按框架分析 transcript    │
└──────────────────────┘        └───────────────────────────┘
```

1. 在 `cursor-chat-export` 项目中运行 `python export_new.py export` 导出 agent transcript
2. 将导出的 Markdown 文件放入本项目（或直接在 Cursor 中引用）
3. 在 Cursor 中打开本项目，启动 Agent 对话，引用 `evaluation-framework` rule
4. 使用 `prompts/` 目录下的模板进行分析

## 项目结构

```
ai-effectiveness-analysis/
├── .cursor/rules/
│   └── evaluation-framework.mdc   # Cursor Rule: 完整评估框架 + AI 角色定义
├── prompts/
│   ├── per-transcript.md          # 单次 transcript 分析模板
│   ├── cross-session.md           # 多会话纵向对比模板
│   └── team-aggregation.md        # 团队层面汇总模板
└── README.md
```

## 评估框架概要

框架围绕 AI-native 开发的四个阶段评估工程师行为：

| Phase | 名称 | 核心关注 |
|-------|------|----------|
| 1 | Requirement Clarification & Spec Definition | 需求澄清与规格定义 |
| 2 | Planning & Task Decomposition | 计划制定与任务拆解 |
| 3 | Orchestration, Verification & Critical Engagement | 编排、验证与批判性参与 |
| 4 | Continuous Alignment, Adaptation & Knowledge Capture | 持续对齐、自适应调整与知识沉淀 |

Phase 3 进一步区分三层行为：
- **Tier 1 — Proactive Interrogation**: 主动提问，用领域知识发现 AI 未暴露的问题（最高价值）
- **Tier 2 — Directed Quality Assurance**: 指导 AI 写测试、review 代码、讨论取舍
- **Tier 3 — Reactive Correction**: 被动纠错，仅在 AI 产出明显错误时介入（基线）

## 使用方式

### 分析单次对话

在 Cursor Agent 中：

```
@evaluation-framework

请按框架分析以下 transcript：
工程师：张三
项目：用户认证模块重构
日期：2026-03-25

[粘贴或引用 transcript 内容]
```

### 跨会话对比

参考 `prompts/cross-session.md` 模板，一次性提供同一工程师的多个 transcript。

### 团队汇总

参考 `prompts/team-aggregation.md` 模板，基于多人的分析结果汇总团队共性。

## 相关项目

- [cursor-chat-export](../cursor-chat-export/) — Cursor 对话导出工具，提供数据采集能力
