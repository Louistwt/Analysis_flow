---
description: Classify the business type, select the valuation lens, name the operating drivers
---

Read `00-brief.md`.

Classify the subject. It may be a SINGLE engine (one of: Compounder, Resource,
Infrastructure, Insurance, Cyclical, Early-stage) OR a **multi-engine hybrid**
(e.g. marketplace + payments + lending + ads). Decide from the economics.

Write `01-classification.md`:
1. **Classification** + two-sentence justification grounded in the economics. If
   hybrid, list the engines and each engine's share of revenue/value.
2. **Valuation lens + basis PER ENGINE.** Name the lens for each (see CLAUDE.md).
   Critically, a **lending engine** is valued on loan book × NIM × cost-of-risk →
   book/ROE (residual income or justified P/B at its own cost of equity), with the
   equity capital it consumes modelled — NOT a revenue-DCF.
3. **Primary operating drivers / unit economics** — REQUIRED, per engine. Payments
   → TPV × take rate × penetration; marketplace → GMV × take rate; lender → loan
   book × NIM × cost-of-risk + cost of funds, cohort loss curves, capital ratios;
   ads → impressions × CPM; SaaS → seats/usage × ARPU × NRR.
4. **If ≥2 engines have materially different lenses (especially a lender):**
   require a **SOTP valuation artifact downstream**, and state explicitly that the
   consolidated DCF is a **cross-check, not the primary**. The split must survive
   to valuation, not collapse into one EBIT / one WACC / one terminal multiple.
5. **If an EM / multi-country footprint** (esp. a hyperinflationary geography):
   flag that growth needs a per-country real-vs-inflation decomposition and a
   value-weighted (not revenue-weighted) country-risk premium.
5b. **If a build-ahead / capex-super-cycle engine** (heavy infra/AI capex built
   AHEAD of revenue — hyperscaler cloud, AI compute): flag it and point downstream
   to `framework/capex-supercycle-hybrids.md`. /assumptions must then glide capex
   AND D&A (not flat), extend the horizon to ~15yr (10+5), use owner-earnings,
   allocate the build-ahead capex to the engine that owns the backlog, and treat
   the discount rate as the dominant swing.
6. **Quality-gate questions** tailored to this business.
7. **What the DeepResearch prompt must prioritise** — incl. the per-engine driver
   time series, competitor primitives, and (if a lender) its funding/capital data.
8. **Open questions.**

If `00-brief.md` is too thin to classify, say what's missing and stop.
