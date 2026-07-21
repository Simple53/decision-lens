# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, dynamic source discovery, and transparent weighted scoring matrices without imposing biased recommendations.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.0.1](https://img.shields.io/badge/Release-v1.0.1-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.0.1)
[中文说明文档](zh/README.md)

---

## 🌟 Core Features

- **Decision Support Over Recommendation**: AI does not output a biased "I recommend Option A". Instead, it presents key variables, evidence coverage, conflict tables, and a transparent weighted scoring matrix for the user to make the final trade-off.
- **Mandatory Interactive Pause**: Enforces Phase 1 execution pause (`ask_question` / confirmation modal) to wait for explicit user approval before Phase 3 retrieval.
- **Dynamic Source Discovery & Choice**: Rejects hardcoded static platform presets. Dynamically discovers active, topic-specific reliable sources during initial scanning and submits them for user confirmation.
- **Hard Constraint Filtering & Silent Elimination**: Mandatory requirements act as absolute dealbreakers. Ineligible candidates are silently eliminated and excluded from primary comparison tables.
- **Clean Endnote Citation System**: Markdown superscripts `[^1]`, `[^2]` mapping strictly to valid web links in `## References` (no leading dashes, no decorative Note callout blocks).

---

## 📂 Repository Structure

```text
decision-lens/
├── SKILL.md                 # Core LLM Agent system instructions (English)
├── README.md                # Main documentation (English)
├── resources/
│   └── report_template.md  # Standardized decision report Artifact template
├── examples/
│   └── good_example.md     # Reference example (Database selection case study)
└── zh/                      # Chinese documentation & resources
    ├── README.md            # 中文说明文档
    ├── SKILL.md            # 中文指令定义
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
