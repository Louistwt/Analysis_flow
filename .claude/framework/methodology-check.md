# Methodology checks — framing dominates the output

Across real valuations, the inputs that swing the per-share answer most are
**methodology/framing errors, not individual data points**. A correctly sourced
number in a mis-framed model still gives the wrong verdict. Run these before
trusting any DCF output. Getting the data right is necessary but not sufficient.

## Revenue construction

1. **Project constant-currency, hold FX flat.** Reported growth bakes a one-off
   FX move into every forward year. Grow the actual base at the cc rate.
2. **Glide each segment year-by-year; let group CAGR be an output.** Flat blocks
   over-state fast segments and ignore mix shift. Glide from a Y1 input to a
   Y-end input; group CAGR falls out.
3. **Match the explicit horizon to company type — not a longer window.** ~10yr
   growth / ~5yr stable. Carry residual runway with a two-stage / H-model
   terminal, never by steepening the in-window fade or extending the window.

## Growth & fade discipline — both directions

4. **No ungrounded numbers in either direction.** A low fade endpoint without
   evidence of deterioration is as much an error as an ungrounded bear. Anchor
   late-stage growth to mature comparables (a generous ceiling, not a floor).
5. **Y-end growth is not terminal growth.** Y-end can stay above GDP; the terminal
   perpetual rate must be ≤ long-run nominal GDP. Bridge the gap with a two-stage
   terminal; never capitalise an above-trend final year into perpetuity.

## EV → equity bridge

6. **Net-cash sign, single t0 figure, strip first.** Add net cash / subtract net
   debt with the right sign. One t0 figure across all scenarios. Strip settlement
   balances, customer funds, credit-book funding, and regulatory/restricted
   capital before computing it; gross cash is not distributable cash.

## Terminal value & cost structure

7. **Terminal value sanity.** Back out the implied terminal exit multiple
   (EV/NOPAT at the final year); sanity-check vs comparables. Keep TV well under
   ~65% of EV — a longer explicit horizon lowers TV-reliance.
8. **SBC / dilution consistency.** Model share-count growth or treat SBC as a cash
   cost — not neither. (If SBC is already in the EBIT you use, no add-back needed.)
9. **Earnings-quality decomposition (NOT "minor").** Separate operating income
   (commerce/marketplace EBIT) from fee income, net interest income, and
   float/investment income. These have different durability and cyclicality —
   never capitalise them at one terminal multiple. Anchoring growth on a headline
   profit/EPS line that bundles a rate-sensitive or one-off non-operating stream
   mis-prices the business (Adyen finance income was 20–28% of pre-tax; a fintech
   hybrid bundles four such streams — this is a required step, not a footnote).

## Margins as outputs

10. **Terminal margin is a mix-weighted output, not a top-down assertion.** For a
    mix-driven or multi-segment business, terminal EBIT margin =
    Σ(segment margin × segment weight) at the terminal year — built from the same
    engine model and reconciled to history, exactly as group revenue CAGR is an
    output of the glide. Asserting it top-down (it is usually the #1 swing input)
    is the margin version of the flat-CAGR error.

## Multi-engine / sum-of-the-parts (when /classify flags ≥2 material engines)

11. **The SOTP split must survive to valuation.** Value each material engine on
    its own lens and carry the split THROUGH to valuation; the consolidated DCF is
    a cross-check, never the primary. A **lender engine** is valued on loan book ×
    NIM × cost-of-risk: model the equity capital it consumes (distributable FCFE =
    net income − increase in required equity capital to fund book growth at its
    capital ratio), and value the stream via residual income or a justified
    P/B = (ROE − g)/(CoE − g) at the **arm's own cost of equity**, not group WACC.
    Never capitalise a loan book as recurring revenue inside a revenue-DCF.
12. **SOTP reconciliation.** Sum the parts and compare to the consolidated DCF;
    they should agree within a band. Material divergence is a flag — and for a
    lender-containing hybrid the SOTP is primary and wins, because the consolidated
    DCF is the thing that mis-frames the lender.
13. **Load-bearing-primitive gate.** Do not pass-to-grade if a material engine's
    load-bearing primitive is unsupported — for a lender that means blended cost of
    funds, NIM, cohort loss curves, funding mix, and capital ratios (as essential
    as TPV is for payments). Grade only with an explicit, sized caveat.

## Emerging markets / multi-country (when /classify flags an EM footprint)

14. **Per-country real-vs-inflation decomposition.** A group constant-currency
    number is too coarse for a hyperinflationary geography. Decompose into real
    volume vs inflation/FX per country (under IAS 29, include the monetary
    gain/loss note); do not read nominal local growth as real growth.
15. **Value-weighted, not revenue-weighted, country-risk premium.** Weight the
    WACC country-risk premium by each geography's share of *value*, not revenue —
    revenue-weighting over-charges a small but fast-growing risky geography.

## How to apply

Run all of the above before trusting any output. Treat only `hard` inputs as Base
movers; widen the spread for soft ones. The newest and most-missed: terminal
margin as an output (10), the SOTP surviving to valuation with the lender valued
as a lender (11–13), and per-country / value-weighted EM treatment (14–15). For a
single-engine, single-geography name, 11–15 simply don't trigger.
