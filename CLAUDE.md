# CLAUDE.md — Equity Research Pipeline

You are operating inside a staged equity-research pipeline. Each slash command
is one stage. Read only the files a stage names, write only the file it names,
and stop. The human reviews between stages. Do not run ahead.

## Pipeline stages

**Sourcing is primary-first.** The issuer's verified financial spine is extracted
from the filings *before* DeepResearch runs — leading with an aggregator narrative
anchors the model on consensus it then has to un-anchor from. DeepResearch supplies
qualitative + competitive *color*, cross-checked against the spine, never the
reverse. The table is in **run order**; the numeric filename prefix is a legacy
artifact and does not always match run order (`04c` is produced at run-step 2).

| Run | Command | Writes |
|---|---------|--------|
| 1 | /classify | 01-classification.md |
| 2 | /verify-primary | 04c-primary-financials.md (PRIMARY FIRST — filings via NotebookLM + SEC XBRL; needs 04b-notebooklm-raw.md) |
| 3 | /deepresearch-prompt | 02-dr-prompt.md (scoped to qualitative + competitive color) |
| 4 | (run prompt in Gemini DeepResearch) | 03-gemini-report.md |
| 5 | /critique-report | 04-critique.md (audits the color vs the verified spine) |
| 6 | /industry-map | 05-industry-map.md (subject's competitive position + profit pool) |
| 7 | /operating-drivers | 06-operating-drivers.md (structural framing + company volume × price build) |
| 8 | /assumptions | 07-assumptions.md |
| 9 | /redteam | 08-redteam.md |
| 10 | /verdict | 09-verdict.md (runs the methodology gate first) |

`/operating-drivers` merges the former `/tech-deepdive` + `/growth-decomposition`
(they were one engine at two zoom levels). A single living **`_open-questions.md`**
register at the company root replaces per-stage open-questions lists: every stage
appends, `/verdict` draws it down.

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
| 4 | /critique-report | 04-critique.md (reused — domain-agnostic) |
| 5 | /industry-layermap | 05-industry-map.md (ranks profit pools, keeps multiple layers live) |
| 6 | /operating-drivers | 06-operating-drivers.md (reused — chokepoint layer's anchor is the "subject") |
| 7 | /industry-shortlist | 07-shortlist.md (ranked named candidates → hand-off to the company funnel) |

The track reuses `/critique-report` and `/operating-drivers` as-is and leaves the
valuation funnel untouched. Its terminal output is NOT a verdict — it is a routing
artifact: each shortlisted name is copied into `companies/<TICKER>/`, seeded with
its entry lens, and run through `/classify` onward. **Cash-cow + optionality**
names (an existing profitable business funding the robotics/AI bet) go first —
they carry an SOTP valuation floor and so fail safer.

## Prime directives

1. **The Base case is the EXPECTED (most-likely) path — not a conservative one.**
   A DCF output is a hypothesis that varies with assumptions, so risk is managed
   through the *width and reasoning* of the Bear–Bull spread, not a precise number.
   But the Base must be the honest **centre** of that spread: it credits
   demonstrated, durable performance and fades only where penetration,
   mean-reversion, or specific evidence warrants — **as willing to hold strength as
   to assume weakness** (methodology #4, both directions). **Conservatism is applied
   ONCE — in the Bear scenario and in the margin-of-safety required at the decision
   — never baked into the Base as well.** Baking caution into the Base, then
   red-teaming it downward, then demanding a discount below it, triple-counts
   caution and makes every quality compounder look "fairly valued." Never present a
   point estimate as a conclusion; never let the Base drift into a de-facto Bear.
2. **Provenance with every number.** Each quantitative assumption cites where it
   came from (report section, filing, or explicit inference). No orphan numbers.
3. **Reliability tagging.** Tag every key input `hard` (sourced, recent,
   corroborated), `soft` (single source or estimate), or `unsupported`
   (asserted, no basis). Only `hard` inputs move the Base case. `soft` and
   `unsupported` widen the Bear–Bull spread instead.
4. **Quality before price — and price enters LAST.** A low valuation on a narrowing moat
   or poor capital allocation is a pass, not a bargain. **The inverse is equally binding: a
   high price on a durable, compounding business is not a reason to rank it down.** Judge
   businesses on quality, moat, operations, margin level and stability, materialised orders
   and reinvestment runway — then value them from those drivers — and only THEN compare the
   result to the market price.

   **The sequencing rule (binding on every stage before `/verdict`):**
   `quality gate → operating drivers → assumptions → our own valuation → THEN price`.
   Until our own valuation exists there is no basis for calling anything cheap or expensive.

   **Never use as a screen, a ranking input, or a reason to drop a name:** current multiple
   vs its own history, percentile-of-own-range, distance from an all-time high, or any other
   price-relative-to-past-price measure. These are statements about the *past price series*,
   not about the business. A quality compounder whose earnings power has structurally changed
   will sit near the top of its own historical multiple range *precisely because it is
   winning* — screening on that systematically discards the best businesses. **Price-derived
   figures are NOT written into any artifact before `/verdict` — not even quarantined.** A
   number sitting in the file is an anchor whether or not it carries a warning label, and this
   framework's own premise is that framing dominates the output. `/verdict` retrieves the price
   fresh at decision time. No earlier stage records it, cites it, or reasons from it, and no
   earlier stage may compute a multiple — including on a normalised or peak-year denominator.

   Price re-enters exactly twice, both at the end: as the **upside check** against our own
   DCF, and as the **margin of safety** demanded at the decision. Historical drawdown of
   *revenue and operating margin* is business performance and stays in scope throughout —
   it is not a price measure.
5. **Distinguish maintenance capex from growth capex — and run BOTH models.**
   Build the DCF twice: once on reported capex, once on Greenblatt maintenance capex.
   **The gap between the two valuations IS the growth investment**, made visible rather
   than asserted, and it must reconcile to the reinvestment ↔ ROIC ↔ growth tie
   (methodology #32). Treat stock-based
   compensation as a real cost — and if owner earnings are built from OCF, deduct
   SBC from OCF (it's added back as non-cash) and use diluted shares (methodology
   #8). Anchor on business performance, not share price.
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

  **Margin measures rent EXTRACTED, not moat WIDTH — never rank moat on margin alone.**
  A monopolist may deliberately under-price to keep its customers healthy, keep the
  ecosystem expanding, and avoid funding an entrant. That choice *understates* it on every
  margin screen while making the position more durable, and it leaves a large block of
  **unexercised pricing power** that a DCF should treat as real optionality. The inverse is
  the standing danger: **extracted rent attracts entry — unexercised rent deters it.** A
  very high margin is as often a signal of vulnerability (it is funding the competitor's
  business case) as of strength.

  Test for **latent pricing power** instead, and treat any of these as evidence of it:
  1. **Rationing rather than price-clearing** — allocation, multi-year lead times, waitlists.
     A supplier facing excess demand that does *not* raise price to clear it is choosing not
     to exercise power it demonstrably has.
  2. **Customer prepayments / capacity reservations** — cash paid ahead to secure supply is
     the customer stating it cannot get enough at the current price.
  3. **Value delivered per unit of price rising** — performance per dollar improving each
     generation is margin handed to the customer on purpose.
  4. **High and rising R&D intensity** — rent recycled into the roadmap rather than taken.
  5. **Position on the customer's critical path** — if the customer's own roadmap fails
     without this supplier, that is the deepest form of moat, and it may show up in no
     margin metric at all.

  The question to answer is: **what happens to the customer if this supplier raises price
  20%?** If they pay, pricing power exists whatever the current margin says.

  **Normalise for purchase accounting before comparing margins.** Amortisation of acquired
  intangibles is a non-cash charge that depresses GAAP operating margin for years after a
  deal and makes an acquirer look structurally less profitable than it is (methodology #28).
  State margins both as-reported and ex-amortisation where a major acquisition is in the
  base, and never rank on the as-reported figure alone.

  **Judge the whole business, not the fashionable segment.** A company's moat lives wherever
  its economics actually sit — an instruction-set duopoly, a defence/industrial design-in
  measured in decades, or a licensing base can be a wider moat than the segment currently
  attracting attention. Scope the moat assessment to the full revenue base before ranking.
- Capital allocation: 10-yr record of buybacks (at what prices?), M&A (returns
  vs promised), debt management. Best predictor of per-share value creation.
  **Is it a *frequent* acquirer?** If so, M&A is growth reinvestment (off-balance-
  sheet R&D) — model acquisition spend in capex, not as free growth, or you
  double-count the bought growth's amortisation while dropping its cash cost
  (methodology #28).
- Reinvestment runway: can incremental capital be deployed at high ROIC? A high
  ROIC that can't be reinvested is a cash cow, not a compounder.
- Balance sheet: net debt/EBITDA, interest coverage, maturities, covenants.
- Insider ownership and comp structure (per-share metrics vs absolute size).

**Valuation lens + primary operating drivers + discount-rate method, by business
type.** The discount-rate *method* is SELECTED per engine at `/classify` (item 2b),
not defaulted to WACC; it must match the cash-flow definition (methodology #18):
- *Compounder / payments*: reverse DCF, owner earnings (op cash flow −
  maintenance capex), EV/EBIT vs own 10-yr history. Drivers: TPV × take rate ×
  penetration (or seats/usage × ARPU × NRR for SaaS). **Method: FCFF → WACC.**
- *Resource/mining*: NAV at conservative mid-cycle commodity price, replacement
  cost / irreplaceability, FCF survival at trough. Drivers: volume × realised
  price × reserve life / cost curve. **Method: FCFF → WACC (NAV variant).**
- *Infrastructure*: DCF on contracted cash flows, distribution coverage. Drivers:
  contracted volume × tariff. **Method: FCFF → WACC, or APV if it deleverages.**
- *Insurance*: book value + dividends growth, combined ratio, cost of float.
  Drivers: premium volume × loss/expense ratios × float yield. **Method: FCFE →
  cost of equity / residual income on book — NOT WACC.**
- *Bank / lender*: loan book × NIM × cost-of-risk. **Method: FCFE → cost of equity
  / residual income — NOT WACC.**
- Do **not** use PEG as a primary lens; it misleads at both extremes.
- *Lender / credit arm* (standalone or an engine within a hybrid): loan book ×
  NIM × cost-of-risk, valued on book/ROE (residual income or justified P/B) at its
  own cost of equity, with equity-capital consumption modelled. Never a revenue-DCF.
- *Multi-engine hybrid*: SOTP of the engine lenses above, **each engine on its own
  method/rate** (a lender at its CoE, commerce at WACC — never one blended WACC);
  the consolidated DCF is a cross-check, not the primary.
- *Changing capital structure* (LBO-like, debt-funded build-ahead that deleverages,
  large time-varying NOLs): **APV** — value unlevered + PV(tax shields) − distress,
  because constant-weight WACC misprices a moving D/E.

**Falsification:** every thesis names three credible bear cases, the leading
indicator for each, and what would have to be true to underperform a global
index over 10 years.

**Sizing / sell discipline (context, not run by these stages):** 8–15 names,
4–10% at cost; sell on broken thesis / deteriorating capital allocation /
structural ROIC decline, not on price moves or macro fear.

## Methodology checks (framing dominates the output)

The authoritative list lives in `framework/methodology-checks.md` and is run as a
gate by `/verdict` before any grade. It covers (1–17): constant-currency revenue;
segment glide with group CAGR as an output; horizon by company type with a
two-stage terminal; grounded fade endpoints in both directions; Y-end vs terminal
distinction; net-cash sign / strip / single figure; terminal-value sanity; SBC/
dilution consistency; operating vs non-operating income; margins-as-outputs; SOTP
surviving to valuation with a lender valued as a lender; EM per-country / value-
weighted CRP; driver-narrative scenarios. And (18–26): **cash-flow ↔ discount-rate
consistency** (FCFF→WACC / FCFE→CoE / residual income / APV — the right *method*
for the business); the **cost-of-capital contract** (component-built, through-cycle
beta); **NOPAT not EBIT** on operating earnings with tax as a glide; **reinvestment
↔ ROIC ↔ growth** ties and growth only creating value **above the cost of capital**;
a **normalised (mid-cycle) base year** (stripped of one-off blended-metric
distortions); **fading the return toward WACC** in the terminal; and the two
triangulations — **reverse-DCF** and a **relative-value cross-check**. And (27–28):
**EBIT vs EBITDA never mixed** (bumping an EBIT input toward an EBITDA headline
double-counts D&A), and **a serial acquirer's M&A modelled as reinvestment** (not
free growth). And (29–34): **competitive shares must sum to ≤100%**; **TAM reconciled
against units × ASP** with the binding constraint named; **one stated ROIC / invested-
capital definition**; **two DCFs — reported capex and maintenance capex — with the gap
read as the growth investment**; **reverse-DCF phrased as the revenue CAGR the price
requires**; and a **component-built but SWEPT discount rate, per engine**. These framing checks outrank any single data point — a mis-framed
model with clean data still gives the wrong verdict. (That file is authoritative;
this is a pointer.)

For **build-ahead / capex-super-cycle hybrids** (hyperscaler cloud, AI compute —
infrastructure built ahead of revenue), `framework/capex-supercycle-hybrids.md` is
the archetype playbook: glide capex AND D&A (not flat), ~15yr horizon, owner
earnings, SOTP with the build-ahead capex charged to the backlog engine, and the
discount rate as the dominant swing (**APV** over constant-weight WACC where the
build deleverages). `/classify` flags the archetype (item 5b).

## The value-capture discipline (used in /industry-map and /industry-layermap)

Decomposing an industry into layers is only useful if it answers: **where do
durable economics actually pool, and is that layer investable in public
markets?** The exciting layer (models, apps) often has commoditising economics;
a boring layer (tooling, a chokepoint component, test/packaging) often captures
disproportionate, sticky profit. For each layer state: who captures the margin,
the margin structure, who holds pricing power, and whether it is investable. The
*full* layer survey is the industry track's job (`/industry-layermap`); the
company-funnel `/industry-map` applies this discipline only to the layers that
touch the subject — position, profit pool, competitor set — not a whole-industry map.

## The operating-driver decomposition (universal engine; used in /operating-drivers)

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

**Two build mechanics take precedence where they fit** (detail in `/operating-drivers`):
- **Generational replacement** — for any business with discrete product generations, build
  the old-vs-new mix year by year until full replacement, **calibrated to the issuer's own
  historical product-cycle length**, with new-generation **ASP growth derived from the
  performance delta** over the prior generation. Preferred over any typed growth rate.
- **Capacity schedule** — for any capacity owner (foundry, memory, packaging), build
  plant-by-plant in normalised units (e.g. 12-inch wafer equivalents): node, start date,
  monthly → annual capacity, ASP per unit, utilisation, capacity used. Rumoured expansions
  may inform the Bull case but never the Base.

The engine answers, in order:
1. **Decompose** realized growth into volume growth + price/rate change →
   classify **volume-led** (durable, capped by penetration) vs **price-led**
   (fragile, mean-reverts). Distinguish real pricing power from mix effects.
2. **Benchmark** the primitive and penetration against named competitors
   (competitor volume is mandatory, not a qualitative landscape).
3. **Build the forward path bottom-up** from volume × price, flagging disclosure
   gaps. `/operating-drivers` does both zoom levels in one stage: the structural/
   industry framing (is the pie growing, who holds the chokepoint) as its opening
   part, then the company-level build — handing the penetration ceiling on volume
   growth and the take-rate assumption to `/assumptions`.

**Revenue-build rule.** Where the operating drivers are quantifiable, the model's
revenue line IS the bottom-up build (volume × price × share, per year) carried
forward from /operating-drivers — group revenue growth/CAGR is an OUTPUT of the
build, never a typed Y1→Y-end glide (the smooth glide is the fallback only when
drivers aren't disclosable). Every forecast year stays grounded in unit economics,
not a smoothed assertion. **Two cross-checks are mandatory before any CAGR is accepted:**
the **TAM ↔ units × ASP reconciliation** with the binding constraint named (methodology #30),
and the **competitive share sum ≤ 100%** across the named competitor set (methodology #29).
Run the TAM check on the **TERMINAL year**, not just t0 — unwind it back through the demand
chain and say what it implies about the market. And **every driver must reach a plateau inside
the window**: a share or penetration glide still climbing in the final year leaks that
transition into the terminal (methodology #5).

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
| Starting revenue (Y0) | most recent actual / clean run-rate; NORMALISED (mid-cycle, not a peak/trough year) |
| Revenue growth — Y1 | constant-currency; built from volume × price (06-operating-drivers) |
| Revenue growth — Y-end (glide end) | anchor to mature comparables; grounded both directions; capped by penetration |
| EBIT margin — start (Y1) | current actual, OPERATING EBIT only (non-operating income valued separately); this is **EBIT, not the EBITDA headline** — never bump it toward a higher EBITDA print, that double-counts D&A (methodology #27) |
| EBIT margin — terminal (Y-end) | margin thesis; state the bridge |
| D&A as % revenue | |
| Capex as % revenue | split maintenance vs growth if disclosed; reconcile to the growth via reinvestment × ROIC |
| Change in WC as % of Δrevenue | |
| Take rate / price path | EXPLICIT; flat/declining unless pricing power is evidenced (not mix) |
| Tax rate (glide) | current-effective → normalised marginal *cash* rate; NOPAT = operating-EBIT × (1 − this) |
| Discount rate (method per /classify 2b) | WACC (FCFF) / cost of equity (FCFE, financials) / APV (changing structure); component-built — state Rf + ERP + beta (through-cycle) — then **PRESENT AS A SWEEP (8/9/10/11/12%)**, stating where the component build lands and why. **For a hybrid, sweep each engine separately** (methodology #34) |
| Terminal growth rate | ≤ long-run nominal GDP (arithmetic, not a view); fade incremental ROIC toward the discount rate |

Single — SAME across all scenarios (never flex by scenario):
| Net cash (t0) | stripped of settlement balances + regulatory capital; correct sign (added) |
| Diluted shares | reconciled; include SBC dilution only if SBC is not already in EBIT |
| Current price | **left EMPTY until `/verdict`** — the model carries the input cell so the upside check can be computed at the decision, but `/assumptions` does not fill it in |

Model structure:
| Explicit horizon (N years) | **~10yr for a growth company, ~5yr for a mature one — NOT 10+5** (15yr is the build-ahead exception only); **model growth in TWO stages — Stage 1 (Y1–5) holds/gently-fades the growth rate, Stage 2 (Y6–10) does the mature fade — NOT a single linear glide from Y1 (which under-states a growth-stage compounder)** (methodology #3); carry residual runway with a two-stage / H-model terminal, not a longer window |

The CAGR must reconcile to implied volume growth × take-rate path, with a
penetration sanity check (implied cumulative volume stays below saturation vs TAM
and vs where peers decelerated).

The four swing inputs to scrutinise hardest and flag for the red team:
**Y1 growth, Y-end growth, terminal EBIT margin, discount rate.**

Group revenue CAGR, Y-end revenue, TV % of EV, implied terminal EV/NOPAT, and the
implied ROIC (from reinvestment × growth) are OUTPUTS to read for the methodology
gate — never inputs.

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

A full run (the ten run-steps to /verdict) produces a one-time verdict; a
multi-year hold is *maintained*, not decided once. Maintenance runs as a separate,
recurring loop that does NOT re-run the pipeline:

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
- Append unresolved items to the single `_open-questions.md` register (not a
  per-file Open-questions list); `/verdict` draws the register down.
- Be concise. No filler. State disagreement with sources directly.
- **A superseded model must not stay runnable.** Delete it or make it print its own
  obsolescence — a script that confidently reports last week's answer is how a wrong number
  outlives its correction. Generated artefacts (a sheet and the script that styles it) must
  come from ONE source, or they drift apart silently.