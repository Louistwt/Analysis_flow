---
description: Verify and structure primary-source figures pulled from NotebookLM
---

The user has run the NotebookLM questions from the worklist in `04-critique.md`
(Part B) and pasted the raw answers into `04b-notebooklm-raw.md`. Read both.

Delegate verification to the **`skeptic` subagent**. Its job is to turn raw,
possibly-mangled RAG extraction into trustworthy inputs — not to trust it.
NotebookLM gets the same scrutiny Gemini did.

Write `04c-primary-financials.md`:

1. **Calibration check first.** Confirm the calibration figure from the worklist
   came back correct with the right citation. If it did NOT, STOP and say so:
   the uploaded source's text layer is corrupt (likely an obfuscated font) and
   nothing extracted from it is usable — recommend OCR or direct extraction
   instead.
2. **Reconciliation pass.** For every figure: absolute number, citation
   (document + page/note), and recompute any derived ratio from the raw inputs.
   A figure whose value does not tie to its own inputs, or whose cited page can't
   plausibly hold it, is a fabricated or mangled citation — tag `unsupported` and
   do NOT pass it forward, however authoritative the named source looks.
3. **Anomaly pass.** Apply the ±40% rule; flag and withhold likely data errors
   (e.g. an SBC line that contradicts headcount direction).
4. **Structured output** — one table in the financials shape:
   `Line | Period | Absolute (as reported) | Source: <doc>, p./note | Recomputed | Tag | Flag`
5. **Remaining gaps** — anything NotebookLM still could not source, so the user
   knows what to OCR by hand or send for direct extraction.

Only figures that pass reconciliation AND carry a real citation may be tagged
`hard` and feed `/assumptions`. Everything else stays `soft`/`unsupported` and
widens the Bear–Bull spread rather than moving the Base case.