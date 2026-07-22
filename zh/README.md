# Decision Lens (`decision-lens`) 中文说明文档

> 融合 **MetaScout 自主工具寻找**、**零 URL 幻觉**、**点击式内联角标**、**10 大核心要素解析**、**`uv` 可移植环境**，以及 **Excel (.xlsx) + 交互式 HTML 网页报告 (.html) + 可编辑 PPT 演示文稿 (.pptx)** 一体化自动生成的深度领域研究与决策支持 Agent 技能。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.4.0](https://img.shields.io/badge/Release-v1.4.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.4.0)

---

## 🌟 V1.4.0 核心重大更新

1. **MetaScout 自主工具发现与能力扩充 (MetaScout Tool Discovery)**：
   - 结合 MetaScout 思想，Agent 在面临特定解析、计算或格式转化需求时，可自主审计能力缺口并搜索补充开源工具/库，通过 `ask_question` 工具获得许可后，通过沙箱/虚拟环境即时挂载运行。
2. **多形态报告一体化生成 (HTML 网页报告 + 可编辑 PPT)**：
   - 自动生成现代自适应暗黑模式的 **交互式 HTML 网页报告 (.html)**。
   - 自动运行基于 `python-pptx` 的 Python 脚本提炼 10 大要素与对比矩阵，生成原生 **可编辑 PowerPoint 演示文稿 (.pptx)**。
   - 保持并强化真实 **Excel (.xlsx)** 数据表格导出。
3. **`uv` 驱动的 100% 可移植环境 (Portable Environment)**：
   - 所有 Python 交互与生成脚本统一由 `uv` 管理运行（例如 `uv run python scripts/generate_report.py` 或 `uv run --with ...`），做到跨平台零环境污染、零手动配置。
4. **绝对禁止 URL 幻觉 (Zero Hallucination Web Search Protocol)**：
   - 强制 AI 显式调用 `search_web` 查找并验证每一个 URL，彻底消灭虚构链接。
5. **严禁总分排名与推荐 (No Total Scores & No Rankings)**：
   - 纯粹的客观决策辅助，去除“加权总分”与 1-N 强行排名，替换为“情境权衡分析”。

---

## 📂 项目文件结构

```text
decision-lens/
├── SKILL.md                 # 英文 Agent 指令定义 (V1.4.0)
├── README.md                # 英文说明文档
├── pyproject.toml           # 可移植 uv 环境配置
├── requirements.txt         # Python 依赖清单
├── scripts/
│   └── generate_report.py   # Excel (.xlsx), HTML (.html) 与 PPTX (.pptx) 一体化导出脚本
├── resources/
│   └── report_template.md   # 标准化决策报告 Artifact 模板 (包含 HTML/PPTX 入口)
├── examples/
│   └── good_example.md      # 案例说明
└── zh/                      # 中文说明文档与资源
    ├── README.md            # 中文说明文档 (V1.4.0)
    ├── SKILL.md            # 中文指令定义 (V1.4.0)
    └── resources/
        └── report_template.md
```

---

## 🚀 快捷运行与使用指南

### 1. 注册 Skill 到 Agent 系统
将本仓库路径添加到 Antigravity 或 Agent 系统的技能配置（`~/.gemini/config/skills.json`）：

```json
{
  "entries": [
    { "path": "path/to/decision-lens" }
  ]
}
```

### 2. 通过 `uv` 运行多格式测试生成脚本
无需手动 `pip install`，使用 `uv` 即可开箱即用：

```bash
uv run python scripts/generate_report.py --output-dir ./output
```

将在 `./output` 目录下自动生成：
- `domain_research_candidates.xlsx` （Excel 全量候选池与矩阵）
- `domain_research_report.html` （交互式 HTML 网页报告）
- `domain_research_presentation.pptx` （原生可编辑 PPT 演示文稿）
