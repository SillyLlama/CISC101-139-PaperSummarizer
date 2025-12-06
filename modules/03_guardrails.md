# Module 3: Guardrails

## Responsibilities
- **Hallucination mitigation:** Ensure summaries contain only content in the section text.
- **Warnings:** Emit messages for missing/empty/short sections.
- **Length enforcement:** Hard cap on per-section and final summaries.
- **Order preservation:** Summaries must follow the original section order.

## Techniques
- **Source-only constraint:** No external facts or interpretations beyond the paper.
- **Claim tracing:** Retain internal references to paragraphs or equations to avoid drift.
- **Numeric fidelity:** Preserve exact numbers and named datasets as stated.
- **Redundancy pruning:** Avoid repeating the same conclusion in multiple outputs.

## Long-paper handling
- **Chunk and aggregate** with no cross-section blending.
- **No semantic merging** unless user explicitly requests merging.

## Pseudocode
- **Validate inputs:** Required items present.
- **Run checks:**
  - Missing sections → add to warnings.
  - Empty/short sections → add to warnings.
- **Apply caps:** Truncate with ellipses only if unavoidable; prefer compression over truncation.
- **Final audit:** Ensure every sentence adds new value; remove repetitive phrasing.
