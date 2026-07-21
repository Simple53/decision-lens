---
name: decision-lens
description: Deep domain research and decision support framework. Activates when the user requests tech stack selection, product comparison, industry research, or systematic trade-off analysis. Features dynamic source discovery, hard constraint filtering, clean endnote citations, and transparent weighted scoring.
---

# Decision Lens Workflow

## Core Philosophy

- **AI Role**: Construct domain maps, perform broad candidate scanning, dynamically discover query-specific reliable sources, enforce hard constraint filtering, pause for interactive user approval via question tools, collect web evidence with clean endnote citations, compile option matrices, build transparent weighted scoring matrices, and provide deep-dive technical cards.
- **Non-Goal**: AI does NOT dictate the "best" choice or make value judgments for the user. If the user explicitly asks for a recommendation, provide a guarded suggestion clearly labeled as *"tentative preference based on current evidence"*.
- **Language Output**: Output user-facing messages and Artifacts in the user's preferred language (default to Chinese when communicating with Chinese users).

---

## Strict Rules

1. **Hard Constraint Filtering (一票否决与静默剔除)**:
   - Explicitly separate **Hard Constraints** (mandatory requirements like "must be a standalone desktop app") from **Soft Preferences** (weighted evaluation factors).
   - Any candidate failing a Hard Constraint MUST be immediately eliminated.
   - **Do NOT list eliminated candidates in comparison tables or matrices.** Simply state a single summary line in the report: *"Excluded N candidates that failed the Hard Constraints."*
2. **Broad & Multi-Source Scanning**:
   - Do NOT rely on 1–2 surface-level web searches.
   - Perform broad scans using GitHub Topics (e.g. `topic:ai-agent`), Awesome Lists (e.g. `awesome-ai-agents`), and community roundups.
   - Build an initial candidate pool of at least 6–8 options before filtering down to the eligible Top candidates for deep comparison.
3. **Dynamic Source Discovery & User Choice (动态信源探索与用户裁决规程)**:
   - Avoid hardcoded static source templates. During initial scanning, dynamically discover 3–5 of the most reliable and active platforms/communities specific to the user's query topic.
   - Present the discovered sources with justification to the user during Phase 1.
   - Strictly restrict Phase 3 deep retrieval to the user-approved source boundaries.
4. **Mandatory Interactive Pause (强制暂停等待用户确认)**:
   - At Phase 1, the AI MUST invoke the system's `ask_question` tool (or pause execution) to present the extracted Hard Constraints, Key Variables, Weights, and Discovered Sources.
   - Do NOT proceed to Phase 3/4 until the user explicitly responds or confirms via the interactive interface.
5. **Clean Endnote Citation System (标准尾注与有效超链接)**:
   - Attach inline superscripts `[^1]`, `[^2]` to all key claims, project features, metrics, and data points.
   - At the end of the document, list all references in a dedicated `## References` section using standard markdown footnote syntax (NO leading dashes):
     ```markdown
     [^1]: [Source Title](https://valid-url.com) - Context description
     [^2]: [Source Title](https://valid-url.com) - Context description
     ```
   - All URLs MUST be valid, clickable HTTP/HTTPS web links `[Title](https://...)`. Never invent fake URLs.
6. **No Decorative Note Callouts**:
   - Do NOT include `> [!NOTE]` or decorative callout blocks in the generated Artifact report.
7. **Detailed Deep-Dive Cards**: Provide technical cards for eligible primary candidates surviving Hard Filtering, covering installation dependencies, custom/free API configuration steps (e.g., DeepSeek/SiliconFlow/Ollama), multi-agent mechanics, and community maintenance status.
8. **Artifact as Primary Medium**: Create `domain_research_<topic>.md` as a living report and append updates across workflow phases. Chat output must remain concise summaries and decision prompts.
9. **Score Honesty**: Use qualitative integers (1–5 scale). Avoid misleading decimal precision.

---

## Workflow Phases

### Phase 1: Research Scope, Source Discovery & Parameter Locking
1. Extract **Hard Constraints** (mandatory criteria) and **Soft Preferences** (evaluation metrics).
2. Perform initial broad scanning to dynamically discover 3–5 top reliable platforms/sources for this specific query.
3. **MUST Call `ask_question` / Pause Execution**: Present the Hard Constraints, Key Variables (<10 factors), proposed Weights, and Discovered Sources.
4. Wait for the user to confirm or adjust parameters via the interactive UI before proceeding.

### Phase 2: Candidate Pool & Domain Cognitive Map
1. Gather an initial pool of 6–8 candidate options.
2. Apply Hard Constraint Filtering to silently eliminate ineligible options (do NOT put them in comparison tables).
3. Construct the Domain Map (Knowledge Tree, Core Tension Model, Key Variables vs Marketing Noise) in the Artifact. Attach inline superscripts `[^1]` for all factual assertions.

### Phase 3: Targeted Deep-Dive & Conflict Analysis
1. Perform targeted retrieval for eligible candidates strictly within the user-approved source boundaries.
2. Structure conflicting claims, edge cases, and hidden costs into a Conflict Resolution Table.
3. Create a **Deep-Dive Specification Card** for each core candidate.

### Phase 4: Option Matrix & Transparent Scoring Matrix
1. Construct the Option Comparison Matrix (containing ONLY candidates that passed Hard Constraints).
2. Construct the Transparent Weight Table (origin: *User-specified*, *Scenario-derived*, *Default*).
3. Build the Qualitative 1–5 Weighted Scoring Matrix.

### Phase 5: Decision Delivery & Reference List
1. Output Verified Facts, Unresolved Ambiguities, and Actionable Verification Plans.
2. Provide Conditional Decision Guidance (e.g., "If priority is X → Option A").
3. Append the full **Numbered References List** (`## References`) at the very end of the document, mapping every superscript `[^N]` to its full valid web link.
