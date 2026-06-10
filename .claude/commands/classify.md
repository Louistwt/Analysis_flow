---
description: Classify the business type, select the valuation lens, name the operating drivers
---

Read `00-brief.md`.

Classify the subject as ONE of: (a) Compounder (b) Resource/mining
(c) Infrastructure/fee-based (d) Insurance (e) Cyclical industrial
(f) Early-stage growth. Decide from the economics, not the sector label.

Write `01-classification.md`:
1. **Classification** + two-sentence justification grounded in the economics.
2. **Valuation lens** that follows (see CLAUDE.md).
3. **Primary operating drivers / unit economics** — REQUIRED. Name the volume ×
   price × penetration primitives this business's growth must be decomposed into;
   this becomes the contract every downstream stage populates. By type:
   - Payments / transactional → TPV, take rate (bps), penetration (volume ÷ TAM), regional mix
   - SaaS → seats/usage, ARPU, NRR/churn, CAC/LTV
   - Bank / lender → loan book, NIM, cost-of-risk
   - Resource → volume, realised price, reserve life / cost curve
   - Hardware/semis → units, ASP, share, adoption/qualification
4. **Quality-gate questions** tailored to this business.
5. **What the DeepResearch prompt must prioritise** — incl. the driver time series
   and competitor primitives from (3).
6. **Open questions.**

If `00-brief.md` is too thin to classify, say what's missing and stop.