# 单次 Transcript 分析模板

在 Cursor Agent 对话中使用此模板。确保已引用 `@evaluation-framework` rule。

---

## Prompt

```
@evaluation-framework

请按 AI-Native Engineering Effectiveness Evaluation Framework 分析以下 agent transcript。

### 基本信息

- **工程师**: [姓名]
- **项目/任务**: [项目名称和具体任务描述]
- **日期**: [YYYY-MM-DD]
- **会话类型**: [新功能开发 / Bug修复 / 重构 / 技术调研 / 其他]

### Transcript

[在此粘贴完整的 agent transcript，或使用 @file 引用导出的 Markdown 文件]

### 分析要求

请按以下结构输出评估报告：

1. **Session Overview** — 概述会话内容、类型和复杂度
2. **Phase-by-Phase Findings** — 逐阶段分析，引用 transcript 原文作为证据
3. **Phase 3 Tier Distribution** — 给出 Tier 1/2/3 的大致比例和典型示例
4. **Pattern Summary** — 归纳核心优势和短板
5. **AI-Native Maturity Assessment** — 判断该工程师在 AI-assisted ↔ AI-native 光谱上的位置

对于每个发现，请：
- 引用 transcript 中的具体对话片段作为证据
- 区分"强项（值得推广）"和"短板（需要培训）"
- 给出具体、可操作的改进建议
```

---

## 使用说明

1. 用 `cursor-chat-export` 中的 `export_new.py export` 导出目标 transcript
2. 在 Cursor 中打开本项目
3. 新建 Agent 对话，复制上方 Prompt 并填入信息
4. 将导出的 Markdown 文件通过 `@file` 引用，或直接粘贴内容
5. AI 将按框架输出结构化评估报告
