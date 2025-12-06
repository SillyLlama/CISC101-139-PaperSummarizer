# Module 1: Intake & setup

## Responsibilities
- **Inputs normalization:** Align user-provided section list with headings in the paper.
- **Detection:** Identify missing sections, duplicate labels, and short/empty sections.
- **Budgets:** Store per-section and final summary max lengths (words or characters).
- **Audience check:** Verify target audience includes “computing undergraduate.”

## Inputs
- **Paper text:** Full content with labeled sections.
- **Section list:** Ordered list of section headings from the user.
- **Audience:** String descriptor.
- **Length constraints:** Per-section max and final integrated max.

## Outputs
- **Normalized sections:** Mapping from user headings to actual paper headings.
- **Section registry:** For each section: start/end offsets, text content, budget, status.
- **Diagnostics:** Missing sections, unmatched headings, short/empty sections.

## Normalization strategy
- **Exact match:** Case-insensitive match of headings.
- **Fuzzy fallback:** If exact match fails, search for nearest canonical phrases (e.g., “Abstract,” “Introduction,” “Model,” “Training,” “Results,” “Conclusion,” “References”).
- **User confirmation:** Present normalization table when fuzzy matches occur.

## Short/empty detection
- **Heuristics:**
  - **Empty:** No textual content beyond heading and whitespace.
  - **Short:** Below a minimal threshold (e.g., < 50 words) without figures/equations.

## Pseudocode
- **Initialize:** Validate audience contains “computing undergraduate”; else request clarification.
- **Parse headings:** Extract headings and offsets.
- **Normalize list:** For each user section, find matching paper heading.
- **Register budgets:** Attach max length per section and final summary cap.
- **Compute status:** Mark missing, short, empty.
- **Emit diagnostics:** For rendering by Module 4.
