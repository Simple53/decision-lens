# Decision Lens (领域决策支持 Skill - 中文版 V1.0.1)

[English Version](../README.md) | [Release v1.0.1](https://github.com/Simple53/decision-lens/releases/tag/v1.0.1)

面向 AI Agent / LLM 的高级 Skill，专注于在陌生或复杂领域建立认知、收集高质量证据、识别核心变量并构建透明可计算的决策矩阵。

> **核心哲学**：Skill 的职责是构建“可验证、可调整、可复算”的决策信息，而不是代替用户输出一个最终答案。

---

## 🌟 V1.0.1 核心修缮与特色

- **强制交互暂停与问答唤醒**：Phase 1 必须调用系统的 `ask_question` 确认工具暂停，明确等待用户界面响应后再启动 Phase 3。
- **硬性条件一票否决与静默剔除**：初筛不符合硬性限制的项目直接静默剔除，**绝不在主对比表格中列出**，保证界面简洁干净。
- **标准尾注与真实网页超链接**：消除尾注列表中多余的 `-` 连字符，确保全量 URL 为有效的真实网页超链接，正文角标一一对应。
- **删除多余提示块**：移除生成的 Artifact 开头无意义的 `> [!NOTE]` 提示块。
- **动态信源探索与用户裁决**：拒绝硬编码静态模板。初筛探索阶段自动识别最靠谱的 3-5 个信源，汇报给用户裁决并可随时删改。

---

## 📂 目录结构

```text
decision-lens/
├── SKILL.md                 # Agent 核心指令与动作规范 (英文 V1.0.1)
├── README.md                # 英文说明文档
├── resources/
│   └── report_template.md  # 英文报告模板
├── examples/
│   └── good_example.md     # 英文示例
└── zh/                      # 中文文档与资源目录
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义 (V1.0.1)
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
