---
description: Convert findings into bear/base/bull DCF assumptions (+ SOTP for hybrids)
---

Read `framework/methodology-checks.md`, `04-critique.md`, `04c-primary-financials.md`,
`05-industry-map.md`, `06-tech.md`, `06b-growth-decomposition.md`, and
`01-classification.md` (for the engine list and per-engine valuation basis).

Produce `07-assumptions.md`: the bear/base/bull inputs for the glide-based tab,
plus — for a multi-engine name — the SOTP build.

## Core rules
- Only `hard` inputs move the Base case; soft/unsupported widen the spread.
  Anchor current-actuals on `04c`; never invent a soft figure.

## Methodology rules (see methodology-checks.md)
- **Revenue: cc, FX flat.** Build from volume × price (06b); reconcile the CAGR to
  implied volume growth × take-rate path; take rate is an EXPLICIT input
  (flat/declining unless pricing power is evidenced); penetration sanity check.
- **Glide, not flat blocks**; group CAGR is an output; horizon ~10yr growth / ~5yr
  stable with a two-stage terminal; ground the fade endpoint both directions.
- **Terminal EBIT margin is a MIX-WEIGHTED OUTPUT**, not a top-down number:
  Σ(segment margin × terminal weight), reconciled to history. Feed that into the
  margin input cell and show the build.
- **Earnings-quality decomposition.** Separate operating EBIT / fee income / net
  interest income / float income; do not capitalise different-durability streams
  at one terminal multiple.
- **Net cash:** single stripped t0 figure (strip settlement balances, customer
  funds, credit-book funding, regulatory capital), correct sign.

## Multi-engine / SOTP (only if /classify flagged ≥2 material engines)
- Value each engine on its own lens and **carry the split through to valuation** —
  do NOT collapse into one EBIT / WACC / terminal multiple. Output a SOTP table:
  per-engine value + the consolidated DCF as a cross-check. SOTP is primary.
- **Lender engine is MANDATORY-separated.** Value on loan book × NIM ×
  cost-of-risk. Model the equity capital it consumes: distributable FCFE = net
  income − increase in required equity capital (to fund book growth at its capital
  ratio). Value via residual income or justified P/B = (ROE − g)/(CoE − g) at the
  **arm's own cost of equity**, not group WACC. Never capitalise the book as
  recurring revenue. Its load-bearing primitives (cost of funds, NIM, cohort loss
  curves, funding mix, capital ratios) must be `hard` or the value is caveated.

## EM / multi-country (only if flagged)
- Per-country real-volume-vs-inflation/FX decomposition (IAS 29 monetary
  gain/loss note for hyperinflation). Country-risk premium in WACC is
  value-weighted, not revenue-weighted.

## Output layout
Per-scenario input table (with justification + source + reliability tag); the SOTP
table if applicable; **spread rationale** (the risk statement); the four swing
inputs for the red team (Y1 growth, Y-end growth, terminal EBIT margin, WACC);
open questions / remaining gaps.

Do not compute fair value — the Sheet does that. Treat Base as an indicative
hypothesis, never an answer.
