---
description: Run the methodology gate, then synthesise the final verdict
---

Read `framework/methodology-checks.md`, all stage files, `07-assumptions.md`, and
the fair-value outputs the user pastes back from the Sheet (incl. the SOTP build
if this is a multi-engine name).

## Step 1 — Methodology gate (BEFORE grading)

Run every check in `framework/methodology-checks.md`. PASS / FAIL / CAN'T-VERIFY
each, one line of evidence. In particular:
- Revenue cc + FX flat (#1); glide with group CAGR as output (#2); horizon by
  company type with a two-stage terminal (#3); fade endpoints grounded both ways
  (#4); Y-end vs terminal not conflated (#5); net cash single/stripped/signed (#6);
  TV sanity + implied multiple (#7); SBC consistent (#8).
- **Earnings-quality decomposition done (#9)** — operating vs fee vs net interest
  vs float income separated, not bundled at one multiple. For a hybrid this is
  required, not "minor."
- **Terminal margin is a mix-weighted output (#10)**, not asserted top-down.
- **SOTP survived to valuation (#11–#12).** If ≥2 material engines: is there a SOTP
  artifact with each engine on its own lens, the lender valued on book/ROE with
  capital consumption modelled (not a revenue-DCF)? Do the consolidated DCF and the
  sum-of-parts reconcile within a band? If they diverge, the SOTP is primary —
  state the gap.
- **Load-bearing primitive (#13).** Do NOT pass-to-grade if a material engine's
  load-bearing primitive is unsupported (e.g. a lender's cost of funds / NIM /
  loss curves). Grade only with an explicit, sized caveat.
- **EM treatment (#14–#15)** where flagged: per-country real-vs-inflation; value-
  weighted country-risk premium.

If any check FAILS, do not issue a verdict. State the failure and what to fix
first. Framing errors outrank data.

## Step 2 — Verdict (only if the gate passes)

Write `09-verdict.md`:
1. Quality grade — A / B / C / Fail, with the deciding facts (per engine if hybrid).
2. Valuation read — a *range* vs current price, citing the SOTP (primary) and the
   consolidated DCF (cross-check) bear/base/bull per share. Base is indicative.
3. Margin of safety — present or not, given quality and spread width.
4. Action — Buy now / Watchlist with target entry / Pass (give the band).
5. The three falsifiers that would trigger a review.
6. Where you disagree with the research, and why.
7. What still needs verifying before this is defensible (size any caveat).

Anchor on business performance and the assumption spread, not the point estimate.
Research, not advice.
