# Decision Lens (领域决策支持 Skill - 中文版 V1.1.0)

[English Version](../README.md) | [Release v1.1.0](https://github.com/Simple53/decision-lens/releases/tag/v1.1.0)

面向 AI Agent / LLM 的高级 Skill，专注于在陌生或复杂领域建立认知、收集高质量证据、识别核心变量并构建透明可计算的决策矩阵。

> **核心哲学**：Skill 的职责是构建“可验证、可调整、可复算”的决策信息，而不是代替用户输出一个最终答案。

---

## 🌟 V1.1.0 核心特色

- **不限制数量全量候选池 (Excel 格式化大表)**：初筛扫描不限制项目数量，以类 Excel 的 Markdown 大表格完整列出全网发现的所有候选项目。
- **正文与矩阵保留 10–15 个核心方案**：从全量候选池中筛选出符合条件的主力项目，在方案对比矩阵、打分表与深度卡片中保留 10–15 个（避免只有 3-4 个选项）。
- **中英双语与中文互联网深挖**：检索同时覆盖英文（GitHub, Reddit）与中文开发者社区（知乎, V2EX, 稀土掘金, B站, Gitee）。
- **强制实地检索与网页读取 (`read_url_content`)**：拒绝凭模型内存脑补，强制执行独立 `search_web` 并调用 `read_url_content` 提取最新 README/官网数据。
- **强制交互暂停与问答唤醒**：Phase 1 必须调用系统 `ask_question` 确认工具暂停，等待用户界面响应后再启动 Phase 3。
- **标准尾注与真实超链接系统**：正文使用 `[^N]` 角标，文末输出不带 `-` 前缀的标准 Markdown 脚注列表，确保 URL 真实可点击。

---

## 📂 目录结构

```text
decision-lens/
├── SKILL.md                 # Agent 核心指令与动作规范 (英文 V1.1.0)
├── README.md                # 英文说明文档
├── resources/
│   └── report_template.md  # 英文报告模板
├── examples/
│   └── good_example.md     # 英文示例
└── zh/                      # 中文文档与资源目录
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义 (V1.1.0)
    ├── resources/
    │   └── report_template.md
    └── examples/
        └── good_example.md
```

---

## 🚀 安装与使用

在 Antigravity 全局配置目录（`~/.gemini/config/skills.json`）中注册路径：

```json
{
  "entries": [
    { "path": "path/to/decision-lens" }
  ]
}
```
