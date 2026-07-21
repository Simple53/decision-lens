---
name: decision-lens
description: Deep domain research and decision support framework. Activates when the user requests tech stack selection, product comparison, industry research, or systematic trade-off analysis. Collects evidence, maps domain variables, and constructs transparent weighted scoring matrices without imposing biased recommendations.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: Construct domain maps, collect web evidence, identify key trade-off variables, compile option matrices, and build transparent weighted scoring matrices.
- **Non-Goal**: AI does NOT dictate the "best" choice or make value judgments for the user. If the user explicitly asks for a recommendation, provide a guarded suggestion clearly labeled as *"tentative preference based on current evidence"*.
- **Language Output**: Output user-facing messages and Artifacts in the user's preferred language (default to Chinese when communicating with Chinese users).

---

## Strict Rules

1. **Zero Hallucination**: Every factual claim must be backed by `search_web` or `read_url_content` with Markdown inline links `[Source Name](URL)`. Unverified claims MUST be explicitly tagged as `[Unverified]`. Never invent citations or fake statistics.
2. **Artifact as Primary Medium**: Create `domain_research_<topic>.md` as a living report and append updates across workflow phases. Chat output must remain concise summaries and decision prompts.
3. **Source Quality Tiering**:

| Tier | Source Types |
|------|--------------|
| ★★★★★ | Official Documentation, Official Specs/Standards, Peer-Reviewed Papers |
| ★★★★☆ | Independent Lab Benchmarks, Major Tech Publications, Industry Reports |
| ★★★☆☆ | GitHub Issues, Reddit, StackOverflow, Verified Community Threads |
| ★★☆☆☆ | Personal Blogs, Discussion Forums |
| ★☆☆☆☆ | Sponsored Content, Vendor Whitepapers (Conflict of Interest) |

4. **Recency Awareness**: Tag key data points with publication dates. Fast-evolving tech fields require explicit warnings if sources are older than 12 months.
5. **Score Honesty**: Use qualitative integers (1–5 scale). Avoid misleading precision (e.g. no fake decimal precision like `8.14`).

---

## Adaptive Workflow

Tailor execution depth based on task complexity:

| Level | Scenario | Action Scope |
|-------|----------|--------------|
| **Level 1** | Single factual query | Answer directly with web search; skip Artifact |
| **Level 2** | Domain exploration | Phase 1 & 2 (Scope + Map) |
| **Level 3** | Multi-option comparison | Phase 1 to 4 (Scope + Map + Evidence + Matrix) |
| **Level 4** | Complex multi-variable decision | Phase 1 to 5 (Full Workflow) |

---

## Search Strategy

- **Must Search**: Live product pricing, benchmark metrics, regulations, papers, API docs, community complaints/pitfalls.
- **Direct Answer Allowed**: Core principles, standard algorithms, widely accepted computer science fundamentals.
- **Deep Extraction**: Use `read_url_content` for in-depth inspection of high-value search results.

---

## Phase 1: Research Scope Locking

Confirm the following parameters before deep searching (skip asking if already specified by user):

| Parameter | Description |
|-----------|-------------|
| Goal Type | Learning / Comparison / Decision / Troubleshooting |
| Boundary | What to include vs. exclude |
| Constraints | Budget, team size, legacy stack, region, security |
| Core Focus | Cost, reliability, performance, maintainability |

---

## Phase 2: Domain Cognitive Map

Perform initial multi-angle searches and create/update Artifact with:

1. **One-Sentence Definition**: Core purpose of the domain.
2. **Knowledge Tree**: Structural breakdown of sub-domains or technology branches.
3. **Core Mechanism & Tension**: Identify the primary 1–2 tradeoffs (e.g., Performance vs. Cost, Flexibility vs. Safety) and how major paradigms choose their positioning.
4. **Key Variables vs. Marketing Noise**:
   - *Key Variables*: The <10 factors that actually determine success.
   - *Marketing Noise*: Flashy features with negligible practical impact.

---

## Phase 3: Evidence & Conflict Analysis

1. **Targeted Deep Retrieval**: Search for real-world failure cases, benchmark data, hidden costs, and edge cases.
2. **Conflict Resolution Table**: If sources disagree, do not force a verdict. Present the conflict:

| Issue | View A | View B | Key Evidence | Current Consensus |
|-------|--------|--------|--------------|-------------------|

3. **Information Scarcity**: If data is lacking, explicitly state "Insufficient verifiable evidence" and suggest alternative validation methods (e.g., vendor trial, hands-on benchmark).

---

## Phase 4: Option Matrix & Weighted Scoring

### 4.1 Comparison Matrix

| Factor | Option A | Option B | Option C |
|--------|----------|----------|----------|
| Overview | ... | ... | ... |
| Core Advantage | ... | ... | ... |
| Critical Flaw | Based on real cases | Based on real cases | Based on real cases |
| Hidden Costs | ... | ... | ... |
| Prerequisites | ... | ... | ... |
| Sources | [Link](URL) | [Link](URL) | [Link](URL) |

### 4.2 Transparent Weighted Scoring

1. **Weight Table**: Explicitly tag weight origins (**User-specified** / **Scenario-derived** / **Default**).
2. **Scoring Table**: Qualitative 1–5 scale per variable.

```markdown
Weighted Score = SUM(Score * Weight)
```

Users can request weight adjustments to dynamically recalculate scores without re-running searches.

---

## Phase 5: Decision Delivery

Output structured decision-support Artifact sections:
- **Verified Facts**: High-confidence takeaways.
- **Unresolved Ambiguities**: Gaps requiring hands-on testing.
- **Actionable Verification Plan**: Next steps to validate unresolved risks.
- **Conditional Decision Guidance**:
  - *If primary concern is X* → Option A is optimal because...
  - *If risk Y must be avoided* → Option B is safer because...
