---
description: Build the verified primary-financial spine from filings — FIRST sourcing step (primary-first)
---

**This runs BEFORE DeepResearch, not after it.** The issuer's hard financials are
the spine the whole model rests on, so they are extracted first, directly from the
filings — never back-filled from an aggregator narrative. Read `01-classification.md`
(for the engine list and the per-engine primitives that must be sourced).

The user has uploaded the issuer's own filings (annual report + consolidated
statements, latest interim, Pillar 3 if licensed) to NotebookLM and pasted the raw
answers into `04b-notebooklm-raw.md`. If that file is absent, first output the
**primary-extraction question set** for the user to run in NotebookLM — the
financial spine keyed to stage 1's drivers: income statement (revenue, operating
EBIT, D&A, net income), cash flow (OCF, capex split maintenance/growth if
disclosed, SBC), balance sheet (cash, debt, regulatory/restricted capital,
settlement balances), diluted share count + SBC dilution, the segment split, and —
per engine — the operating primitives (e.g. TPV + take rate; loan book, NIM, cost
of funds, cohort loss curves, capital ratios for a lender). Include one
**calibration figure** with a known page/note to test the source's text layer.

Delegate verification to the **`skeptic` subagent** — its job is to turn raw,
possibly-mangled RAG extraction into trustworthy inputs, not to trust it. Where a
US filing line is truncated, pull it from SEC XBRL (`data.sec.gov` companyconcept
API) and map by period start/end dates, not the fy tag.

Write `04c-primary-financials.md`:

1. **Calibration check first.** Confirm the calibration figure returned correct
   with the right citation. If NOT, STOP and say so: the source's text layer is
   corrupt (likely an obfuscated font) and nothing extracted is usable — recommend
   OCR or direct XBRL extraction.
2. **Reconciliation pass.** For every figure: absolute number, citation (document +
   page/note), and recompute any derived ratio from the raw inputs. A figure whose
   value doesn't tie to its own inputs, or whose cited page can't plausibly hold
   it, is a fabricated/mangled citation — tag `unsupported` and do NOT pass it
   forward, however authoritative the named source looks.
3. **Anomaly pass.** Apply the ±40% rule; flag and withhold likely data errors
   (e.g. an SBC line that contradicts headcount direction).
4. **Structured output** — one table in the financials shape:
   `Line | Period | Absolute (as reported) | Source: <doc>, p./note | Recomputed | Tag | Flag`
5. **Material-engine primitives are load-bearing, not optional.** If a lender
   engine was flagged, its cost of funds / NIM / cohort loss curves / funding mix /
   capital ratios must be sourced and reconciled like any swing input — flag a
   missing one explicitly (it blocks a clean grade), never silently omit it.
6. **Remaining gaps** — anything the filings + XBRL still can't source, appended to
   the run's disclosure-gap register (see CLAUDE.md) so the DeepResearch prompt and
   `/operating-drivers` know what still needs color or hand-OCR.

Only figures that pass reconciliation AND carry a real citation are tagged `hard`
and feed `/assumptions`. Everything else stays `soft`/`unsupported` and widens the
Bear–Bull spread rather than moving the Base case. This verified spine is
authoritative — the later DeepResearch report is cross-checked against it, not the
reverse.


---

## Quarterly series (added 2026-08-18) — required

Annual data hides the working-capital signals that matter most. In addition to the annual
spine, extract **five years of QUARTERLY** data:

- **Income statement, cash-flow statement and balance sheet**, per quarter, from 10-Q / 10-K /
  earnings releases. **Pull these from SEC XBRL `companyfacts` where the issuer files with the
  SEC** — exact, free, and not reconstructable-from-memory. Use NotebookLM only for non-SEC
  issuers. Never ask a model to "find these on the web".
- **Derived per quarter:** gross / EBIT / EBITDA / net / OCF / FCFF margins, capex-to-sales,
  **ROIC (methodology #31 definition, stated in full)**, and **DIO, DSO, DPO, CCC**.

The working-capital series is not decoration — inventory days and DSO together are the earliest
clean read on a demand turn (see `companies/Industry/Semiconductor/04d-verification-chains.md`
V1), and they exist only at quarterly frequency.
