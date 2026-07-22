---
name: decision-lens
description: Host-agnostic deep domain research and decision support framework (V1.4.0 Protocol). Universal compatibility across Codex, Claude Code, OpenCode, Grok Build, Antigravity, and custom agent platforms. Features MetaScout dynamic tool discovery, permission auditing, isolated sandbox deployment, automatic rollback protocols, zero-hallucination web citations, 10 Core Factors deep dive, and integrated generation of Excel (.xlsx), Interactive HTML (.html), and Editable PowerPoint (.pptx) reports. Strictly prohibits total scores or 1-N rankings.
---

# Decision Lens Workflow (Host-Agnostic Protocol V1.4.0)

## 1. Protocol Architecture & Host Abstraction

This Skill is built upon a **Host-Agnostic Protocol**, decoupling instructions from system-specific APIs. It natively runs across any agent ecosystem, including **Codex**, **Claude Code**, **OpenCode**, **Grok Build**, and **Antigravity**.

### Host Capability Mapping
- **[User Authorization Interface]**: Abstract user prompt/modal/question interface provided by the host system.
- **[Isolated Sandbox Capability]**: Abstract isolated worker/subagent/terminal/sandbox capability provided by the host system.
- **[Web Search & Retrieval]**: Abstract web search and URL content fetching tools.

---

## 2. MetaScout Tool Orchestration & 5-Step Security Protocols

When discovering capability gaps (e.g. missing parsers, data models, or export tools like `python-pptx`, `pandas`, `openpyxl`, `jinja2`), the AI MUST follow these 5 security workflows:

### 2.1 Capability Audit
- Audit task requirements against current environment capabilities.
- Identify exact capability gaps (e.g., `Requires python-pptx for editable PPTX slide generation`).

### 2.2 Approval & Permission Audit Protocol
- BEFORE installing or invoking new tools/libraries, **MUST submit a permission request via [User Authorization Interface]**.
- **The request MUST explicitly declare**:
  1. Package/tool name and origin (PyPI, GitHub, etc.).
  2. Rationale for introduction (Capability Gap).
  3. Scope of permissions required (e.g., local venv execution, no unauthorized network activity).
- **Silent/unauthorized installations are strictly prohibited.**

### 2.3 Isolated Sandbox Deployment via `uv`
- Upon user approval, deploy tools in an [Isolated Sandbox Capability] environment.
- **Enforce `uv` portable execution** (e.g., `uv run python script.py` or `uv run --with <package> python script.py`).
- Global `pip install` is prohibited to prevent host environment pollution.

### 2.4 Execution & Dynamic Rollback Protocol
- Execute the research task using newly acquired tools.
- **Exception & Rollback Handling**: If execution fails or dependency conflicts occur, capture full logs and trigger an automatic rollback:
  - Clean up failed build artifacts.
  - Gracefully fallback to standard Markdown and basic Excel export, logging the rationale transparently in the final report without faking outputs.

### 2.5 Tool Retention & Housekeeping Protocol
- Upon completion, perform housekeeping according to user preferences and workspace rules:
  - **Ephemeral Tools**: Clean up temporary virtual environments and build caches.
  - **Persistent Tools**: Register dependencies in workspace configuration (e.g., `pyproject.toml`) for auditability.

---

## 3. Strict Rules

### 3.1 Zero Hallucination Web Search Protocol
- Explicitly call web search tools to verify every single URL. Never guess or hallucinate links from parametric memory.

### 3.2 Clickable Inline Citations
- Inline citations MUST be clickable Markdown links: `[[1]](https://exact-url.com)`.

### 3.3 NO Rankings & NO Total Scores
- Pure decision support. Qualitative scores (1-5) MUST NOT be summed up into a Total Score column. Replace recommendations with objective **Trade-off Analysis**.

### 3.4 Top 10 Core Domain Factors Breakdown
- Write at least one full paragraph of detailed explanation for EACH of ~10 core domain factors.

### 3.5 Multi-Format Report Deliverables (Excel, HTML & Editable PPTX)
- Must run Python scripts via `uv` to deliver:
  1. 📊 **Excel Sheet (.xlsx)**: Full candidate pool and scoring table.
  2. 🌐 **Interactive HTML Report (.html)**: Modern responsive dark-mode web page.
  3. 📑 **Editable PowerPoint Presentation (.pptx)**: Native editable slides generated via `python-pptx`.

---

## 4. Workflow Phases

### Phase 0: Capability Audit & MetaScout Approval Setup
Audit requirements; request user approval via **2.2 Approval Protocol**; deploy via `uv`.

### Phase 1: Research Scope, Source Discovery & Parameter Locking
Extract constraints; search reliable sources; **Invoke [User Authorization Interface]** to lock parameters.

### Phase 2: Candidate Scanning, 10 Core Factors & Multi-Format Export
Detail 10 Core Factors; scan candidate pool; **Run `uv run python scripts/generate_report.py`** to produce `.xlsx`, `.html`, and `.pptx` files. Trigger **2.4 Dynamic Rollback Protocol** if errors occur.

### Phase 3: Targeted Deep-Dive & Live Web Extraction
Perform targeted search and content extraction; write Deep-Dive cards.

### Phase 4: Option Matrix & Transparent Scoring (No Totals)
Build Option Matrix and qualitative 1-5 Scoring Matrix (No Total Score column).

### Phase 5: Trade-off Analysis & Housekeeping
Deliver Trade-off Analysis; provide clickable file links to `.xlsx`, `.html`, and `.pptx` deliverables; execute **2.5 Housekeeping Protocol** and append verified reference list.
