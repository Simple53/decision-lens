# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, unconstrained candidate scanning, and transparent weighted scoring matrices without imposing biased recommendations.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.1.0](https://img.shields.io/badge/Release-v1.1.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.1.0)
[中文说明文档](zh/README.md)

---

## 🌟 V1.1.0 Major Features

- **Unconstrained Candidate Scanning & Full Table**: Discovers all candidate options without artificial caps and outputs an unconstrained Excel-like Markdown table of ALL scanned candidates.
- **Top 10–15 Core Comparison Matrix**: Retains 10–15 top eligible candidates in the main Option Matrix, Weighted Scoring Table, and Deep-Dive Technical Cards.
- **Bilingual & Chinese Tech Community Scans**: Executes query search across English (GitHub, Reddit) and Chinese developer communities (Zhihu, V2EX, Gitee, Juejin, Bilibili).
- **Mandatory Live Search & Web Extraction (`read_url_content`)**: Eliminates pure memory dumps by requiring explicit live searches and real web page extractions.
- **Mandatory Interactive Pause**: Enforces Phase 1 execution pause (`ask_question` / confirmation modal) before Phase 3 retrieval.
- **Clean Endnote Citation System**: Markdown superscripts `[^1]`, `[^2]` mapping strictly to valid web links in `## References` (no leading dashes).

---

## 📂 Repository Structure

```text
decision-lens/
├── SKILL.md                 # Core LLM Agent system instructions (English V1.1.0)
├── README.md                # Main documentation (English)
├── resources/
│   └── report_template.md  # Standardized decision report Artifact template
├── examples/
│   └── good_example.md     # Reference example (Database selection case study)
└── zh/                      # Chinese documentation & resources
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义 (V1.1.0)
    ├── resources/
    │   └── report_template.md
    └── examples/
        └── good_example.md
```

---

## 🚀 Installation & Setup

Register the skill path in your AI Agent framework or Antigravity configuration (`~/.gemini/config/skills.json`):

```json
{
  "entries": [
    { "path": "path/to/decision-lens" }
  ]
}
```
