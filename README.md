# Research Paper Summarizer system

## Overview
This repository implements a constrained summarization system for academic papers with clearly labeled sections. It produces per-section summaries, a final integrated summary, expert and lay variants, a section-by-section table, a mini-glossary, checks & warnings, extracted citations, and key contributions. The system is designed to summarize the NeurIPS 2017 paper “Attention Is All You Need” by Vaswani et al. for a computing undergraduate audience, using only the content within the paper itself.

## What you provide
- **Paper:** Full text with clearly labeled sections (e.g., Abstract, Introduction, Model, Training, Results, Conclusion, References).
- **Section list:** The ordered list of sections you want summarized.
- **Audience:** Must include “computing undergraduate.”
- **Length constraints:**
  - Per-section max length (words or characters).
  - Final integrated summary max length.

## What you get
- **Paper summary:** A concise, whole-paper overview aligned to your audience.
- **Section-by-section table:** Budget vs actual length, and status (ok/missing/short/empty).
- **Expert summary + lay summary:** Two calibrated variants of the final summary.
- **Mini-glossary:** Short definitions of key terms encountered in the text.
- **Checks & warnings:** Missing or empty sections, normalization notes.
- **Citation extractor:** List of references cited in the text and their bibliographic entries.
- **Key contributions:** 3–5 main contributions strictly supported by the paper.

## Architecture
- **Module 1: Intake & setup:** Normalizes sections, validates audience, detects missing/short/empty sections.
- **Module 2: Section loop:** Summarizes each section in original order, enforcing length caps and source-only constraints.
- **Module 3: Guardrails:** Hallucination mitigation, warnings, long-paper chunking, length enforcement.
- **Module 4: Rendering & refinement:** Final integrated summary; expert and lay variants; table; glossary; checks & warnings.
- **Module 5: Citation extractor:** Parses in-text citations and maps to the References section.
- **Module 6: Key contributions summarizer:** Highlights 3–5 core contributions.

## Usage
- **Step 1:** Provide the paper text, the ordered section list, the audience (including “computing undergraduate”), and length constraints.
- **Step 2:** The system normalizes and validates sections; if mismatches occur, it will present a normalization table and request confirmation.
- **Step 3:** Summaries are generated per section, followed by the final integrated summary and required outputs.
- **Step 4:** Review checks & warnings for any missing or short sections.

## Constraints and guarantees
- **Source-only:** No external claims or invented citations; all content derives from the paper.
- **Length-aware:** Summaries respect maximum lengths via compression and prioritization.
- **Order-preserving:** Section summaries follow the original order of sections.
- **Audience-targeted:** Clear, undergraduate-accessible explanations with a mini-glossary.

## Notes on the paper
- **Title:** Attention Is All You Need
- **Venue:** NeurIPS 2017
- **Core idea:** Transformer architecture relying solely on self-attention, improving parallelization and translation performance.

> Sources: 
