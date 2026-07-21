# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, Python Excel (.xlsx) file generation, Pyramid domain breakdown, terminology glossary, exact URL citations [1], and transparent weighted scoring.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.2.0](https://img.shields.io/badge/Release-v1.2.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.2.0)
[中文说明文档](zh/README.md)

---

## 🌟 V1.2.0 Major Features

- **Python Excel (.xlsx) File Generation**: Automatically runs Python scripts (`pandas`/`openpyxl`) to generate real, downloadable `.xlsx` Excel spreadsheet files alongside Markdown Artifacts.
- **Pyramid Domain Breakdown & Terminology Glossary**: Incorporates Minto's Pyramid Principle for structured domain mapping and a dedicated jargon/acronym dictionary.
- **Exact Specific URL Citations `[1]`**: Enforces exact, specific web page/video URLs (e.g. `https://bilibili.com/video/BVxxx` or `https://github.com/org/repo/issues/123`), completely forbidding generic root homepages.
- **Unconstrained Candidate Scanning & Full Table**: Scans all candidate options without artificial caps and outputs an unconstrained Excel-like Markdown table of ALL scanned candidates.
- **Top 10–15 Core Comparison Matrix**: Retains 10–15 top eligible candidates in the main Option Matrix, Weighted Scoring Table, and Deep-Dive Technical Cards.
- **Mandatory Interactive Pause**: Enforces Phase 1 execution pause (`ask_question` / confirmation modal) before Phase 3 retrieval.

---

## 📂 Repository Structure

```text
decision-lens/
├── SKILL.md                 # Core LLM Agent system instructions (English V1.2.0)
├── README.md                # Main documentation (English)
├── resources/
│   └── report_template.md  # Standardized decision report Artifact template
├── examples/
│   └── good_example.md     # Reference example (Database selection case study)
└── zh/                      # Chinese documentation & resources
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义 (V1.2.0)
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
