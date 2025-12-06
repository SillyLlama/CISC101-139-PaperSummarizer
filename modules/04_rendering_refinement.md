# Module 4: Rendering & refinement

## Responsibilities
- **Final integrated summary:** Combine section summaries into a coherent whole under budget.
- **Variants:** Produce expert and lay summaries.
- **Table:** Generate section-by-section table with budgets, actual lengths, statuses.
- **Glossary:** Build mini-glossary of terms encountered in the paper.
- **Formatting:** Assemble outputs per required heading structure.

## Final integrated summary
- **Scope:** High-level narrative covering motivation, architecture, training, results, and conclusions.
- **Constraint:** Use only content from the paper; no external context.
- **Compression:** Prioritize main claims and results; avoid per-section duplication.

## Expert vs lay summaries
- **Expert summary:** Concise, method-centric; include key equations or parameter choices where necessary.
- **Lay summary:** Simplify terminology; explain concepts with analogies to computing fundamentals; remove dense formulae.

## Section-by-section table columns
- **Section name**
- **Budget**
- **Actual length**
- **Status** (ok/missing/short/empty)

## Mini-glossary entries
- **Term**
- **Concise definition** aligned with usage in the paper; no external claims.
- **Section where encountered** (optional)

## Pseudocode
- **Compose final integrated summary** by selecting key sentences from section outputs; compress under budget.
- **Generate expert summary** with technical details; ensure no duplication of final summary.
- **Generate lay summary** with simplified explanations.
- **Build table** from section registry.
- **Assemble glossary** from terms collected during Section Loop.
- **Emit Checks & Warnings** collected by Guardrails.
