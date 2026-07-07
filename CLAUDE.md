# CLAUDE.md — Equity Research Pipeline

You are operating inside a staged equity-research pipeline. Each slash command
is one stage. Read only the files a stage names, write only the file it names,
and stop. The human reviews between stages. Do not run ahead.

## Pipeline stages

| # | Command | Writes |
|---|---------|--------|
| 1 | /classify | 01-classification.md |
| 2 | /deepresearch-prompt | 02-dr-prompt.md |
| 3 | (run prompt in Gemini DeepResearch) | 03-gemini-report.md |
| 4 | /critique-report | 04-critique.md (audit + remediation worklist) |
| 4b | (run worklist in NotebookLM) | 04b-notebooklm-raw.md |
| 4c | /verify-primary | 04c-primary-financials.md |
| 5 | /industry-map | 05-industry-map.md |
| 6 | /tech-deepdive | 06-tech.md |
| 6b | /growth-decomposition | 06b-growth-decomposition.md |
| 7 | /assumptions | 07-assumptions.md |
| 8 | /redteam | 08-redteam.md |
| 9 | /verdict | 09-verdict.md (runs the methodology gate first) |

## Industry sub-track (survey, not valuation)

The stages above are a **valuation funnel** — they converge on one priced verdict
and need a named issuer (financials, net cash, shares, price). An **industry
review** is the opposite: a *divergent survey* that fans out across layers and
ends in a ranked shortlist of candidates, each of which then ENTERS the company
funnel at stage 1. Use this track when `00-brief.md` asks to decompose an
industry / find investable layers rather than to value one company.

