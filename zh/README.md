# Decision Lens (领域决策支持 Skill - 中文版 V1.2.0)

[English Version](../README.md) | [Release v1.2.0](https://github.com/Simple53/decision-lens/releases/tag/v1.2.0)

面向 AI Agent / LLM 的高级 Skill，专注于在陌生或复杂领域建立认知、收集高质量证据、识别核心变量并构建透明可计算的决策矩阵。

> **核心哲学**：Skill 的职责是构建“可验证、可调整、可复算”的决策信息，而不是代替用户输出一个最终答案。

---

## 🌟 V1.2.0 核心特色

- **真实 Python 生成 Excel (.xlsx) 文档**：自动编写并运行 Python 脚本 (`pandas`/`openpyxl`)，在 Artifacts 目录下生成包含全量候选池与矩阵的真实可下载 `.xlsx` Excel 文件。
- **金字塔领域结构解析与专有名词词典**：引入金字塔原理（顶层目标 → 中层机制 → 底层技术栈）进行结构化解析，并集中设立专有名词与缩写词典板块。
- **真实长 URL 数字超链接规程 `[1]`**：正文使用 `[1]` 数字超链接，文末参考文献**严禁使用泛泛根域名**（如 `https://bilibili.com`），必须使用具体文章/视频/仓库的完整长 URL。
- **不限制数量全量候选池 (Excel 格式化大表)**：初筛扫描不限制项目数量，以类 Excel 的 Markdown 大表格完整列出全网发现的所有候选项目。
- **正文与矩阵保留 10–15 个核心方案**：从全量候选池中筛选出符合条件的主力项目，在方案对比矩阵、打分表与深度卡片中保留 10–15 个。
- **强制交互暂停与问答唤醒**：Phase 1 必须调用系统 `ask_question` 确认工具暂停，等待用户界面响应后再启动 Phase 3。

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
