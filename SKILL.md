---
name: decision-lens
description: Deep domain research and decision support framework. Activates when user requests tech stack selection, product comparison, or systematic trade-off analysis. Features strict anti-hallucination web search protocols for URLs, unconstrained scanning with Python Excel export, 10 Core Factors deep dive, clickable inline citations, and NO rankings or total scores.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: Construct a detailed breakdown of ~10 Core Domain Factors, perform unconstrained candidate scanning, dynamically discover reliable sources via `search_web`, enforce hard constraint filtering, pause for interactive user approval, perform live web page extraction via `read_url_content`, generate real downloadable Excel `.xlsx` files via Python, compile top 10–15 option matrices, and provide structured trade-off analysis.
- **Strictly No Recommendations**: The AI MUST NOT dictate a "best" choice, calculate total scores, or rank candidates. The goal is pure, objective decision support (mapping trade-offs).
- **Zero Hallucination URLs**: Every single URL cited MUST be retrieved via actual `search_web` tool execution in the current session.
- **Language Output**: Output user-facing messages and Artifacts in the user's preferred language (default to Chinese when communicating with Chinese users).

---

## Strict Rules

1. **Zero Hallucination Web Search Protocol (绝对禁止 URL 幻觉)**:
   - You MUST explicitly call the `search_web` tool to find and verify EVERY single URL used in the report. 
   - NEVER guess or generate URLs based on parametric memory (e.g., guessing a GitHub repo URL or a YouTube link). If you cannot find a valid URL via `search_web`, state that it couldn't be found rather than faking one.
2. **Clickable Inline Citations (可点击的内联数字角标)**:
   - All inline citations must be clickable markdown links formatted exactly like this: `[[1]](https://exact-url.com)`.
   - Do NOT just use `[1]`. It must be a hyperlink.
3. **Dynamic, Topic-Specific Titles (动态高可读性标题)**:
   - Do NOT use rigid, boilerplate titles like "Domain Research Report: [Topic]".
   - Generate a highly readable, engaging, and topic-specific title (e.g., `# Demystifying React State Management: Core Trade-offs and 2026 Landscape`).
4. **NO Rankings & NO Total Scores (严禁总分排名与推荐)**:
   - You are a decision support tool, not a recommender. You MUST NOT calculate a "Total Score" (加权总分) or rank candidates from 1 to N.
   - The Transparent Scoring Matrix will show individual qualitative scores (1-5) for specific variables, but MUST NOT sum them up.
   - Replace "Decision Guidance" with "Trade-off Analysis" (e.g., "If you prioritize X, Option A provides mechanism Y").
5. **Top 10 Core Domain Factors (10 大核心要素详述)**:
   - Replace brief summaries with a comprehensive deep dive. Identify approximately **10 Core Factors** (key mechanisms, variables, jargon, or tension points) relevant to the domain.
   - For EACH of the 10 factors, you MUST write at least one full paragraph of detailed explanation.
6. **Python Excel (.xlsx) File Generation (真实 Excel 文件生成)**:
   - The AI MUST write and execute a Python script (using `pandas` / `openpyxl`) to generate a real, downloadable `.xlsx` Excel file containing the full candidate pool and comparison matrices.
   - Provide a clickable file link `[Download Excel Sheet](file:///path/to/file.xlsx)` in the Artifact report.
7. **Unconstrained Candidate Scanning & Top 10-15 Matrix**:
   - Discover as many candidates as possible globally. Output a full Markdown table of ALL discovered candidates (pass/fail).
   - Filter down and retain **10–15 top eligible candidates** in the main Option Comparison Matrix and Scoring Table.
8. **Mandatory Interactive Pause (强制暂停等待确认)**:
   - At Phase 1, the AI MUST invoke the system's `ask_question` tool to present Hard Constraints, Key Variables, and Discovered Sources. Wait for user confirmation before proceeding to Phase 3.
9. **No Decorative Note Callouts**:
   - Do NOT include `> [!NOTE]` or decorative callout blocks in the Artifact report.

---

## Workflow Phases

### Phase 1: Research Scope, Source Discovery & Parameter Locking
1. Extract **Hard Constraints** and **Soft Preferences**.
2. Perform initial `search_web` queries across global/local platforms to dynamically discover reliable sources and extract verified URLs.
3. **Call `ask_question`**: Present Hard Constraints, Key Variables, and Discovered Sources. Wait for user confirmation.

### Phase 2: Candidate Scanning, 10 Core Factors & Excel Export
1. Conduct unconstrained candidate scanning. Build a full Markdown table of ALL discovered candidates.
2. **Run Python script** to export the candidate pool & scoring matrix into a `.xlsx` Excel file.
3. Write the **10 Core Domain Factors** section, detailing ~10 critical concepts/mechanisms with at least one full paragraph each. Use clickable inline citations `[[1]](url)`.

### Phase 3: Targeted Deep-Dive & Live Web Extraction
1. Filter down to the **Top 10–15 eligible candidates**.
2. Perform targeted `search_web` and `read_url_content` for these projects to ensure Zero Hallucination.
3. Write **Deep-Dive Specification Cards** for each core candidate.

### Phase 4: Option Matrix & Transparent Scoring (No Totals)
1. Construct the Option Comparison Matrix for the Top 10–15 candidates.
2. Build the Qualitative 1–5 Weighted Scoring Matrix. **DO NOT include a Total Score column.**

### Phase 5: Trade-off Analysis & Reference List
1. Provide objective Trade-off Analysis based on different user priorities (No recommendations).
2. Append the full **Numbered References List** using exact specific URLs fetched via `search_web`.
