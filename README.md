# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, dynamic source discovery, and transparent weighted scoring matrices without imposing biased recommendations.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Release: v1.0.0](https://img.shields.io/badge/Release-v1.0.0-blue.svg)](https://github.com/Simple53/decision-lens/releases/tag/v1.0.0)
[中文说明文档](zh/README.md)

---

## 🌟 Core Features

- **Decision Support Over Recommendation**: AI does not output a biased "I recommend Option A". Instead, it presents key variables, evidence coverage, conflict tables, and a transparent weighted scoring matrix for the user to make the final trade-off.
- **Dynamic Source Discovery & Choice**: Rejects hardcoded static platform presets. During initial scanning, dynamically discovers 3–5 of the most active and reliable sources specific to the query topic, presenting them to the user for confirmation or editing before proceeding.
- **Hard Constraint Filtering**: Mandatory requirements (e.g., "must be a standalone desktop app") act as absolute dealbreakers. Ineligible candidates are eliminated immediately during screening.
- **Endnote Citation System**: Uses Markdown superscripts `[^1]`, `[^2]` throughout the text, mapping every claim, feature, and statistic to a numbered reference list at the end of the document.
- **Transparent Weight Matrix**: Deconstructs decision variables with explicit weight origins (*User-specified* / *Scenario-derived* / *Default*). Users can tweak weights dynamically to recalculate rankings instantly.

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

---

## 🛠 Workflow Phases

1. **Phase 1: Research Scope, Source Discovery & Parameter Locking** – Confirm target goal, boundary constraints, dynamically discover topic-specific sources, and present parameters to the user for locking.
2. **Phase 2: Candidate Pool & Domain Cognitive Map** – Map knowledge branches, perform broad candidate scanning (6–8 pool), filter out ineligible candidates via Hard Constraints, and identify core tension models.
3. **Phase 3: Targeted Deep-Dive & Conflict Analysis** – Perform targeted web retrieval strictly within user-approved source boundaries; construct Deep-Dive Specification Cards and Conflict Tables.
4. **Phase 4: Option Matrix & Weighted Scoring** – Build comparison matrices and qualitative 1–5 integer weighted scoring tables.
5. **Phase 5: Decision Delivery & Reference List** – Output verified facts, unresolved ambiguities, verification plans, conditional decision prompts, and the complete Endnote References List (`## References`).
