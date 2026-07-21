---
name: decision-lens
description: Deep domain research and decision support framework. Activates when the user requests tech stack selection, product comparison, industry research, or systematic trade-off analysis. Features dynamic source discovery, hard constraint filtering, endnote citations, and transparent weighted scoring.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: Construct domain maps, perform broad candidate scanning, dynamically discover query-specific reliable sources, enforce hard constraint filtering, collect web evidence with endnote citations, compile option matrices, build transparent weighted scoring matrices, and provide deep-dive technical cards.
- **Non-Goal**: AI does NOT dictate the "best" choice or make value judgments for the user. If the user explicitly asks for a recommendation, provide a guarded suggestion clearly labeled as *"tentative preference based on current evidence"*.
- **Language Output**: Output user-facing messages and Artifacts in the user's preferred language (default to Chinese when communicating with Chinese users).

---

## Strict Rules

1. **Hard Constraint Filtering (一票否决机制)**: Explicitly separate **Hard Constraints** (mandatory requirements like "must be a standalone desktop app") from **Soft Preferences** (weighted evaluation factors). Any candidate failing a Hard Constraint MUST be immediately eliminated during screening and cannot occupy a slot in the primary comparison matrix.
2. **Broad & Multi-Source Scanning**:
   - Do NOT rely on 1–2 surface-level web searches.
   - Perform broad scans using GitHub Topics (e.g. `topic:ai-agent`), Awesome Lists (e.g. `awesome-ai-agents`), and community roundups.
   - Build an initial candidate pool of at least 6–8 options before filtering down to the Top candidates for deep comparison.
3. **Dynamic Source Discovery & User Choice (动态信源探索与用户裁决规程)**:
   - Avoid hardcoded static source templates. During initial scanning, dynamically discover 3–5 of the most reliable and active platforms/communities specific to the user's query topic (e.g. PubMed/IEEE for academic research, GitHub/StackOverflow for dev tools, Bilibili/Xiaohongshu for hardware testing).
   - In Phase 1, present the discovered sources with justification to the user: *"Here are the most reliable sources discovered for your query: [Source A (Reason), Source B (Reason)...]. Would you like to confirm, remove any sources, or add specific platforms?"*
   - Strictly restrict Phase 3 deep retrieval to the user-approved source boundaries.
4. **Endnote Citation System (角标/尾注引用系统)**:
   - Attach superscript citations `[^1]`, `[^2]` (or `[1]`, `[2]`) to all key claims, project features, metrics, and data points throughout the text—not just inside tables.
   - Compile all numbered references at the end of the document in a dedicated `## References` section with full URLs, source names, and context.
   - Never invent citations. Unverified claims MUST be explicitly tagged as `[Unverified]`.
5. **Interactive Parameter & Weight Locking**:
   - At Phase 1, present extracted Hard Constraints, Key Variables, and proposed Weights alongside the Discovered Sources to the user.
   - Prompt the user for confirmation or adjustments before proceeding to Phase 3 deep retrieval.
6. **Detailed Deep-Dive Cards**: Provide technical cards for all primary candidates surviving Hard Filtering, covering installation dependencies, custom/free API configuration steps (e.g., DeepSeek/SiliconFlow/Ollama), multi-agent mechanics, and community maintenance status.
7. **Artifact as Primary Medium**: Create `domain_research_<topic>.md` as a living report and append updates across workflow phases. Chat output must remain concise summaries and decision prompts.
8. **Score Honesty**: Use qualitative integers (1–5 scale). Avoid misleading decimal precision.

---

## Workflow Phases

### Phase 1: Research Scope, Source Discovery & Parameter Locking
1. Extract **Hard Constraints** (mandatory criteria) and **Soft Preferences** (evaluation metrics).
2. Perform initial broad scanning to dynamically discover 3–5 top reliable platforms/sources for this specific query.
3. Present the Hard Constraints, Key Variables (<10 factors), proposed Weights, and Discovered Sources to the user.
4. Prompt the user to confirm or adjust weights and source boundaries before proceeding.

### Phase 2: Candidate Pool & Domain Cognitive Map
1. Gather an initial pool of 6–8 candidate options.
2. Apply Hard Constraint Filtering to eliminate ineligible options (list eliminated options and reasons briefly).
3. Construct the Domain Map (Knowledge Tree, Core Tension Model, Key Variables vs Marketing Noise) in the Artifact. Attach inline superscripts `[^1]` for all factual assertions.

### Phase 3: Targeted Deep-Dive & Conflict Analysis
1. Perform targeted retrieval for eligible candidates strictly within the user-approved source boundaries.
2. Structure conflicting claims, edge cases, and hidden costs into a Conflict Resolution Table.
3. Create a **Deep-Dive Specification Card** for each core candidate.

### Phase 4: Option Matrix & Transparent Scoring Matrix
1. Construct the Option Comparison Matrix.
2. Construct the Transparent Weight Table (origin: *User-specified*, *Scenario-derived*, *Default*).
3. Build the Qualitative 1–5 Weighted Scoring Matrix.

### Phase 5: Decision Delivery & Reference List
1. Output Verified Facts, Unresolved Ambiguities, and Actionable Verification Plans.
2. Provide Conditional Decision Guidance (e.g., "If priority is X → Option A").
3. Append the full **Numbered References List** (`## References`) at the very end of the document, mapping every superscript `[^N]` to its full URL and description.
