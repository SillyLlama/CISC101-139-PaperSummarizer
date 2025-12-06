# Module 3: Guardrails

# Change Log (2025-12-05)
- Added evidence_mode variable ("standard" | "strict").
- Added strict-evidence rules: summaries must only include claims explicitly present.
- Added standardized warning messages for missing/empty/short sections (<50 words).
- Strengthened hallucination constraints and numeric fidelity checks.
- Integrated evidence-mode logic into pseudocode while preserving original structure.


## Responsibilities
- **Hallucination mitigation:** Ensure summaries contain only content in the section text.
- **Evidence enforcement:** In strict mode, include only claims directly verified in the source.
- **Warnings:** Emit standardized messages for missing, empty, or short sections.
- **Length enforcement:** Hard cap on per-section and final summaries.
- **Order preservation:** Summaries must follow the original section order.

## Variables
- **evidence_mode:** "standard" or "strict".

## Techniques
- **Source-only constraint:** No external facts or interpretations beyond the paper.
- **Strict evidence rule:**  
  - If evidence_mode == "strict":  
    * Reject claims without direct textual support.  
    * If insufficient evidence is available, emit:  
      _"The source text does not provide enough detail to summarize this section in strict evidence mode."_  
- **Claim tracing:** Retain internal references to paragraphs or equations to avoid drift.
- **Numeric fidelity:** Preserve exact numbers, metrics, and dataset names as stated.
- **Redundancy pruning:** Avoid repeating the same conclusion in multiple outputs.

## Warning messages (standardized)
- **Missing section:**  
  _"Section skipped: no usable text was provided."_  
- **Empty or figure-only section:**  
  _"Section contains no meaningful text; summary cannot be produced."_  
- **Short section (<50 words):**  
  _"Section very short: summary may be incomplete."_


## Long-paper handling
- **Chunk and aggregate** with no cross-section blending.
- **No semantic merging** unless user explicitly requests merging.

## Pseudocode
- **Validate inputs:** Ensure paper text, section registry, and configuration are present.
- **Run checks:**
  - If section missing → attach missing-section warning.
  - If section empty/figure-only → attach empty-section warning.
  - If section < 50 words → attach short-section warning.
- **If evidence_mode == "strict":**
  - Disallow any claim not directly grounded in source text.
  - If insufficient evidence → return strict-evidence warning.
- **Apply caps:** Truncate with ellipses only if unavoidable; prefer structured compression over truncation.
- **Final audit:**  
  - Ensure every sentence adds new value.  
  - Remove repetitive phrasing.  
  - Confirm all claims trace cleanly to the original section content.
