---
name: decision-lens
description: Deep domain research and decision support framework. Activates when the user requests tech stack selection, product comparison, industry research, or systematic trade-off analysis. Features unconstrained candidate scanning with full Markdown/Excel tables, live web page extraction, Chinese internet coverage, top 10-15 comparison matrices, and clean endnote citations.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: Construct domain maps, perform unconstrained candidate scanning, dynamically discover query-specific reliable sources (including Chinese tech communities), enforce hard constraint filtering, pause for interactive user approval via question tools, perform live web page extraction via `read_url_content`, compile top 10–15 option matrices, build transparent weighted scoring matrices, and provide deep-dive technical cards.
- **Non-Goal**: AI does NOT dictate the "best" choice or make value judgments for the user. If the user explicitly asks for a recommendation, provide a guarded suggestion clearly labeled as *"tentative preference based on current evidence"*.
- **Language Output**: Output user-facing messages and Artifacts in the user's preferred language (default to Chinese when communicating with Chinese users).

---

## Strict Rules

1. **Unconstrained Candidate Scanning & Full Table (无限制候选池与全量表格)**:
   - Do NOT limit the candidate discovery scan to 3–4 items. Discover as many candidates as possible across global (GitHub, Reddit) and Chinese (Zhihu, V2EX, Gitee, Juejin) platforms.
   - In the Artifact, output an unconstrained Markdown table (Excel-like formatting) listing ALL candidates discovered, their form factors, Hard Constraint pass/fail status, and reasons.
2. **Top 10–15 Primary Comparison Matrix**:
   - Filter down and retain **10–15 top eligible candidates** in the main Option Comparison Matrix, Transparent Scoring Table, and Deep-Dive Specification Cards (rather than a sparse list of 3–4).
3. **Bilingual & Chinese Tech Community Scans**:
   - Must execute search queries in both English and Chinese (e.g. `开源 桌面 AI agent 编程 替代 Claude Code site:zhihu.com OR site:v2ex.com OR site:juejin.cn`).
   - Actively search Chinese developer communities (Zhihu, V2EX, Gitee, Juejin, Bilibili) to capture domestic open-source desktop agents and Chinese API setup experiences.
4. **Mandatory Live Search & Web Page Extraction (强制实操检索与网页读取)**:
   - **No Pure Parametric Memory Dumps**: For key candidates, execute targeted `search_web` queries and call `read_url_content` to read actual README files or project homepages.
   - Extract live features, installation dependencies, and authentic metrics directly from fetched web pages.
5. **Hard Constraint Filtering (一票否决机制)**:
   - Explicitly separate **Hard Constraints** (mandatory requirements like "must be a standalone desktop app") from **Soft Preferences** (weighted evaluation factors). Any candidate failing a Hard Constraint is tagged as `[Eliminated]` in the initial full table and excluded from the main Top 10–15 Comparison Matrix.
6. **Mandatory Interactive Pause (强制暂停等待用户确认)**:
   - At Phase 1, the AI MUST invoke the system's `ask_question` tool (or pause execution) to present extracted Hard Constraints, Key Variables, Weights, and Discovered Sources. Wait for user confirmation before proceeding to Phase 3.
7. **Clean Endnote Citation System (标准尾注与有效超链接)**:
   - Attach inline superscripts `[^1]`, `[^2]` to all key claims, project features, metrics, and data points.
   - At the end of the document, list all references in a dedicated `## References` section using standard markdown footnote syntax (NO leading dashes):
     ```markdown
     [^1]: [Source Title](https://valid-url.com) - Context description
     ```
   - All URLs MUST be valid, clickable HTTP/HTTPS web links `[Title](https://...)`.
8. **No Decorative Note Callouts**:
   - Do NOT include `> [!NOTE]` or decorative callout blocks in the generated Artifact report.
9. **Artifact as Primary Medium**: Create `domain_research_<topic>.md` as a living report and append updates across workflow phases. Chat output must remain concise summaries and decision prompts.
10. **Score Honesty**: Use qualitative integers (1–5 scale). Avoid misleading decimal precision.

---

## Workflow Phases

### Phase 1: Research Scope, Source Discovery & Parameter Locking
1. Extract **Hard Constraints** (mandatory criteria) and **Soft Preferences** (evaluation metrics).
2. Perform initial broad scanning across global and Chinese search queries to dynamically discover 3–5 top reliable platforms/sources.
3. **MUST Call `ask_question` / Pause Execution**: Present Hard Constraints, Key Variables (<10 factors), proposed Weights, and Discovered Sources. Wait for user confirmation.

### Phase 2: Candidate Pool & Domain Cognitive Map
1. Conduct unconstrained candidate scanning across GitHub, Gitee, Zhihu, V2EX, etc.
2. Build an unconstrained Markdown table (Excel-like format) of ALL discovered candidates with Hard Constraint pass/fail status.
3. Construct the Domain Map (Knowledge Tree, Core Tension Model, Key Variables vs Marketing Noise) in the Artifact with inline superscripts `[^N]`.

### Phase 3: Targeted Deep-Dive & Live Web Extraction
1. Filter down to the **Top 10–15 eligible candidates**.
2. Perform targeted `search_web` and `read_url_content` page extractions for these 10–15 projects.
3. Structure conflicting claims into a Conflict Resolution Table and write **Deep-Dive Specification Cards** for each core candidate.

### Phase 4: Option Matrix & Transparent Scoring Matrix
1. Construct the Option Comparison Matrix for the **Top 10–15 candidates**.
2. Construct the Transparent Weight Table (origin: *User-specified*, *Scenario-derived*, *Default*).
3. Build the Qualitative 1–5 Weighted Scoring Matrix.

### Phase 5: Decision Delivery & Reference List
1. Output Verified Facts, Unresolved Ambiguities, and Actionable Verification Plans.
2. Provide Conditional Decision Guidance (e.g., "If priority is X → Option A").
3. Append the full **Numbered References List** (`## References`) at the very end of the document, mapping every superscript `[^N]` to its full valid web link.
