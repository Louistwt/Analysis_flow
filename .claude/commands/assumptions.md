---
description: Convert findings into bear/base/bull DCF assumptions for the Sheet
---

Read `framework/methodology-checks.md`, `04-critique.md`, `04c-primary-financials.md`
(reconciled hard data — backbone of the inputs), `05-industry-map.md`, `06-tech.md`,
and `06b-growth-decomposition.md` (the volume × price × penetration build).

Produce `07-assumptions.md`: the bear/base/bull input block matching the refined
DCF input schema below, ready to paste into the Sheet's blue cells.

## Input schema (matches the refined glide-based tab)

Per scenario (Bear / Base / Bull), each cell with justification + source + tag:
- Starting revenue (Y0)
- Revenue growth — Y1
- Revenue growth — Y-end (glide endpoint)
- EBIT margin — start (Y1)
- EBIT margin — terminal (Y-end)
- D&A as % of revenue
- Capex as % of revenue
- Change in WC as % of Δrevenue
- Tax rate
- WACC
- Terminal growth rate (≤ long-run nominal GDP)

Single, SAME across all scenarios (do not flex by scenario):
- Net cash (t0, stripped of settlement balances + regulatory capital)
- Diluted shares (reconciled)
- Current price (for the upside check)

Model structure:
- Explicit horizon: ~10yr growth / ~5yr stable (by classification). Bridge
  any residual runway with a two-stage terminal, not a longer window.

## Core rules

- Only `hard` inputs move the Base case. Soft/unsupported uncertainty widens the
  Bear–Bull spread, never moves Base. Anchor current-actuals on
  `04c-primary-financials.md`; never invent a figure that is still soft there.

## Methodology rules (these dominate — see methodology-checks.md)

- **Revenue: constant-currency, FX flat.** Grow the actual base at the cc rate;
  never project reported growth.
- **Glide, not flat blocks.** Growth interpolates from the Y1 input to the Y-end
  input; group CAGR is an OUTPUT you read, not an input you type. Where segment
  data exists, glide Digital / Unified Commerce / Platforms separately and sum.
- **Reconcile the CAGR to volume × price × penetration.** Build revenue growth from
  the 06b decomposition: implied volume growth × take-rate path. Take rate is an
  EXPLICIT input (flat/declining unless pricing power is evidenced, not a mix
  effect). Penetration sanity check: does implied cumulative volume keep the company
  below saturation vs TAM and vs where peers decelerated? If not, volume growth is
  too high. A CAGR not reconciled to the primitives is an assertion, not an estimate.
- **Match the horizon to company type (standard).** ~10yr explicit for a growth
  company, ~5yr for a stable one, per the stage-1 classification. Do NOT extend
  the window. If final-year growth is still well above the perpetual rate, capture
  the remaining runway with a two-stage / H-model terminal — not a longer forecast
  and not by steepening the in-window fade. Ground the final-year growth to mature
  comparables; do not fade it to an ungrounded low.
- **Ground the fade endpoint, both directions.** Anchor Y-end growth to mature
  comparables (payment networks ~low-double-digit for years = generous ceiling;
  adjust down for Adyen-type acquirer economics/competition). A low Y-end or bear
  CAGR needs evidence of deterioration — do not impose ungrounded deceleration.
- **Y-end ≠ terminal.** Y-end growth can stay well above GDP; terminal perpetual
  rate must be ≤ nominal GDP. Note the implied terminal exit multiple for the
  verdict gate.
- **Net cash:** single stripped t0 figure, identical across scenarios; correct
  sign (added for net cash). **SBC:** confirm whether it is already in EBIT (then
  no add-back/dilution) or needs modelling.

## Output layout

```
| Input | Bear | Base | Bull | Justification + source | Reliability |
|-------|------|------|------|------------------------|-------------|
```
Then: explicit horizon chosen (+ why); single net cash / shares / price block;
**spread rationale** (what drives Bear↔Bull — the risk statement); the four swing
inputs flagged for the red team (Y1 growth, Y-end growth, terminal EBIT margin,
WACC); open questions / remaining gaps.

Do not compute fair value — the Sheet does that. Treat Base as an indicative
hypothesis, never an answer.