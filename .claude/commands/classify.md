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
2b. **Discount-rate METHOD per engine — SELECT it, do not default to WACC.** State
   the method and the cash-flow definition it discounts; they must match (gated by
   methodology-checks). Choose per engine from:
   - **FCFF → WACC** (unlevered FCF → enterprise value, then −net debt → equity).
     The default for an operating business with a roughly *stable* capital
     structure — compounders, payments, resources, most hardware/SaaS.
   - **FCFE → cost of equity** (flows to equity after interest/debt → equity
     value *directly*, no net-debt bridge). Use for **financials — banks,
     insurers, lenders** — where leverage IS the raw material and "net debt / EV"
     is meaningless. Often expressed as **residual income / justified
     P/B = (ROE − g)/(CoE − g)** on book.
   - **APV** (value unlevered at the asset return + PV of tax shields − distress,
     each discounted separately). Use when the **capital structure changes
     materially over the horizon** — deleveraging infrastructure, a debt-funded
     build-ahead that pays down, LBO-like names, or large time-varying tax
     attributes (NOLs). WACC's constant-weight assumption breaks here; APV is
     cleaner. Flag for `framework/capex-supercycle-hybrids.md`.
   For a **hybrid**, engines can carry DIFFERENT methods (a lender engine at its
   own CoE, the commerce engine at WACC) — you cannot collapse them to one
   discount rate. Name the currency of each rate; it must match the cash-flow
   currency.
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
5c. **If a serial / frequent acquirer** (roll-up, or buys capability instead of
   building it): flag it. M&A is then growth reinvestment (off-balance-sheet R&D) —
   `/assumptions` must model acquisition spend in the capex/reinvestment line, not
   let capex glide down while acquisition-funded growth (and its amortisation) stays
   in the P&L (methodology #28). Also flag a company that is *becoming* an acquirer.
6. **Quality-gate questions** tailored to this business.
7. **What the DeepResearch prompt must prioritise** — incl. the per-engine driver
   time series, competitor primitives, and (if a lender) its funding/capital data.
8. **Seed the disclosure-gap register.** Start `_open-questions.md` at the company
   root (the single living register every stage appends to and `/verdict` draws
   down — see CLAUDE.md) with the open items this classification raises. Do not use
   a per-stage open-questions list.

If `00-brief.md` is too thin to classify, say what's missing and stop.