| # | Command | Writes |
|---|---------|--------|
| 1 | /industry-classify | 01-classification.md (layers + player archetypes + value-capture question) |
| 2 | /industry-dr-prompt | 02-dr-prompt.md (industry-shaped DeepResearch prompt) |
| 3 | (run prompt in Gemini DeepResearch) | 03-gemini-report.md |
| 4 | /critique-report | 04-critique.md (reused unchanged — domain-agnostic) |
| 5 | /industry-layermap | 05-industry-map.md (ranks profit pools, keeps multiple layers live) |
| 6 | /tech-deepdive | 06-tech.md (reused — chokepoint layer's anchor is the "subject") |
| 7 | /industry-shortlist | 07-shortlist.md (ranked named candidates → hand-off to the company funnel) |

The track reuses `/critique-report` and `/tech-deepdive` as-is and leaves the
valuation funnel untouched. Its terminal output is NOT a verdict — it is a routing
artifact: each shortlisted name is copied into `companies/<TICKER>/`, seeded with
its entry lens, and run through `/classify` onward. **Cash-cow + optionality**
names (an existing profitable business funding the robotics/AI bet) go first —
they carry an SOTP valuation floor and so fail safer.

## Prime directives

1. **The Base case is indicative, never an answer.** A DCF output is a
   hypothesis that varies with assumptions. Risk is managed through the *width
   and reasoning* of the Bear–Bull spread, not a precise number. Never present a
   point estimate as a conclusion.
2. **Provenance with every number.** Each quantitative assumption cites where it
   came from (report section, filing, or explicit inference). No orphan numbers.
3. **Reliability tagging.** Tag every key input `hard` (sourced, recent,
   corroborated), `soft` (single source or estimate), or `unsupported`
   (asserted, no basis). Only `hard` inputs move the Base case. `soft` and
   `unsupported` widen the Bear–Bull spread instead.
4. **Quality before price.** A low valuation on a narrowing moat or poor capital
   allocation is a pass, not a bargain.
5. **Distinguish maintenance capex from growth capex.** Treat stock-based
   compensation as a real cost. Anchor on business performance, not share price.
6. **State uncertainty plainly.** If data is missing, say so. Never fabricate or
   interpolate to fill a section.
7. **Decompose growth into unit economics before setting a CAGR.** Build revenue
   from volume × price and validate it against penetration/capacity and named
   competitors. A CAGR not reconciled to volume × price × penetration is an
   assertion, not an estimate.

## The investment framework

**Quality gate (pass / conditional / fail) — applied before valuation:**
- Moat: which of switching costs / network effects / intangibles / cost
  advantage / efficient scale, and is it widening, stable, or narrowing?
- Capital allocation: 10-yr record of buybacks (at what prices?), M&A (returns
  vs promised), debt management. Best predictor of per-share value creation.
- Reinvestment runway: can incremental capital be deployed at high ROIC? A high
  ROIC that can't be reinvested is a cash cow, not a compounder.
- Balance sheet: net debt/EBITDA, interest coverage, maturities, covenants.
- Insider ownership and comp structure (per-share metrics vs absolute size).

**Valuation lens + primary operating drivers, by business type:**
- *Compounder / payments*: reverse DCF, owner earnings (op cash flow −
  maintenance capex), EV/EBIT vs own 10-yr history. Drivers: TPV × take rate ×
  penetration (or seats/usage × ARPU × NRR for SaaS).
- *Resource/mining*: NAV at conservative mid-cycle commodity price, replacement
  cost / irreplaceability, FCF survival at trough. Drivers: volume × realised
  price × reserve life / cost curve.
- *Infrastructure*: DCF on contracted cash flows, distribution coverage. Drivers:
  contracted volume × tariff.
- *Insurance*: book value + dividends growth, combined ratio, cost of float.
  Drivers: premium volume × loss/expense ratios × float yield.
- *Bank / lender*: loan book × NIM × cost-of-risk.
- Do **not** use PEG as a primary lens; it misleads at both extremes.
- *Lender / credit arm* (standalone or an engine within a hybrid): loan book ×
  NIM × cost-of-risk, valued on book/ROE (residual income or justified P/B) at its
  own cost of equity, with equity-capital consumption modelled. Never a revenue-DCF.
- *Multi-engine hybrid*: SOTP of the engine lenses above; the consolidated DCF is
  a cross-check, not the primary.

**Falsification:** every thesis names three credible bear cases, the leading
indicator for each, and what would have to be true to underperform a global
index over 10 years.

**Sizing / sell discipline (context, not run by these stages):** 8–15 names,
4–10% at cost; sell on broken thesis / deteriorating capital allocation /
structural ROIC decline, not on price moves or macro fear.

## Methodology checks (framing dominates the output)

The authoritative list lives in `framework/methodology-checks.md` and is run as a
gate by `/verdict` before any grade. It covers: constant-currency revenue;
segment glide with group CAGR as an output; horizon by company type with a
two-stage terminal for residual runway; grounded fade endpoints in both
directions; Y-end vs terminal distinction; net-cash sign / strip / single figure;
terminal-value sanity (implied exit multiple, TV % of EV); SBC/dilution
consistency; operating vs non-operating income. These framing checks outrank any
single data point — a mis-framed model with clean data still gives the wrong
verdict. (That file is authoritative; this is a pointer.)

For **build-ahead / capex-super-cycle hybrids** (hyperscaler cloud, AI compute —
infrastructure built ahead of revenue), `framework/capex-supercycle-hybrids.md` is
the archetype playbook: glide capex AND D&A (not flat), ~15yr horizon, owner
earnings, SOTP with the build-ahead capex charged to the backlog engine, and the
discount rate as the dominant swing. `/classify` flags the archetype (item 5b).

## The value-capture discipline (used in /industry-map)

Decomposing an industry into layers is only useful if it answers: **where do
durable economics actually pool, and is that layer investable in public
markets?** The exciting layer (models, apps) often has commoditising economics;
a boring layer (tooling, a chokepoint component, test/packaging) often captures
disproportionate, sticky profit. For each layer state: who captures the margin,
the margin structure, who holds pricing power, and whether it is investable.

## The operating-driver decomposition (universal engine; used in /tech-deepdive and /growth-decomposition)

Every revenue forecast is built from the business's unit economics — volume ×
price — and validated against penetration/capacity and named competitors BEFORE
any CAGR is set. The old semiconductor "substitution model" was the right shape
but the wrong framing: it is this general engine, instantiated per business type
from stage 1's primary operating drivers:

- Payments / transactional → TPV × take rate (bps) × penetration (volume ÷ TAM)
- SaaS → seats or usage × ARPU × NRR/churn
- Bank / lender → loan book × NIM × cost-of-risk
- Resource → volume × realised price × reserve life / cost curve
- Hardware / semis → units × ASP × share, gated by adoption / qualification

The engine answers, in order:
1. **Decompose** realized growth into volume growth + price/rate change →
   classify **volume-led** (durable, capped by penetration) vs **price-led**
   (fragile, mean-reverts). Distinguish real pricing power from mix effects.
2. **Benchmark** the primitive and penetration against named competitors
   (competitor volume is mandatory, not a qualitative landscape).
3. **Build the forward path bottom-up** from volume × price, flagging disclosure
   gaps. /tech-deepdive applies this to the industry/structural opportunity (is
   the pie growing, who holds the chokepoint); /growth-decomposition applies it
   to the company and hands the result — penetration ceiling on volume growth,
   and the take-rate assumption — to /assumptions.

**Revenue-build rule.** Where the operating drivers are quantifiable, the model's
revenue line IS the bottom-up build (volume × price × share, per year) carried
forward from /growth-decomposition — group revenue growth/CAGR is an OUTPUT of the
build, never a typed Y1→Y-end glide (the smooth glide is the fallback only when
drivers aren't disclosable). Every forecast year stays grounded in unit economics,
not a smoothed assertion.

**Sum-of-the-parts rule (multi-engine businesses).** Value each material engine on
its own lens and carry the split THROUGH to valuation; the consolidated DCF is a
*cross-check*, not the primary. A **lender engine** is valued on loan book × NIM ×
cost-of-risk, modelling the equity capital it consumes (distributable FCFE = net
income − increase in required equity capital), via residual income or justified
P/B = (ROE − g)/(CoE − g) at the arm's own cost of equity — never capitalised as
recurring revenue. SOTP and the consolidated DCF should reconcile within a band;
if they diverge, the SOTP wins.

**Earnings-quality rule (generalises the Adyen finance-income lesson).** Separate
operating income from fee income, net interest income, and float/investment
income. They have different durability — do not capitalise them at one terminal
multiple. This is required for any hybrid, not "minor."

**Margins-as-outputs rule.** Terminal EBIT margin is a mix-weighted output —
Σ(segment margin × terminal weight), reconciled to history — not a top-down
assertion, exactly as group revenue CAGR is an output of the glide.

**EM / multi-country rule.** Per-country real-volume-vs-inflation/FX decomposition
(IAS 29 monetary gain/loss for hyperinflation), not a single group constant-
currency number. Country-risk premium in WACC is value-weighted, not
revenue-weighted.

## The DCF assumptions contract (used in /assumptions)

The model is a glide-based DCF: revenue growth interpolates from a Y1 input to a
Y-end input over an explicit horizon set by business type (~10yr growth / ~5yr
stable), with runway beyond the window carried by a two-stage / H-model terminal
rather than a single Gordon jump or a longer window. Output exactly these inputs,
three scenarios each, with justification + source + reliability tag.

Per scenario (Bear / Base / Bull):
| Input | Notes |
|-------|-------|
| Starting revenue (Y0) | most recent actual / clean run-rate |
| Revenue growth — Y1 | constant-currency; built from volume × price (06b) |
| Revenue growth — Y-end (glide end) | anchor to mature comparables; grounded both directions; capped by penetration |
| EBIT margin — start (Y1) | current actual |
| EBIT margin — terminal (Y-end) | margin thesis; state the bridge |
| D&A as % revenue | |
| Capex as % revenue | split maintenance vs growth if disclosed |
| Change in WC as % of Δrevenue | |
| Take rate / price path | EXPLICIT; flat/declining unless pricing power is evidenced (not mix) |
| Tax rate | |
| WACC | state equity risk premium + beta |
| Terminal growth rate | ≤ long-run nominal GDP (arithmetic, not a view) |

Single — SAME across all scenarios (never flex by scenario):
| Net cash (t0) | stripped of settlement balances + regulatory capital; correct sign (added) |
| Diluted shares | reconciled; include SBC dilution only if SBC is not already in EBIT |
| Current price | for the upside check |

Model structure:
| Explicit horizon (N years) | ~10yr growth / ~5yr stable, by classification; carry residual runway with a two-stage / H-model terminal, not a longer window |

The CAGR must reconcile to implied volume growth × take-rate path, with a
penetration sanity check (implied cumulative volume stays below saturation vs TAM
and vs where peers decelerated).

The four swing inputs to scrutinise hardest and flag for the red team:
**Y1 growth, Y-end growth, terminal EBIT margin, WACC.**

Group revenue CAGR, Y-end revenue, TV % of EV, and implied terminal EV/NOPAT are
OUTPUTS to read for the methodology gate — never inputs.

## Scenario construction (driver narrative — not uniform multipliers)

Bear / Base / Bull are three COHERENT stories about **which driver(s) break** —
never base × 0.7 / 1.3 across every input. For each scenario state: a one-line
narrative, the specific driver(s) that move and why, and *what has to be true*.
Within a scenario related drivers move TOGETHER (a demand-digestion Bear lowers
volume AND pricing AND lifts the discount rate — correlated, not independent dials).
Each scenario's broken driver maps to a falsifier carried to /redteam and /verdict.
Built in /assumptions as a scenario-narrative table beside the per-input table;
gated by /verdict (methodology check 16). A spread made by flexing every input
independently is mechanical, not a risk model.

## Monitoring loop (after a completed run)

A full run (stages 1–9) produces a one-time verdict; a multi-year hold is
*maintained*, not decided once. Maintenance runs as a separate, recurring loop
that does NOT re-run the pipeline:

- `THESIS.md` (company root, living file) — the compressed thesis: swing inputs +
  assumed paths, falsifiers, the moat call, and a "things to follow up on" watch
  list. Created by `/thesis` from a completed run; updated thereafter. It outlives
  any single run snapshot.
- `/thesis` — run once after `/verdict` to create THESIS.md.
- `/earnings-update` — run on each earnings report (or a guidance change, M&A, or
  management change — never on price moves). Checks the ER against the thesis,
  appends a dated log entry, updates the watch list, returns a HOLD/ADD/TRIM/SELL
  delta. Re-runs the model only if a falsifier trips or a swing input materially
  deviates — otherwise the tracker update is the whole job.

The `/earnings-update` assessment runs in the `skeptic` subagent specifically to
fight the disposition effect: the failure mode in monitoring is explaining away
bad news to avoid selling (or panicking on one noisy quarter). Hold the sell
discipline — act on thesis change, not price; a price fall on an intact thesis is
an ADD candidate, not a sell.

## UK / ISA context

Investor holds via two family ISAs (~£40k/yr combined). No CGT inside an ISA, so
rebalancing is friction-free. For US-listed names note 15% dividend withholding
(W-8BEN) and GBP/USD exposure. Active sleeve is 20–40% of capital; the rest is
broad index ETFs + BRK.B.

## Output conventions

- Markdown. Lead each file with a one-line status (e.g. `Quality gate: CONDITIONAL PASS`).
- Tables for anything with scenarios or per-item structure.
- End each file with **Open questions** the next stage or the human must resolve.
- Be concise. No filler. State disagreement with sources directly.