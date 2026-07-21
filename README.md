# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, Python Excel (.xlsx) file generation, 10 Core Factors deep dive, zero-hallucination URL citations [[1]](url), and strict no-ranking decision support.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.3.0](https://img.shields.io/badge/Release-v1.3.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.3.0)
[中文说明文档](zh/README.md)

---

## 🌟 V1.3.0 Major Features

- **Zero Hallucination Web Search Protocol**: Explicitly mandates the AI to invoke `search_web` to retrieve and verify every single URL, completely eliminating hallucinated links from parametric memory.
- **Clickable Inline Citations `[[1]](URL)`**: Enforces functional, clickable Markdown hyperlinks for all inline citations.
- **Top 10 Core Domain Factors Breakdown**: Replaces the brief pyramid map with a systemic, deep-dive section covering ~10 critical domain variables/mechanisms, requiring at least one paragraph of explanation for each factor.
- **Dynamic, Topic-Specific Titles**: Auto-generates engaging, highly readable report titles tailored to the research topic (banning generic boilerplate titles).
- **Strict No-Ranking Decision Support**: Completely removes Total Scores and 1-N rankings to prevent biased AI recommendations. Replaces standard decision guidance with objective "Trade-off Analysis" (e.g., "If priority is X, choose Y").
- **Python Excel (.xlsx) File Generation**: Automatically runs Python scripts (`pandas`/`openpyxl`) to generate real, downloadable `.xlsx` Excel spreadsheet files alongside Markdown Artifacts.

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
