# Decision Lens (`decision-lens`)

> Advanced AI Agent / LLM Skill for deep domain research, evidence-based trade-off analysis, and transparent weighted scoring matrices without imposing biased recommendations.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[中文说明文档](zh/README.md)

---

## 🌟 Core Philosophy

The fundamental duty of `decision-lens` is to construct **verifiable, adjustable, and reproducible** decision-support information, rather than making value judgments on behalf of the user.

- **Decision Support Over Recommendation**: AI does not output a biased "I recommend Option A". Instead, it presents key variables, evidence coverage, conflict tables, and a transparent weighted scoring matrix for the user to make the final trade-off.
- **Zero Hallucination**: Enforces a 5-tier evidence grading system (Official Docs > Independent Benchmarks > Verified Community Threads > Sponsored Content). Avoids fake statistics and misleading decimal precision.
- **Transparent Weight Matrix**: Deconstructs decision variables with explicit weight origins (*User-specified* / *Scenario-derived* / *Default*). Users can tweak weights dynamically to recalculate rankings instantly.
- **Adaptive Workflow**: Dynamically scales execution depth from Level 1 (quick factual answer) to Level 4 (full multi-variable decision report).

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

1. **Phase 1: Research Scope Locking** – Confirm target goal, boundary constraints, and primary user concerns.
2. **Phase 2: Domain Cognitive Map** – Map knowledge branches, identify core tension models, and filter key variables from marketing noise.
3. **Phase 3: Evidence & Conflict Analysis** – Perform targeted web retrieval for pitfalls/benchmarks; structure conflicting views transparently.
4. **Phase 4: Option Matrix & Weighted Scoring** – Build comparison matrices and qualitative 1–5 integer weighted scoring tables.
5. **Phase 5: Decision Delivery** – Output verified facts, unresolved ambiguities, verification plans, and conditional decision prompts.
