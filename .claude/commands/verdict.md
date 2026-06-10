---
description: Run the methodology gate, then synthesise the final verdict
---

Read `framework/methodology-checks.md`, all stage files (01–08), `07-assumptions.md`,
and the fair-value outputs the user pastes back from the Google Sheet.

## Step 1 — Methodology gate (BEFORE grading)

Run every check in `framework/methodology-checks.md` against the final
assumptions and the Sheet output. PASS / FAIL / CAN'T-VERIFY each, one line of
evidence. In particular:
- Revenue projected constant-currency, FX flat? (#1)
- Growth a year-by-year glide with group CAGR as an output, not flat blocks? (#2)
- **Horizon matches company type?** ~10yr growth / ~5yr stable. If final-year
  growth is well above terminal, is the runway carried by a two-stage / H-model
  terminal rather than lost to a single Gordon jump or faked by an over-steep
  in-window fade? (#3)
- **Fade endpoint grounded, both directions?** Is the Y-end / bear growth anchored
  to mature comparables and evidence, or is it an ungrounded low number? (#4)
- **Y-end vs terminal not conflated?** Terminal perpetual rate ≤ nominal GDP;
  Y-end may be higher. No above-trend year capitalised straight into perpetuity. (#5)
- Net cash single, correct sign, settlement balances stripped? (#6)
- Implied terminal exit multiple sane; TV not an excessive % of EV? (#7)
- SBC treatment consistent; operating vs non-operating income separated? (#8, #9)

If any check FAILS, do not issue a verdict. State the failure and what to fix in
`/assumptions` or the Sheet first. Framing errors outrank data here.

## Step 2 — Verdict (only if the gate passes)

Write `09-verdict.md`:
1. Quality grade — A / B / C / Fail, with the deciding facts.
2. Valuation read — cheap / fair / expensive as a *range* vs current price, citing
   the Sheet's bear/base/bull equity value per share. Base is indicative only.
3. Margin of safety — required given quality and spread width; present or not?
4. Action — Buy now / Watchlist with target entry / Pass (give the band).
5. The three falsifiers that would trigger a review.
6. Where you disagree with the research, and why.
7. What still needs verifying before this is defensible.

Anchor on business performance and the assumption spread, not the point estimate.
Research, not advice.