# Improvement backlog — framework and command changes

Pending changes. Each item states the proposed edit and the file it touches.

---

## ✅ BATCH 1 APPLIED — 2026-08-18

All eight adoptions (A1–A8) and the C1 synthesis are now live. B1–B3 were deliberately not
adopted (our method is better). Applied to:

| Change | Where it landed |
|---|---|
| A1 share sum ≤100% | `methodology-checks.md` #29 · `/operating-drivers` M-C · `/verdict` gate · CLAUDE.md revenue-build rule |
| A2 generational replacement build | `/operating-drivers` M-A · CLAUDE.md operating-driver engine |
| A3 TAM ↔ units × ASP check | `methodology-checks.md` #30 · `/operating-drivers` M-C · `/verdict` gate |
| A4 TAM from consensus of primary voices | `/deepresearch-prompt` · `/industry-dr-prompt` |
| A5 capacity-schedule bottom-up | `/operating-drivers` M-B · CLAUDE.md |
| A6 twin DCF (reported + maintenance capex) | `methodology-checks.md` #32 · `/assumptions` · `/verdict` · CLAUDE.md directive #5 |
| A7 reverse-DCF as required revenue CAGR | `methodology-checks.md` #33 · `/verdict` |
| A8 quarterly series + explicit ROIC definition | `methodology-checks.md` #31 · `/verify-primary` |
| C1 synthesis — component-built reasoning, swept presentation, per engine | `methodology-checks.md` #34 · `/assumptions` · CLAUDE.md assumptions contract |
| C2 model artifact | `/assumptions` — sheet built alongside the markdown contract |

**Deliberately NOT adopted** (ours is stronger): web-sourcing quarterly financials (we use SEC
XBRL); scenarios as parameter flexes rather than driver narratives; untagged rumoured capacity.

**Validation:** the investor reports that this framework, the senior investor's method, and their
own independent work converged on similar valuations for MSFT, GOOGL and ADYEN — three different
routes to the same answer, which is the strongest available evidence that the framework is sound
rather than merely internally consistent.

**Where we deliberately differ from the senior investor:** he does no macro work at all. We keep
it — see `companies/Industry/Semiconductor/05b-macro-regime.md` for the fiscal-dominance /
neomercantilism regime lens, whose conclusions (capacity duplication subsidises tools and taxes
capacity-owner returns; sovereign demand relaxes the commercial-ROI test; rearmament puts a
government-funded floor under mature-node silicon; complexity-metered layers have inflation
pass-through) are all decision-relevant and would be invisible to a bottom-up-only process.

---

## Pending — not yet applied

---

## Batch 1 — from a senior investor's INTC research/valuation prompt (reviewed 2026-08-18)

Source: a working prompt used to drive a full INTC model (TAM → segment build → capacity
schedule → DCF → reverse-DCF → 5yr quarterly financials + ratios). Written in Chinese; the
methodology is summarised here in English.

### ★ ADOPT — 8 items where his method is sharper than ours

**A1. The >100% share check (highest value, lowest cost).**
> *"對比競爭對手市佔加總會唔會 > 100%"* — check whether competitors' assumed market shares sum
> to more than 100%.

