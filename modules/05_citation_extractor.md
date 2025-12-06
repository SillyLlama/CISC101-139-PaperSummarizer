# Module 5: Citation extractor

## Responsibilities
- **In-text references:** Identify references cited (e.g., [1], [2]) within the body.
- **Bibliography linkage:** Map in-text references to entries in the References section of the paper.
- **Output:** List of cited references with bibliographic info as presented in the paper.

## Inputs
- **Paper text:** Full body and references section.

## Outputs
- **Cited references list:** Items, each with index, authors, title, venue/year (as available in the paper), and any identifiers present (e.g., arXiv).

## Extraction approach
- **Regex match:** Patterns like “[n]” or parenthetical numeric citations.
- **Scope:** Collect unique indices; then parse References section for matching entries.
- **No external augmentation:** Do not add missing fields not present in the paper.

## Pseudocode
- **Scan body** for citation tokens.
- **Deduplicate** indices preserving first-seen order.
- **Parse References** into (index → entry) map.
- **Emit list** in order of first appearance in body.
