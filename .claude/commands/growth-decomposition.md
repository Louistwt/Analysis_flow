---
description: Decompose the company's growth into volume × price × penetration (mandatory gate)
---

Read `04c-primary-financials.md`, `06-tech.md`, `05-industry-map.md` (for TAM),
and the operating drivers from `01-classification.md`.

This is a mandatory gate for any business whose value is driven by unit economics
(payments, SaaS, lending, resource, hardware). Apply the operating-driver engine
(CLAUDE.md) at the COMPANY level. Write `06b-growth-decomposition.md`:

1. **Decompose realized growth** per period for 5+ years into the primitives:
   revenue growth ≈ volume growth + price/rate change (e.g. TPV growth + take-rate
   change). Show the table. Use only `hard`/`soft` figures from 04c.
2. **Volume-led vs price-led verdict.** State which drives growth. Volume-led on a
   flat/competitive rate = durable but penetration-capped; price-led (rising rate)
   = fragile, mean-reverts. Distinguish genuine pricing power from mix effects
   (e.g. a take-rate rise caused by shedding low-rate volume is mix, not pricing).
3. **Competitor benchmarking on the SAME primitive.** Named peers' volume and
   growth (e.g. competitor TPV + growth), sourced. Is the subject gaining or
   losing share of the primitive? Flag any peer out-growing it. **Compare
   like-for-like only** — different firms measure differently (e.g. Meta reports
   impressions × price-per-impression, Google reports clicks × CPC; the volume/price
   *halves* are NOT comparable, only total revenue growth is). Pull competitor
   primitives EARLY, before the base is set.
4. **Penetration vs TAM and vs peers.** player volume ÷ TAM; where did comparable
   players decelerate? This sets the **ceiling on how high volume growth can stay**.
4b. **Per-engine and (if EM) per-country.** Decompose each engine on its own
   primitive. For a hyperinflationary geography, split growth into real volume vs
   inflation/FX (IAS 29 — note the monetary gain/loss); do not read nominal local
   growth as real.
5. **Forward REVENUE BUILD, bottom-up** from volume × price — a per-year,
   per-driver table (e.g. a demand-stack → units × ASP × share, or
   TPV × take × penetration), NOT a top-down CAGR. **This build is the revenue
   ENGINE the model carries forward** wherever the drivers are quantifiable:
   group revenue growth/CAGR is an OUTPUT that falls out of the roll-up, never a
   typed Y1→Y-end glide %. Show the roll-up to total revenue and reconcile it to
   the most recent actual. Flag every disclosure gap (e.g. regional take-rate
   non-disclosure) as a known limitation; where the drivers are NOT disclosable,
   fall back to a glide and say so.
6. **Hand-off to `/assumptions`** — state explicitly: (a) the penetration ceiling
   on volume growth, and (b) the take-rate assumption (flat / declining / rising)
   with its justification. These ground the glide endpoints.

A forward growth number not reconciled to volume × price × penetration is an
assertion, not an estimate — say so if the data won't support one.

**Smuggled-bull guard:** a segment CAGR set against a peer's *scale* and back-solved
to revenue (e.g. "we reach AWS's size in 10yr"), with no share-bridge, is an
assertion — require a NAMED share-bridge (logo wins / displacement) or relabel it as
"riding TAM" and move the unsupported version to the Bull.
