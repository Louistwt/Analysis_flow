---
description: Decompose growth into volume × price × penetration — structural framing + company build (mandatory gate)
---

Read `04c-primary-financials.md` (the hard numbers), `05-industry-map.md` (the
chosen layer + where economics pool), and the operating drivers from
`01-classification.md`.

This is the single operating-driver stage — it replaces the old split between a
structural "tech deep-dive" and a company "growth decomposition," which were the
same engine (volume × price × penetration) run at two zoom levels. It is a
**mandatory gate** for any business whose value is driven by unit economics
(payments, SaaS, lending, resource, hardware). In the **industry track** the
"subject" is the chokepoint layer's anchor company; otherwise it is the issuer.

Write `06-operating-drivers.md` in three parts — structural framing (A), the
company build (B, the core), and the penetration/competitor close (C).

## Part A — Structural framing (the pie the company sits inside)

Keep this tight; it exists to *bound* the company build, not to re-survey the
industry (that is `05`'s job).
1. **What is being substituted** — the incumbent solution/economics being replaced
   and the new solution's cost/performance crossover (where it wins on merit).
2. **Adoption curve** — rate and gating factors (cost crossover, capacity,
   qualification cycles); a year-by-year migration path, bear/base/bull.
3. **Chokepoint & pricing power** — the scarce/single-sourced input in the stack
   and who holds pricing power during the migration.
4. **TAM & pool** — TAM migration expressed in the business's own units
   (transactional → TPV × take rate × share, not generic units × ASP), so it
   reconciles with Part B.

## Part B — Company volume × price build (the core)

5. **Decompose realized growth** per period for 5+ years into the primitives:
   revenue growth ≈ volume growth + price/rate change (e.g. TPV growth + take-rate
   change). Show the table. Use only `hard`/`soft` figures from `04c`. **The
   observed multi-year trajectory is the anchor for the forecast — not decoration.**
   Read the *shape*: the volume-growth deceleration curve (e.g. 49%→33%→21%), the
   take-rate path (mix vs pricing), the margin cycle. The forward glide (step 7)
   MUST be a grounded continuation of this curve, not a hand-set endpoint. If you
   catch yourself typing a Y1/Y-end pair the history doesn't imply, stop.
6. **Volume-led vs price-led verdict.** Volume-led on a flat/competitive rate =
   durable but penetration-capped; price-led (rising rate) = fragile, mean-reverts.
   Distinguish genuine pricing power from mix effects (a take-rate rise caused by
   shedding low-rate volume is mix, not pricing).
7. **Forward REVENUE BUILD, bottom-up** from volume × price — a per-year,
   per-driver table (e.g. TPV × take × penetration, or units × ASP × share), NOT a
   top-down CAGR. **This build is the revenue ENGINE the model carries forward**
   wherever the drivers are quantifiable: group revenue growth/CAGR is an OUTPUT
   that falls out of the roll-up, never a typed Y1→Y-end glide %. Reconcile the
   roll-up to the most recent actual. Where drivers are NOT disclosable, fall back
   to a glide and say so.
7b. **Per-engine and (if EM) per-country.** Decompose each engine on its own
   primitive. For a hyperinflationary geography, split growth into real volume vs
   inflation/FX (IAS 29 — note the monetary gain/loss); do not read nominal local
   growth as real.
7c. **Two reconciling builds where two granularities are disclosed (MELI-standard).**
   If the issuer discloses the primitive at two cuts — e.g. group volume (long
   series) *and* segment/regional revenue (another series) — build the forecast
   BOTH ways and reconcile them, the way a SOTP reconciles to a consolidated DCF.
   Agreement between two independent bottom-up paths is the confidence; a divergence
   is a flag to resolve, not average. Where one cut has more history, anchor on it
   and use the other as the cross-check. (MELI: per-country GMV×take-rate roll-up
   reconciled to the consolidated build.)
7d. **Margin is an OUTPUT of the observed leverage curve, not asserted.** Read the
   terminal margin off the multi-year operating-leverage record (e.g. EBITDA
   63%→44% trough→53%, guided >55%) plus the segment/mix shift — the same way the
   CAGR falls out of the volume build. State the bridge; do not type a terminal
   margin the history and mix don't support (methodology #10).

## Part C — Penetration & competitor close (the ceiling)

8. **Competitor benchmarking on the SAME primitive.** Named peers' volume and
   growth (e.g. competitor TPV + growth), sourced. Is the subject gaining or losing
   share of the primitive? Flag any peer out-growing it. **Compare like-for-like
   only** — different firms measure differently (Meta impressions × price, Google
   clicks × CPC; the volume/price *halves* are NOT comparable, only total revenue
   growth is). Pull competitor primitives EARLY, before the base is set. Competitor
   *volume* is mandatory, not a qualitative landscape.
9. **Penetration vs TAM and vs peers.** player volume ÷ TAM; where did comparable
   players decelerate? This sets the **ceiling on how high volume growth can stay**.
10. **Hand-off to `/assumptions`** — state explicitly: (a) the penetration ceiling
   on volume growth, and (b) the take-rate/price assumption (flat / declining /
   rising) with its justification. These ground the glide endpoints and Part A's
   structural tailwind is the band the company build sits inside.

A forward growth number not reconciled to volume × price × penetration is an
assertion, not an estimate — say so if the data won't support one. Tag every
number hard/soft/unsupported.

**Smuggled-bull guard:** a segment CAGR set against a peer's *scale* and back-solved
to revenue (e.g. "we reach AWS's size in 10yr"), with no share-bridge, is an
assertion — require a NAMED share-bridge (logo wins / displacement) or relabel it
as "riding TAM" and move the unsupported version to the Bull.

Append unresolved items to the run's disclosure-gap register (see CLAUDE.md), not a
standalone open-questions list.


---

## Build mechanics (added 2026-08-18) — use the one that fits the business

### ★ M-A. Generational replacement (any business with discrete product generations)
Preferred over a typed growth rate wherever products come in generations — accelerator
programmes, tool generations, node transitions, handset silicon. Build it as:

1. **Product roadmap** — what launches in each forecast year, from disclosed roadmaps and
   management commentary. Separate *shipping* / *qualified* / *sampling* / *announced*.
2. **Old-vs-new mix, year by year, until full replacement** — the S-curve. **Anchor the
   replacement pace to the issuer's own HISTORICAL product-cycle length**, not to an assumed
   ramp. Past cycles are the empirical calibration and they are usually disclosable.
3. **ASP path derived from the PERFORMANCE DELTA** — new-generation ASP growth should follow
   the performance (or performance-per-watt, or performance-per-dollar) improvement over the
   prior generation, not a typed inflation number. Where a vendor deliberately hands part of
   that improvement to the customer, that is *unexercised pricing power* and belongs in the
   moat assessment, not in the ASP line (CLAUDE.md quality gate).
4. **Units per generation × ASP per generation**, summed = revenue. Group growth is an OUTPUT.

### ★ M-B. Capacity schedule (any capacity-owning business: foundry, memory, packaging, fabs)
Build bottom-up from physical plant, normalised to a common unit (e.g. 12-inch wafer
equivalents):

| Per site | Node/process | Production start | Monthly capacity | → Annual capacity |
|---|---|---|---|---|

Then per forecast year: **total capacity · new capacity added · ASP per normalised unit ·
expected utilisation · capacity actually used** → revenue. Include announced *and* credibly
rumoured expansions, **tagged separately** — rumoured capacity may inform the Bull case but
must not sit in the Base (reliability tagging, CLAUDE.md prime directive #3).

### ★ M-C. Two mandatory cross-checks before any CAGR is accepted
- **TAM ↔ units × ASP** (methodology #30): derive the market size independently top-down, and
  bottom-up from this build. State both and the gap. Where physical ceilings exist (capacity,
  a scarce input, power, funding), add them as further independent ceilings and say **which
  binds** — that determines whether pricing holds or erodes.
- **Share sum ≤ 100%** (methodology #29): name the competitive set, state each player's assumed
  share, and show the sum. If it exceeds 100%, say which assumption is wrong.
