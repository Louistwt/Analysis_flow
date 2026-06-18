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
- **Revenue: cc, FX flat — carry the 06b build forward as the revenue ENGINE.**
  Where drivers are quantifiable, the model's revenue line IS the bottom-up build
  (volume × price × share, per year from 06b), and group growth/CAGR is an OUTPUT —
  not a typed Y1→Y-end glide. The smooth glide is the FALLBACK only when drivers
  aren't disclosable. Either way: reconcile to the latest actual; take rate is an
  EXPLICIT input (flat/declining unless pricing power is evidenced); penetration
  sanity check. (Horizon + two-stage-terminal discipline still applies to the
  resulting path.)
- **Glide, not flat blocks**; group CAGR is an output; horizon ~10yr growth / ~5yr
  stable with a two-stage terminal; ground the fade endpoint both directions.
- **Capex % and D&A % are GLIDE inputs too, not flat** (start → terminal, like EBIT
  margin). A flat capex % gives a build-ahead name a *negative* EV. Capex glides DOWN
  from the build peak; D&A glides UP as the build comes into service.
- **Terminal EBIT margin is a MIX-WEIGHTED OUTPUT**, not a top-down number:
  Σ(segment margin × terminal weight), reconciled to history. Feed that into the
  margin input cell and show the build.
- **Earnings-quality decomposition.** Separate operating EBIT / fee income / net
  interest income / float income; do not capitalise different-durability streams
  at one terminal multiple.
- **Net cash:** single stripped t0 figure (strip settlement balances, customer
  funds, credit-book funding, regulatory capital), correct sign.

## Scenario construction (driver narrative — NOT uniform multipliers)
Build Bear / Base / Bull as three COHERENT stories about WHICH DRIVER(S) BREAK —
never base × 0.7 / 1.3 across every input. Output a **scenario-narrative table**
beside the per-input table: for each scenario give (a) a one-line narrative,
(b) the specific driver(s) that move and why, (c) "what has to be true." Within a
scenario, related drivers move TOGETHER (e.g. a demand-digestion Bear lowers volume
AND pricing AND lifts the discount rate — correlated, not independent dials). Each
broken driver should map to a falsifier (carried to /redteam and /verdict). A spread
made by flexing every input independently is mechanical, not a risk model.

## Build-ahead / capex-super-cycle (if /classify flagged 5b — see `framework/capex-supercycle-hybrids.md`)
- **Extend the explicit horizon to ~15yr (10 growth + 5 stable)** so the FCF recovery
  is captured explicitly; an 8+yr negative-FCF J-curve in a 10yr window dumps value
  into the terminal (fails methodology #7).
- **Owner earnings = OCF − maintenance capex**, alongside headline FCF. Maintenance
  capex is NOT current depreciation (it lags the build) — it RISES toward a higher
  AI-era steady state; do not revert to the pre-AI level.
- **Allocate the build-ahead capex to the engine that owns the backlog.** The SOTP
  *total* is robust to the split; the split only shifts value between engines — flag
  it as the #1 assumption.
- **WACC is the dominant swing** for a terminal-heavy name. Per-engine WACC + a
  sensitivity spanning the required-return debate (~8–11%); distinguish through-cycle
  beta from spot beta (spot is inflated by the AI run-up).

## Multi-engine / SOTP (only if /classify flagged ≥2 material engines)
- Value each engine on its own lens and **carry the split through to valuation** —
  do NOT collapse into one EBIT / WACC / terminal multiple. Output a SOTP table:
  per-engine value + the consolidated DCF as a cross-check. SOTP is primary.
  **Re-run the consolidated cross-check after ANY base revision — it goes stale silently.**
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
