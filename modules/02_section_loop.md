# Module 2: Section loop

# Change Log (2025-12-05)
 - Added summary_level variable (“short” | “detailed”).
 - Added conditional behaviors:
 - Short mode → 1–2 sentence summary only.
 - Detailed mode → short paragraph + 3–5 bullet points.
 - Integrated summary-level logic into pseudocode and summarization responsibilities.

## Responsibilities
- **Summarization:** Produce concise summaries for each section in original order.
- **Budget enforcement:** Cut or compress to meet max length.
- **Integrity:** Use only material from the section; retain key equations and numeric results.
- - **Summary-level control:**  
  - summary_level = "short" → compact 1–2 sentence summary.  
  - summary_level = "detailed" → short paragraph + bullet list (3–5 points).

## Inputs
- **Section registry:** Text, offsets, budget, status.
- **Paper text:** For local chunking of long sections.
- - **summary_level:** "short" or "detailed", controlling output depth.

## Outputs
- **Section summaries:** One per section, respecting order and budget.
- **Metrics:** Actual length vs budget for table display.

## Summarization priorities
- **Core elements:** Problem setting, methods, architecture, equations, training setup, datasets, metrics, results, ablations, conclusions.
- **Preservation:** Keep explicit numeric claims and formulae as needed for clarity.
- **Audience tuning:** Accessible phrasing suitable for computing undergraduates.
- - **Mode behavior:**  
  - *Short mode:* Emphasize only the core idea + most essential result.  
  - *Detailed mode:* Provide fuller explanation plus bullet list capturing 3–5 key details directly supported by the text.

## Chunking strategy (for long sections)
- **Chunk by paragraphs/subheadings.**
- **Local summarize per chunk (micro-summaries).**
- **Aggregate:** Combine micro-summaries, remove redundancy, preserve chronology.
- **Trim:** If over budget, remove lower-priority details (implementation minutiae) before key claims.

## Pseudocode
- **For each section in order:**
  - If missing:  
    → produce placeholder summary “Missing; not present in provided text.”
  - If empty/short:  
    → produce minimal summary “Content unavailable or figure-only.”
  - Else:
    - If length > threshold:  
      → apply chunking pipeline (chunk → micro-summarize → aggregate → trim).
    - Extract key sentences/claims (verbatim or paraphrased, within policy).
    
    - **If summary_level == "short":**
      • Produce **1–2 sentence** compact summary.  
      • Prioritize the main point of the section only.  
      • Must remain within section budget.

    - **If summary_level == "detailed":**
      • Produce a **short paragraph** capturing the section’s central ideas.  
      • Then generate a **bullet list of 3–5 key points** based strictly on section text.  
      • Bullets may include equations, numeric results, or architectural details if present.

  - Record actual length.
