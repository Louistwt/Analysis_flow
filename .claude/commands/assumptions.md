---
description: Convert findings into bear/base/bull DCF assumptions (+ SOTP for hybrids)
---

Read `framework/methodology-checks.md`, `04-critique.md`, `04c-primary-financials.md`,
`05-industry-map.md`, `06-operating-drivers.md`, and `01-classification.md` (for the
engine list, per-engine valuation basis, and per-engine discount-rate method).

Produce `07-assumptions.md`: the bear/base/bull inputs for the glide-based tab,
plus — for a multi-engine name — the SOTP build.

## Core rules
- Only `hard` inputs move the Base case; soft/unsupported widen the spread.
  Anchor current-actuals on `04c`; never invent a soft figure.
- **The Base is the EXPECTED / most-likely path, not a conservative one** (CLAUDE.md
  Prime Directive 1). Credit demonstrated durable performance; fade only where
  penetration, mean-reversion, or specific evidence warrants — as willing to hold
  strength as to assume weakness. Conservatism belongs in the Bear and the
  margin-of-safety, NOT baked into the Base. If the Base sits below the company's
  demonstrated trajectory with no deterioration evidence, that is the same error as
  an ungrounded bull (methodology #4).
- **Evidence-source consistency.** Treat a given evidence source the same way
  across every input. If you credit management's operating-leverage record to expand
  the *margin*, you must credit the same record to hold *growth* — do not discount
  guidance on one axis while leaning on it for another. Pick the optimistic corner
  on every input independently and you have manufactured a bear labelled "Base."
  **This applies to challenges from the analyst-user too:** when a revision is
  proposed (up *or* down), test it against the evidence — credit it if grounded,
  refuse it if not. A strong quarter is a reason to raise *growth* on evidence, not
  a licence to bump an EBIT margin toward the EBITDA headline (#27). Be the third
  party to the user's nudge, not only to the prior model.

## Methodology rules (see methodology-checks.md)
- **Revenue: cc, FX flat — carry the 06 build forward as the revenue ENGINE.**
  Where drivers are quantifiable, the model's revenue line IS the bottom-up build
  (volume × price × share, per year from 06), and group growth/CAGR is an OUTPUT —
  not a typed Y1→Y-end glide. The smooth glide is the FALLBACK only when drivers
  aren't disclosable. Either way: reconcile to the latest actual; take rate is an
  EXPLICIT input (flat/declining unless pricing power is evidenced); penetration
  sanity check. (Horizon + two-stage-terminal discipline still applies to the
  resulting path.)
- **Two-stage growth, not a single linear fade from Y1** (methodology #3): Stage 1
  (Y1–5) holds near the Y1 rate / fades gently — a compounder with runway does not
  decay on day one; Stage 2 (Y6–10) does the mature fade toward terminal. A straight
  Y1→Y10 glide under-states a growth-stage name. Group CAGR is an output; ground the
  fade endpoints both directions; two-stage terminal beyond the window.
- **EBIT vs EBITDA — label the line and never mix (methodology #27).** The margin
  inputs are **EBIT**; do not bump them toward an EBITDA headline (Adyen 53% EBITDA
  vs 47% EBIT) — that double-counts D&A. Compare an EBIT input to reported EBIT only.
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

## Discount-rate method + cost-of-capital contract (methodology #18–#19)
- **Use the method `/classify` selected (item 2b) — do not default to WACC.** The
  discount rate must match the cash-flow definition: **FCFF → WACC** (then −net
  debt), **FCFE → cost of equity** (equity directly, NO net-debt bridge),
  **residual income / justified P/B = (ROE − g)/(CoE − g)** for a financial, or
  **APV** (unlevered value + PV of tax shields − distress) when the capital
  structure changes materially over the horizon. A hybrid carries a different rate
  per engine — never one blended WACC over a lender + commerce mix.
- **Build the rate from named components, per scenario where it flexes:** risk-free
  (which bond + date, in the cash-flow currency), ERP (source, e.g. Damodaran),
  beta (source + window + index; **through-cycle**, not a run-up-inflated spot;
  unlever/relever if leverage differs from peers), value-weighted CRP for EM. No
  screen-scraped WACC. State the ERP and beta explicitly — they are red-team inputs.
- **NOPAT, not EBIT.** The revenue×margin build feeds an explicit
  **NOPAT = operating-EBIT × (1 − cash tax rate)** line. Build it on *operating*
  EBIT only (non-operating fee/interest/float income is valued separately per the
  earnings-quality rule). **Tax is a GLIDE input** — current-effective → normalised
  marginal cash rate — not a single cell.

## Returns & reinvestment consistency (methodology #21–#22)
- **Tie growth to reinvestment and ROIC.** g ≈ reinvestment rate × ROIC — the
  growth path and the capex + ΔWC + M&A path are not independent. Show the ROIC the
  modelled reinvestment implies and reconcile it to the assumed growth; flag free
  growth (implied ROIC absurd) or under-funded growth.
- **Value-creation check.** Where incremental ROIC ≤ the discount rate, growth
  earns no premium (cash cow, not compounder). Fade incremental ROIC toward the
  discount rate in the terminal (methodology #24).
- **Serial acquirer → M&A is reinvestment (methodology #28).** If the company grows
  by frequent acquisition, put acquisition spend in the capex/reinvestment line —
  the bought revenue and its D&A/amortisation are already in the P&L, so gliding
  capex down while growth is acquisition-funded manufactures free FCF. Fold M&A into
  the reinvestment↔ROIC↔growth tie.

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
- **The discount rate is the dominant swing** for a terminal-heavy name. Per-engine
  WACC + a sensitivity spanning the required-return debate (~8–11%); distinguish
  through-cycle beta from spot beta (spot is inflated by the AI run-up). If the
  build is debt-funded and the name **deleverages** across the window, prefer **APV**
  (unlevered value + PV of tax shields) — constant-weight WACC misprices a changing
  capital structure (methodology #18).

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
inputs for the red team (Y1 growth, Y-end growth, terminal EBIT margin, discount
rate). Append any remaining gaps to the run's disclosure-gap register
(`_open-questions.md`), not a standalone list.

Do not compute fair value — the Sheet does that. Treat Base as an indicative
hypothesis, never an answer.


---

## Added 2026-08-18

### ★ Discount rate — component-built reasoning, SWEPT presentation, per engine (methodology #34)
Keep the component build (Rf + ERP + through-cycle beta, method matched to the cash-flow
definition) as the **reasoning** step — it forces the question of *why* this return is required.
But **output a sensitivity sweep, default 8 / 9 / 10 / 11 / 12%**, and **state where in that range
the component build lands and why**. A single point rate is false precision; beta is noisy and
backward-looking.

**For a multi-engine hybrid, sweep EACH ENGINE SEPARATELY.** One blended sweep across engines of
different risk destroys the per-engine distinction that is the point of the SOTP — a contracted
software annuity and a programme-concentrated hardware business cannot share a rate. Terminal
growth stays ≤ long-run nominal GDP, held consistent across the sweep.

### ★ Two DCFs — reported capex and maintenance capex (methodology #32)
Produce the model **twice**:
1. **Reported capex** — as disclosed.
2. **Maintenance capex** — the Greenblatt approach: the capex needed to sustain current unit
   volumes and competitive position, with growth capex stripped out.

**The gap between the two valuations IS the growth investment.** Report it explicitly and
reconcile it to the reinvestment ↔ ROIC ↔ growth tie: if the model forecasts growth that the
maintenance-capex version shows is not being funded, that growth is unsupported and must come
out. For a serial acquirer, acquisition spend sits in the growth half (methodology #28).

### Model artifact
Output the markdown assumptions contract **and**, where the run is proceeding to a decision,
build the live spreadsheet (see the `gsheet-model-build` memory) with adjustable inputs and the
discount-rate sensitivity grid. Markdown is the contract; the sheet is the model.
