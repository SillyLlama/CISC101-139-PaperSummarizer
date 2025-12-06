# Module 2: Section loop

## Responsibilities
- **Summarization:** Produce concise summaries for each section in original order.
- **Budget enforcement:** Cut or compress to meet max length.
- **Integrity:** Use only material from the section; retain key equations and numeric results.

## Inputs
- **Section registry:** Text, offsets, budget, status.
- **Paper text:** For local chunking of long sections.

## Outputs
- **Section summaries:** One per section, respecting order and budget.
- **Metrics:** Actual length vs budget for table display.

## Summarization priorities
- **Core elements:** Problem setting, methods, architecture, equations, training setup, datasets, metrics, results, ablations, conclusions.
- **Preservation:** Keep explicit numeric claims and formulae as needed for clarity.
- **Audience tuning:** Accessible phrasing suitable for computing undergraduates.

## Chunking strategy (for long sections)
- **Chunk by paragraphs/subheadings.**
- **Local summarize per chunk (micro-summaries).**
- **Aggregate:** Combine micro-summaries, remove redundancy, preserve chronology.
- **Trim:** If over budget, remove lower-priority details (implementation minutiae) before key claims.

## Pseudocode
- **For each section in order:**
  - If missing: produce placeholder summary “Missing; not present in provided text.”
  - If empty/short: produce minimal summary “Content unavailable or figure-only.”
  - Else:
    - If length > threshold: apply chunking pipeline.
    - Extract key sentences/claims verbatim or paraphrased.
    - Compose concise summary within budget.
  - Record actual length.
