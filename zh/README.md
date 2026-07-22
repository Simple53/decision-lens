# Decision Lens (`decision-lens`)

<p main-align="center">
  <img src="../assets/logo.svg" alt="Decision Lens Logo" width="160" height="160" />
</p>

> **宿主无关的深度领域研究与决策支持 Agent 协议 (Host-Agnostic Decision Support Protocol)**  
> 融合 **MetaScout 自主工具发现**、**权限审批与安全回滚**、**零 URL 幻觉**、**10 大核心要素拆解**、**`uv` 可移植环境**，以及 **Excel (.xlsx) + 交互式 HTML 网页报告 (.html) + 可编辑 PPT 演示文稿 (.pptx)** 一体化导出。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.4.0](https://img.shields.io/badge/Release-v1.4.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.4.0)
[![Protocol: Host--Agnostic](https://img.shields.io/badge/Protocol-Host--Agnostic-green.svg)](#-宿主通用兼容性矩阵)

---

## 🌟 核心特性 (Core Features)

1. **MetaScout 自主工具发现与 5 大安全演进流程**：
   - 包含能力审计 (Capability Audit)、审批与权限审查 (Approval Audit)、隔离部署 (Isolated Sandbox)、动态回滚 (Dynamic Rollback) 与工具保留清理 (Housekeeping)。
2. **多形态报告一体化生成 (Excel, HTML & Editable PPTX)**：
   - 自动运行 Python 脚本生成自适应暗黑模式的 **交互式 HTML 网页报告 (.html)**、原生 **可编辑 PowerPoint 演示文稿 (.pptx)**，以及数据全量 **Excel 表格 (.xlsx)**。
3. **`uv` 驱动的 100% 可移植环境 (Portable Execution)**：
   - 统一由 `uv` 隔离管理运行（`uv run python scripts/generate_report.py`），做到零环境污染、零手动配置。
4. **绝对禁止 URL 幻觉与强可点击角标**：
   - 强制显式调用联网检索验证每一个 URL，正文必须使用可点击的 Markdown 超链接角标 `[[1]](URL)`。
5. **严禁总分排名与推荐**：
   - 保持中立决策辅助定位，去除“加权总分”与 1-N 强行排名，替换为客观的“情境权衡分析”。

---

## 🔌 宿主通用兼容性矩阵 (Host Compatibility)

Decision Lens 采用宿主无关协议，支持在主流 AI Agent 平台无缝接入：

| AI Agent 平台 | 接入方式与配置文件 | 人机授权接口映射 | 沙箱能力映射 |
|---|---|---|---|
| **Codex** (OpenAI) | `.codex/skills/decision-lens` | CLI Confirmation Prompt | Sandbox Execution |
| **Claude Code** | `.claude/skills/decision-lens` | Interactive Terminal Dialog | Isolated Process |
| **OpenCode** | `opencode.json` / Skills | Host Question Modal | Isolated Venv / Subagent |
| **Grok Build** | `grok.config.json` | Approval Prompt | Worker Subagent |
| **Antigravity / AGY** | `~/.gemini/config/skills.json` | `ask_question` Tool | `invoke_subagent` (self) |

---

## 📂 项目文件结构

```text
decision-lens/
├── assets/
│   └── logo.svg             # 扁平透明背景矢量 Logo
├── SKILL.md                 # 宿主无关英文 Agent 协议 (V1.4.0)
├── README.md                # 英文说明文档
├── plugin.json              # 通用 Plugin 元数据说明
├── pyproject.toml           # 可移植 uv 环境配置
├── requirements.txt         # Python 依赖清单
├── scripts/
│   └── generate_report.py   # Excel, HTML 与 PPTX 一体化导出脚本
├── resources/
│   └── report_template.md   # 标准化决策报告 Artifact 模板
└── zh/                      # 中文说明文档与资源
    ├── README.md            # 中文说明文档 (V1.4.0)
    ├── SKILL.md            # 中文协议定义 (V1.4.0)
    └── resources/
        └── report_template.md
```

---

## 🚀 快捷运行指南

### 1. 注册 Skill 到 AI Agent 平台
以 Antigravity / AGY 为例，将仓库添加到配置文件：

```json
{
  "entries": [
    { "path": "path/to/decision-lens" }
  ]
}
```

### 2. 通过 `uv` 一键测试报告导出
使用 `uv` 隔离运行测试，无需手动 `pip install`：

```bash
uv run python scripts/generate_report.py --output-dir ./output
```

输出产物包含：
- `domain_research_candidates.xlsx`（全量候选池 Excel）
- `domain_research_report.html`（交互式 HTML 网页）
- `domain_research_presentation.pptx`（原生可编辑 PPT 演示文稿）
