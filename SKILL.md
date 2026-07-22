---
name: decision-lens
description: Deep domain research and decision support framework (V1.4.0 Enhanced). Integrates MetaScout autonomous tool/library discovery, zero-hallucination web search protocols, clickable inline citations [[1]](URL), 10 Core Factors deep dive, portable uv environment execution, auto-generation of downloadable Excel (.xlsx), interactive HTML web reports (.html), and editable PowerPoint presentations (.pptx). Strictly bans total scores or 1-N rankings.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: 
  1. **MetaScout Dynamic Tool Discovery**: Autonomously identify capability gaps (e.g., missing data parsers or document export tools), propose required libraries/tools via `ask_question`, and deploy via portable `uv` environments.
  2. **Multi-Format Deliverables**: Generate not only Markdown Artifact reports, but also auto-build real downloadable **Excel spreadsheets (.xlsx)**, **Interactive HTML Web Reports (.html)**, and **Editable PowerPoint Presentations (.pptx)** via Python scripts.
  3. **Zero-Hallucination & Neutrality**: Construct detailed breakdowns of ~10 Core Domain Factors, perform unconstrained candidate scanning, dynamically discover reliable sources via `search_web`, enforce hard constraint filtering, pause for interactive user approval, and provide structured trade-off analysis.
- **Strictly No Recommendations**: The AI MUST NOT dictate a "best" choice, calculate total scores, or rank candidates. The goal is pure, objective decision support (mapping trade-offs).
- **Portable Execution (`uv`)**: All Python scripts run via `uv` (e.g., `uv run python scripts/generate_report.py`) ensuring zero global environment pollution and seamless cross-platform execution.

---

## Strict Rules

1. **MetaScout Autonomous Tool Discovery Protocol**:
   - When encountering a capability gap (e.g., needing custom parsers, data models, or export engines like `python-pptx`, `jinja2`, `openpyxl`), the AI MUST NOT guess or hallucinate logic.
   - Use `search_web` to search for appropriate Python packages/tools.
   - Before executing/installing, **MUST call `ask_question`** to present the tool rationale and request explicit user authorization.
   - Once authorized, run tools via portable `uv` environments in isolation.
2. **Multi-Format Report Generation (Excel, HTML & Editable PPTX)**:
   - Must run Python scripts to automatically export three distinct deliverables:
     - 📊 **Excel Sheet (.xlsx)**: Full candidate pool and scoring table.
     - 🌐 **Interactive HTML Report (.html)**: Modern responsive web page (dark/light themes, micro-interactive cards).
     - 📑 **Editable PowerPoint Presentation (.pptx)**: Native editable slides generated via `python-pptx`.
   - Provide clickable file links (e.g., `[View HTML Report in Browser](file:///path/to/report.html)`).
3. **`uv` Portable Environment Requirement**:
   - All Python invocations MUST use `uv` (`uv run python ...` or `uv run --with ...`). Global `pip install` is strictly prohibited.
4. **Zero Hallucination Web Search Protocol**:
   - Explicitly call `search_web` to verify every single URL. Never guess or hallucinate links.
5. **Clickable Inline Citations**:
   - Inline citations MUST be formatted as clickable markdown links: `[[1]](https://exact-url.com)`.
6. **NO Rankings & NO Total Scores**:
   - Qualitative scores (1-5) MUST NOT be summed up into a Total Score column. No candidate rankings.
7. **Top 10 Core Domain Factors Breakdown**:
   - Write at least one full paragraph of detailed explanation for EACH of ~10 core domain factors.

---

## Workflow Phases

### Phase 0: Capability Audit & MetaScout Tool Setup
Audit task requirements (data extraction, HTML/PPTX generation). If missing tools, invoke `ask_question` for authorization and run via `uv`.

### Phase 1: Research Scope, Source Discovery & Parameter Locking
Extract Hard Constraints; search reliable sources; **Call `ask_question`** to confirm parameters with user.

### Phase 2: Candidate Scanning, 10 Core Factors & Multi-Format Export
Scan candidate pool; detail 10 Core Factors; **Run `uv run python scripts/generate_report.py`** to produce `.xlsx`, `.html`, and `.pptx` files.

### Phase 3: Targeted Deep-Dive & Live Web Extraction
Perform targeted `search_web` and `read_url_content`; write Deep-Dive cards.

### Phase 4: Option Matrix & Transparent Scoring (No Totals)
Build Option Matrix and qualitative 1-5 Scoring Matrix (No Total Score column).

### Phase 5: Trade-off Analysis & Multi-Format Deliverables
Deliver objective Trade-off Analysis; provide direct file links to `.xlsx`, `.html`, and `.pptx` deliverables; append Numbered References List.