Every company model assumes its subject gains share. Summed across the competitive set, those
assumptions are frequently collectively impossible. We gesture at this in `/industry-dr-prompt`
("quantify the inconsistency") but never operationalise it.
**Proposed:** add as a hard gate in `framework/methodology-checks.md` (new check #29) and to the
`/verdict` gate list. Wherever a share assumption exists, the model must name the competitive set
and show the shares summing to ≤100%.

**A2. Generational replacement as the revenue-build mechanic.**
> Consider product roadmap → what launches each year → the old/new mix shifting annually until
> full replacement → calibrated against *historical product-cycle length* → then derive new-product
> ASP growth from the *performance improvement* over the old product.

This is materially more concrete than our "units × ASP × share, gated by adoption/qualification".
It gives an S-curve with an empirical anchor (past cycle length) and a principled ASP path
(performance delta), instead of a typed growth rate. It is exactly the right shape for AVGO's XPU
programme generations, Disco/BESI tool generations, and Nvidia's annual cadence.
**Proposed:** add to `/operating-drivers` as the preferred build for any business with
discrete product generations, with the two anchors named (historical cycle length; performance-per-
dollar delta).

**A3. TAM ↔ (units × ASP) contradiction check.**
> *"請你對照並檢查有關 TAM 數字與條件 1 中的資料所算的出貨量及 ASP 有沒有矛盾之處"*

He derives the TAM and the unit×ASP build from *independent* sources, then explicitly checks them
against each other. We build bottom-up but rarely reconcile against an independently-derived TAM.
**Proposed:** `/operating-drivers` must state both numbers and the gap. Already partly reflected in
`companies/AVGO/01b-ai-accelerator-tam.md` (the five-meter method) — generalise it.

**A4. TAM built from a consensus of primary voices, not one number.**
> Gather earnings-call, conference and interview transcripts plus institutional reports across
> *many* companies; find the commonalities; derive a consensus TAM from the overlap.

Triangulating qualitative sources against each other, rather than accepting one figure with a
stated method. Better than our current "show your method or it's `soft`".
**Proposed:** add to `/industry-dr-prompt` and `/deepresearch-prompt` — where a market size is
needed, ask for *what several named participants each say* and where they agree, not for a number.

**A5. Capacity-schedule bottom-up, in normalised wafer equivalents.**
> Plant name, location, process node, production start, monthly → quarterly → annual capacity;
> then total capacity, new capacity, ASP per 12" wafer, utilisation, used capacity, per year.

The correct way to model any capacity business. Directly applicable to TSMC, to the CoWoS
crossover question, and to memory.
**Proposed:** add as a named sub-method in `/operating-drivers` for capacity-owning businesses,
and reference from `framework/capex-supercycle-hybrids.md`.

**A6. Run TWO DCFs — reported capex and Greenblatt maintenance capex — and compare.**
The gap between them *is* the growth investment, made visible rather than asserted. Our CLAUDE.md
says "distinguish maintenance from growth capex" but never requires both models.
**Proposed:** `/assumptions` produces both; `/verdict` reads the gap as the implied growth
investment and sanity-checks it against the reinvestment ↔ ROIC ↔ growth tie (methodology #24).

**A7. Reverse-DCF stated as "what revenue CAGR does the current price require?"**
We have reverse-DCF as a triangulation (methodology #25) but not in this form. His phrasing is the
most legible version of the question and lands the price comparison in driver terms rather than
multiple terms — which fits our price-enters-last rule well, because it converts price into a
*testable operating assumption*.
**Proposed:** make this the required form of the reverse-DCF output in `/verdict`.

**A8. Five years of QUARTERLY financials + derived ratios, with definitions spelled out.**
> Quarterly IS, CF, BS for 5 years; then GM, EBIT/EBITDA/net/OCF/FCFF margins, capex/sales, ROIC,
> DIO, DSO, DPO, CCC. ROIC defined explicitly as EBIT × (1 − 25% marginal tax) ÷ (Inventory + AR +
> Intangibles *incl. goodwill* + PP&E *incl. operating-lease assets* − AP − capital lease), with the
> instruction to *understand the meaning* because filings use different wording.

We have been working annually. Quarterly is what surfaces the working-capital signals we actually
used in this project (inventory days, DSO, the V1 turn signal). Spelling out the ROIC formula and
warning about naming differences is good anti-ambiguity practice worth copying verbatim.
**Proposed:** add a quarterly-series step to `/verify-primary`, and put the explicit ROIC/invested-
capital definition into `framework/methodology-checks.md` so it stops being re-derived per run.

### WHERE OUR METHOD IS BETTER — do not adopt

**B1. He asks the model to "find from the web" 5 years of quarterly statements (his steps 14, 16).**
This is precisely the failure mode documented in `companies/Industry/Semiconductor/04-critique.md`
— an LLM reconstructing filing figures from memory. **We pull these from SEC XBRL** with the
tooling built in this project (`companyfacts`, ~40 lines of Python, exact and free). Keep ours.

**B2. Scenario construction.** His prompt asks for Bear/Base/Bull but never requires them to be
coherent *driver narratives*. CLAUDE.md's scenario rule (three stories about which driver breaks,
correlated moves within a scenario, each mapped to a falsifier) is stronger. Keep ours.

**B3. Reliability tagging.** He explicitly allows *rumoured* capacity schedules
(*"已落實或傳聞落實"*) into the model. Pragmatic for capacity work, but rumour then enters
unlabelled. Our `hard`/`soft`/`unsupported` tagging is the guard. Adopt his willingness to *use*
rumoured capacity — but tag it, and keep it out of the Base case.

### ⚠️ GENUINE DISAGREEMENT — needs the investor's decision

**C1. "Do not use CAPM or WACC" — sweep 8/9/10/11/12% instead, with 3% terminal growth.**

This directly contradicts CLAUDE.md methodology #18–19 (cash-flow ↔ discount-rate consistency;
component-built cost of capital with a through-cycle beta).

*The case for his approach:* beta is noisy, backward-looking, and gives false precision; a hurdle
sweep is honest about uncertainty and lets the reader locate their own required return. Many
capable investors work exactly this way.

*The case against:* (i) FCFF still needs *a* rate consistent with the cash-flow definition;
(ii) for a **multi-engine SOTP** — which is exactly what we are building for AVGO — one swept rate
across all engines destroys the per-engine risk distinction that is the entire point of the SOTP;
(iii) it removes the discipline of asking *why* a rate is appropriate.

**Proposed synthesis (recommend):** keep the component-built rate as the *reasoning* step, then
**present the answer as a sweep** — and for a hybrid, **sweep each engine separately** rather than
one blended sweep. State where in the range we believe the answer sits and why. That keeps his
honesty about uncertainty without losing per-engine risk.

**Decision needed from the investor** before this changes `/assumptions` or
`framework/methodology-checks.md`.

**C2. Excel/Sheets as the model artifact.** His whole workflow is spreadsheet-native (tabs,
sensitivity grids, adjustable inputs). Ours is markdown. For actual DCF work a live sheet is
better — and there is already a memory (`gsheet-model-build`) covering how to build one.
**Proposed:** at `/assumptions`, output the markdown contract *and* build the live sheet.
**Decision needed:** whether to make the sheet mandatory or optional.

### Cheap wins to do first
A1 (>100% share check), A7 (reverse-DCF phrasing), A8's ROIC definition. All three are small edits
to `framework/methodology-checks.md` and immediately useful.
