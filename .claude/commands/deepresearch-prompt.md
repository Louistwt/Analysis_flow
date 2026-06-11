---
description: Write a lens-specific, source-disciplined DeepResearch prompt for Gemini
---

Read `01-classification.md`.

Write `02-dr-prompt.md`: a single, self-contained prompt the user pastes into
Gemini DeepResearch, tailored to the classification and lens from stage 1.

First, find the issuer's primary sources. Identify the company's investor-
relations page and the exact, most recent primary documents (annual report and
consolidated financial statements, interim/half-year or quarterly financial
statements, shareholder letters, and any regulatory disclosure such as a Pillar 3
report for licensed entities). Name those documents and their publication dates
in the prompt so Gemini cannot default to a stale period. State the reporting
standard (IFRS/US GAAP), currency, and reporting cadence.

The prompt you produce MUST open with these non-negotiable rules:

1. A figure is UNSUPPORTED by default; it is HARD only with a citation to the
   issuer's own document + reporting period + page/note. No citation = write
   "NOT FOUND IN PRIMARY SOURCE." Never substitute an aggregator value.
2. PRIMARY SOURCES ONLY for financial figures: the issuer's filings and
   statements. BAN as a cited source: stockanalysis.com, discountingcashflows.com,
   Digrin, macrotrends, simplywall.st, koyfin, investing.com, wisesheets, marketing
   blogs, broker/teaser decks, Wikipedia. These may be used ONLY to locate a
   primary document, never to source a number.
3. USE THE LATEST AVAILABLE PERIOD. If a more recent annual/interim report
   exists, use it; reporting an older year as "latest" is a failure.
4. ARITHMETIC RECONCILIATION: for every growth rate, margin, or ratio, show the
   two absolute figures it derives from and recompute it. State "as reported" and
   "as recomputed" side by side; flag mismatches. No rounding-then-asserting.
5. CONSISTENCY PASS: any metric contradicting another in the output = flag
   "CONTRADICTION," leave unresolved.
6. ANOMALY PASS: any YoY move beyond ±40% in a normally stable line (SBC, share
   count, margins) = flag "ANOMALY — verify; likely data error," never tag HARD.
7. Output format per figure:
   `Metric | Period | Absolute (as reported) | Source: <doc>, p./note | Recomputed | Tag | Flag`

Then tailor the body to the lens. Always require, with the rules above:
- Quality gate: moat (widening/narrowing, evidence); 10-yr capital allocation
  with specific buyback prices and M&A outcomes; ROIC trend with formula stated;
  balance sheet detail.
- The four DCF swing inputs, sourced properly:
  - Most recent reported operating profit / EBIT (from the income statement, not
    just headline EBITDA) and D&A, so terminal margin rests on a current actual.
  - WACC built from components — risk-free (which bond + date), ERP (source),
    beta (source, window, index); if debt-free, WACC ≈ cost of equity; show CAPM.
    Reject any single screen-scraped WACC.
  - Revenue / take-rate inputs recomputed from filings; treat any attribution of
    a change to a specific event as a hypothesis needing issuer confirmation;
    separate one-off from structural.
  - Net cash net of restricted cash, regulatory capital, and (for payments/
    financials) settlement balances. Distributable cash is not gross cash; use
    the latest dated balance sheet.
- For cash-flow-sensitive businesses, require OCF reconciled to net income with
  the driver named (e.g. working-capital or settlement-balance timing).
- If stage 1 flagged a LENDER engine, require its load-bearing primitives as
  first-class tables — treat a missing one like a missing TPV: blended cost of
  funds, NIM, vintage/cohort loss curves, funding mix, capital/leverage ratios,
  deposit base. If EM/hyperinflationary, require per-country real-vs-inflation
  splits, not just a group constant-currency number.
- The operating-driver time series from stage 1, as FIRST-CLASS TABLES (not
  prose): volume and price per period for 5+ years (e.g. TPV and take rate);
  the SAME primitive for named competitors (e.g. competitor TPV + growth);
  and penetration = player volume ÷ TAM. Competitor *volume* is mandatory, not
  just a qualitative landscape.
- Industry layers + where economics pool (feeds stage 5); strongest bear case;
  what the market may be pricing that bulls dismiss.

Output the prompt in one fenced block for easy copy. Keep it focused — a prompt
that asks for everything gets shallow answers on everything.

Outside the block, remind the user to paste Gemini's output into
`03-gemini-report.md` before running `/critique-report`.
