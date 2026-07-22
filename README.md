# Decision Lens (`decision-lens`)

> Advanced AI Agent Skill for deep domain research, featuring **MetaScout dynamic tool discovery**, zero-hallucination URL citations [[1]](url), 10 Core Factors deep dive, **`uv` portable environments**, and integrated generation of **Excel spreadsheets (.xlsx)**, **Interactive HTML Web Reports (.html)**, and **Editable PowerPoint Presentations (.pptx)**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.4.0](https://img.shields.io/badge/Release-v1.4.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.4.0)
[中文说明文档](zh/README.md)

---

## 🌟 V1.4.0 Major Features

- **MetaScout Dynamic Tool Discovery**: Incorporates MetaScout's philosophy. When facing capability gaps (e.g. missing parsers, data models, or export tools), the agent autonomously discovers tools/libraries, requests user authorization via `ask_question`, and runs them via isolated portable environments.
- **Multi-Format Report Generation (HTML & Editable PPTX)**: Automatically builds responsive dark-mode **Interactive HTML Reports (.html)** and native **Editable PowerPoint Presentations (.pptx)** via Python scripts (`python-pptx`), alongside traditional **Excel spreadsheets (.xlsx)**.
- **100% Portable Execution with `uv`**: Environment management is driven by `uv` (`uv run python scripts/generate_report.py`), eliminating global environment pollution and ensuring zero-config cross-platform execution.
- **Zero Hallucination Web Search Protocol**: Explicitly mandates invoking `search_web` to retrieve and verify every single URL.
- **Clickable Inline Citations `[[1]](URL)`**: Enforces functional, clickable Markdown hyperlinks for all inline citations.
- **Strict No-Ranking Decision Support**: Completely removes Total Scores and 1-N rankings. Replaces biased recommendations with objective "Trade-off Analysis".

---

## 📂 Repository Structure

```text
decision-lens/
├── SKILL.md                 # Main LLM Agent system instructions (V1.4.0)
├── README.md                # Main documentation (English V1.4.0)
├── pyproject.toml           # Portable uv configuration
├── requirements.txt         # Dependency manifest
├── scripts/
│   └── generate_report.py   # Multi-format export script (Excel, HTML, PPTX)
├── resources/
│   └── report_template.md   # Standardized decision report Artifact template
├── examples/
│   └── good_example.md      # Reference case study
└── zh/                      # Chinese documentation & resources
    ├── README.md            # 中文说明文档 (V1.4.0)
    ├── SKILL.md            # 中文指令定义 (V1.4.0)
    └── resources/
        └── report_template.md
```

---

## 🚀 Quick Start & Usage

### 1. Register Skill Path
Add the repository path to your AI Agent framework or Antigravity configuration (`~/.gemini/config/skills.json`):

```json
{
  "entries": [
    { "path": "path/to/decision-lens" }
  ]
}
```

### 2. Portable Execution via `uv`
Generate all multi-format reports without manual environment setup:

```bash
uv run python scripts/generate_report.py --output-dir ./output
```

This generates:
- `domain_research_candidates.xlsx` (Excel candidate pool and scoring matrix)
- `domain_research_report.html` (Interactive web report)
- `domain_research_presentation.pptx` (Editable PowerPoint presentation)
