# Decision Lens (领域决策支持 Skill - 中文版 V1.3.0)

[English Version](../README.md) | [Release v1.3.0](https://github.com/Simple53/decision-lens/releases/tag/v1.3.0)

面向 AI Agent / LLM 的高级 Skill，专注于在陌生或复杂领域建立认知、收集高质量证据、识别核心变量并构建透明可计算的决策矩阵。

> **核心哲学**：Skill 的职责是构建“可验证、客观权衡”的决策信息，而不是代替用户输出一个带排名推荐的最终答案。绝对禁止 URL 幻觉，强制使用 `search_web` 提取真实链接。

---

## 🌟 V1.3.0 核心特色

- **绝对禁止 URL 幻觉规程 (Zero Hallucination)**：强制要求 AI 显式调用 `search_web` 提取并验证正文和参考文献中所有的 URL，彻底杜绝大模型基于内部参数瞎编死链。
- **可点击内联数字角标 `[[1]](URL)`**：强制规定所有的内联引用必须是可直接点击跳转的 Markdown 超链接，极大提升使用体验。
- **10 大核心领域要素详解**：废除原先点到为止的金字塔结构，改为系统性地深挖该领域约 10 个最核心机制/专有名词/张力点，每条至少撰写一段完整解释。
- **动态高可读性标题**：自动根据用户的研究主题，生成具有高度吸引力和可读性的专属标题，摒弃死板的“研究模板”字样。
- **严禁总分与排名推荐**：为保证绝对的客观中立，评分矩阵中禁止计算“加权总分”，禁止给候选方案排 1-2-3 名。决策引导改为中立的“情境权衡分析”。
- **真实 Python 生成 Excel (.xlsx) 文档**：自动编写并运行 Python 脚本 (`pandas`/`openpyxl`)，在 Artifacts 目录下生成包含全量候选池与矩阵的真实可下载 `.xlsx` Excel 文件。

---

## 📂 目录结构

```text
decision-lens/
├── SKILL.md                 # Agent 核心指令与动作规范 (英文 V1.2.0)
├── README.md                # 英文说明文档
├── resources/
│   └── report_template.md  # 英文报告模板
├── examples/
│   └── good_example.md     # 英文示例
└── zh/                      # 中文文档与资源目录
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义 (V1.2.0)
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
