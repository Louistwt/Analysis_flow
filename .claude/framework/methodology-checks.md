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
3. **Match the horizon to company type, and model growth in TWO STAGES — not a
   single linear fade from Y1.** **The explicit window is ~10yr for a growth company
   and ~5yr for an already-mature one — it is NOT 10+5.** **Within the
   window use two growth stages:** Stage 1 (Y1–5, growth phase) holds near the Y1
   rate or fades *gently* — a company with real runway does not start decaying on
   day one; Stage 2 (Y6–10, mature phase) does the heavy fading, from the stage-1
   exit rate toward the terminal-entry rate. A single straight-line glide from Y1
   to Y10 **systematically under-states a growth-stage compounder** (it erodes the
   high rate immediately) — reserve the straight glide for already-mature names.
   The two CAGR inputs (yrs 1–5, yrs 6–10) define the two stages. **Residual runway is
   carried by the two-stage / H-model TERMINAL — never by steepening the in-window fade,
   and never by extending the window.** Extending it double-counts: the stub years grow
   *and* the terminal then fades from that inflated rate. (AVGO 2026-08: a 15yr window
   used on a fabless name with +$35bn of Y1 FCFF — the exception below plainly did not
   apply — and the change was logged as a *correction*. ~$11/share of phantom value.)
   *Exception — build-ahead / capex-super-cycle names ONLY:* if near-term FCF is
   suppressed for many years by a build-ahead (8+ yrs negative FCF), the explicit
   window MUST extend to ~15yr (10+5) to capture the recovery — otherwise the
   J-curve recovery is dumped into the terminal (see #7 and
   `capex-supercycle-hybrids.md`).

## Growth & fade discipline — both directions

4. **No ungrounded numbers in either direction.** A low fade endpoint without
   evidence of deterioration is as much an error as an ungrounded bear. Anchor
   late-stage growth to mature comparables (a generous ceiling, not a floor).
5. **Nothing may still be in transition at the end of the window.** Y-end growth can
   stay above GDP; the terminal perpetual rate must be ≤ long-run nominal GDP. Bridge
   the gap with a two-stage terminal; never capitalise an above-trend final year into
   perpetuity. **This applies to EVERY driver, not just growth:** a share, penetration
   or margin glide still climbing in the final year leaks that transition into the
   terminal, because the terminal reads the year-N rate. Land each driver on an explicit
   **plateau** inside the window, so the terminal grows with the market alone. (AVGO
   2026-08: a custom-silicon share climbing 2.3pp/yr with no plateau left year-10 growth
   at 17% instead of 5%, and pushed TV to 71% of EV.)

## EV → equity bridge

6. **Net-cash sign, single t0 figure, strip first.** Add net cash / subtract net
   debt with the right sign. One t0 figure across all scenarios. Strip settlement
   balances, customer funds, credit-book funding, and regulatory/restricted
   capital before computing it; gross cash is not distributable cash.

## Terminal value & cost structure

7. **Terminal value sanity.** Back out the implied terminal exit multiple
   (EV/NOPAT at the final year); sanity-check vs comparables. Keep TV well under
   ~65% of EV — a longer explicit horizon lowers TV-reliance. If TV-reliance is
   high because near-term FCF is *suppressed by a build-ahead* (not because the
   business is genuinely terminal-weighted), that is a HORIZON problem — extend the
   window (#3 exception), don't accept it.
8. **SBC / dilution consistency.** Model share-count growth or treat SBC as a cash
   cost — not neither. (If SBC is already in the EBIT you use, no add-back needed.)
   **If owner earnings are built from OCF, OCF has already added SBC back as
   non-cash — so DEDUCT SBC from OCF (it is a real cost) and use DILUTED shares.**
   OCF without the SBC deduction and with basic shares double-benefits: an inflated
   cash figure AND no dilution charge.
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

## Scenario construction

16. **Scenarios are driver-narrative-constructed, not uniform multipliers.** Each
    of Bear / Base / Bull names which driver(s) break and what has to be true;
    related drivers move TOGETHER within a scenario (a digestion Bear moves volume,
    pricing, and the discount rate in concert). A spread built by multiplying every
    input by a constant (base × 0.7 / 1.3) is mechanical noise, not a risk model —
    reject it. Each broken driver should map to a falsifier.
17. **Revenue is built, not glided, where drivers are quantifiable.** The forecast
    revenue line is the bottom-up build (volume × price × share, per year), and
    group growth/CAGR is an OUTPUT of it — a smoothed Y1→Y-end glide is the fallback
    only when the drivers aren't disclosable. A glide that was never reconciled to a
    unit-economics build is an assertion.

## Discount rate & cost of capital

18. **Cash-flow ↔ discount-rate consistency (the framing error that most often
    mis-values a financial).** Discount FCFF at WACC and FCFE at cost of equity —
    never cross them. Discounting equity flows (FCFE / residual income) at WACC
    understates the rate and *overvalues*; discounting unlevered FCFF at cost of
    equity overstates the rate. Do the net-debt bridge exactly **once**: subtract
    net debt only after an FCFF→EV valuation. An FCFE / residual-income / justified-
    P/B valuation already yields **equity** — subtracting net debt again double-
    counts. Confirm the method `/classify` selected (item 2b) is the one actually
    run, per engine, and that its currency matches the cash-flow currency.
19. **Cost-of-capital contract — build it, don't scrape it.** WACC/CoE from named
    components: risk-free (which bond, which date, in the cash-flow currency), ERP
    (source, e.g. Damodaran), beta (source, window, index; use **through-cycle
    beta**, not a spot beta inflated by a recent run-up; unlever/relever if the
    subject's leverage differs from the peer set), value-weighted country-risk
    premium for EM (#15). Reject any single screen-scraped WACC. For a terminal-
    heavy name the discount rate is usually the dominant swing — run the
    sensitivity and frame the read as "fair value at hurdle X," not a point.

## NOPAT, returns, and reinvestment

20. **Capitalise NOPAT, not EBIT, and build it on OPERATING earnings only.** The
    DCF discounts NOPAT-derived FCFF (NOPAT = operating-EBIT × (1 − cash tax
    rate)); name NOPAT as an explicit line so the tax and the base are visible.
    Two failure modes: (a) computing NOPAT off a *bundled* EBIT that includes fee /
    net-interest / float income capitalises different-durability streams at the
    operating multiple (ties to #9); (b) using the book-effective tax rate. Tax is
    a **glide input** — current-effective → normalised marginal *cash* rate (IP-box,
    tax assets, one-offs distort the spot rate). Keep EV/EBIT (a pre-tax comp)
    distinct from EV/NOPAT (the intrinsic terminal check, #7).
21. **Reinvestment ↔ ROIC ↔ growth must tie (internal-consistency gate).**
    g ≈ reinvestment rate × ROIC. The revenue/growth path and the capex + ΔWC + M&A
    path are NOT independent dials — the assumed growth must be *funded* at a
    credible incremental ROIC. Compute the growth implied by the modelled
    reinvestment and reconcile it to the assumed growth; a mismatch means either
    free growth (implied ROIC absurd) or under-funded growth. Fix by moving one
    side, not by ignoring the gap.
22. **Growth only creates value above the cost of capital.** Check ROIC vs WACC
    (ROE vs CoE for a financial). Where incremental ROIC ≤ the discount rate,
    growth adds no value (or destroys it) and must NOT be rewarded with a premium;
    a high ROIC that cannot be reinvested is a cash cow, not a compounder (CLAUDE.md
    quality gate).

## Base year & terminal returns

23. **Normalise the starting (Y0) base — no peak/trough anchor, and strip one-off
    mix distortions from blended metrics.** Start off a mid-cycle year, not a spot
    high or low. **A single large customer entering or exiting distorts a blended
    rate/margin:** Adyen's blended take rate printed 17.0 bps only because a large
    *low-take* customer had just exited (mechanically lifting the blend) — the clean
    level was ~16. Decompose and anchor on the clean level, not the flattered/
    depressed print; a base distortion propagates through every forecast year.
    Mandatory for cyclicals/commodities (mid-cycle price), general otherwise.
24. **Fade the RETURN in the terminal, not just growth.** Excess returns compete
    away; incremental ROIC should fade toward WACC across the two-stage terminal
    for a high-quality compounder. A terminal holding ROIC >> WACC in perpetuity
    overstates value (growth fade #4/#5 handles the numerator; this handles the
    return).

## Triangulation — the DCF is not the only read

25. **Reverse-DCF.** Back out what the *current price* implies for growth / margin /
    take rate, and judge whether that is beatable — the primary framing for a
    high-multiple compounder (CLAUDE.md). Use own-model expectations, never banned
    consensus.
26. **Relative-valuation cross-check.** Reconcile the intrinsic output to a peer set
    (same-primitive economics) and the company's own multiple history. A DCF never
    sanity-checked against what the market pays for comparable economics is fragile;
    a large divergence is a flag to explain, not to ignore.

## Profit line & acquisition discipline

27. **Never mix profit lines; label which line every input is.** Gross, operating,
    EBITDA and owner earnings are different lines — an input, its comparable and any
    management statement about it must all refer to the same one. Companies
    often headline **EBITDA** (Adyen 53%) while the DCF capitalises **EBIT** (47%) —
    the gap is D&A. Bumping an "EBIT margin" input toward the EBITDA headline
    (because the headline *looks* higher, or because a strong quarter tempts an
    upgrade) double-counts D&A and inflates value by the whole depreciation load.
    Compare like-for-like: an EBIT assumption against reported EBIT, an EBITDA
    assumption against EBITDA, owner earnings against owner earnings.
    **A management warning names a line — apply it to that line only, and never quote
    half of it.** (AVGO 2026-08: the 10-Q says AI racks *"will likely **increase our
    operating margin** but compress or lower future **gross** margin."* Only the
    gross-margin half was carried forward, and it was applied to an **operating**-margin
    input — fading it against an explicit statement in the opposite direction. ~$9/share.)
    This trap bites hardest when *good* news invites a reflexive margin bump — resist it.
28. **Serial acquirer: M&A is reinvestment (off-balance-sheet R&D).** Check whether
    the company grows by **frequent acquisition** — a roll-up, or buying capability
    instead of building it. If so, **acquisition spend is growth reinvestment:
    include it in the capex/reinvestment line**, because the acquired revenue AND its
    D&A/amortisation are already in the P&L. Gliding capex *down* to lift FCF while
    the growth is acquisition-funded **double-counts** — you keep the bought growth
    and its amortisation drag but drop the cash that produced it, manufacturing free
    FCF. Fold M&A into the reinvestment↔ROIC↔growth tie (#21); organic capex alone
    understates a serial acquirer's true reinvestment rate. **And the acquired revenue
    must EARN a margin:** if M&A cash is charged to reinvestment, the revenue it buys has
    to carry a segment margin as well as its share of corporate cost — otherwise the model
    pays for growth and books none of it. (AVGO 2026-08: acquired revenue sat inside group
    revenue carrying full SBC, amortisation and working-capital drag with **zero EBIT** —
    $67/share, the single largest error of the run.) Watch this as a company *becomes* an
    acquirer (e.g. Adyen's first deals — Talon.One + Orb, H1 2026).

## Consistency gates (29–31) — added 2026-08-18

29. **★ COMPETITIVE SHARE MUST SUM TO ≤100%.** Wherever a market-share assumption
    exists — for the subject or in any TAM build — **name the competitive set and
    show the shares summing across it.** Every company's model assumes *its* subject
    gains share; summed across the set those assumptions are frequently collectively
    impossible, and nothing in a single-company model catches it. If the sum exceeds
    100%, at least one player's assumption is wrong and the model must say which and
    fix it. Cheapest, highest-yield check in this document.
30. **TAM ↔ (units × ASP) CONTRADICTION CHECK.** Derive the market size **twice, from
    independent sources**: (a) top-down from what participants and bodies state, and
    (b) bottom-up as units × ASP from the driver build. State both numbers and the
    gap. A bottom-up build that has never been checked against an independent TAM is
    unvalidated, and a TAM accepted without a unit×ASP reconciliation is an assertion.
    Where physical constraints exist (capacity, a scarce input, power), add them as
    further independent ceilings and report **which constraint binds** — that answers
    whether the market is supply- or demand-limited, which sets the entire pricing path.
    **Where your revenue driver is someone else's capex, funding capacity is one of those
    ceilings: test capex ÷ operating cash flow per customer out to the forecast year, and
    check what it leaves for the dividends and buybacks they have historically defended.**
    (AVGO 2026-08: Big-4 capex is 68% of OCF; a flat 16%/yr for four years put it at
    81–91%, which breaks the buyback. Forcing the decay was worth −$42/share.)
31. **ROIC AND INVESTED CAPITAL — ONE DEFINITION, STATED EVERY TIME.**
    `ROIC = EBIT × (1 − marginal tax rate) ÷ invested capital`, with a **flat marginal
    rate (default 25%)** rather than the noisy effective rate, and
    `invested capital = Inventory + Accounts receivable + Intangibles (INCLUDING goodwill)
    + PP&E (INCLUDING operating-lease right-of-use assets) − Accounts payable − capital
    lease obligations`.
    Show the formula and the inputs, not just the answer. **Issuers label these lines
    differently** — read for the economic meaning rather than matching a caption, and
    say which caption you mapped to which term. Including goodwill is deliberate: a
    serial acquirer that excludes it flatters its own returns (ties to #28).

## Model-construction gates (32–33)

32. **RUN TWO DCFs — reported capex and MAINTENANCE capex — and read the gap.**
    Build the model once on reported capex and once with **maintenance capex** on the
    Greenblatt approach (the capex required to sustain current unit volumes and
    competitive position, distinct from capex that buys growth). **The difference
    between the two valuations IS the growth investment**, made visible instead of
    asserted. Reconcile that implied growth investment against the reinvestment ↔ ROIC
    ↔ growth tie (#21): if the model claims growth that the maintenance-capex version
    shows is not being funded, the growth is unsupported. For a serial acquirer,
    acquisition spend belongs in the growth half, not the maintenance half (#28).
    **For an asset-light business the gap is near-zero and tells you little about growth
    — but it tells you something else worth having: where the growth came from.** (AVGO
    2026-08: gap $12/share = 4% of value on capex of 1.2% of revenue. The reading that
    mattered was that a two-decade roll-up's AI growth is **organic, not bought**.)
33. **REVERSE-DCF, STATED AS A REQUIRED OPERATING ASSUMPTION.** Express the reverse-DCF
    as: **"at the current price, what revenue CAGR (and terminal margin) must the
    business deliver over the explicit horizon?"** — then judge whether that path is
    plausible against the driver build, the TAM ceiling (#30) and the share check (#29).
    This is strictly better than comparing multiples: it converts price into a
    *testable operating claim* in the same units as our own forecast, and it is the only
    form in which price is permitted to enter before the final margin-of-safety step
    (CLAUDE.md prime directive #4).

## Discount-rate presentation (34)

34. **COMPONENT-BUILT REASONING, SWEPT PRESENTATION, PER ENGINE.** Check #19's
    component-built cost of capital (Rf + ERP + through-cycle beta) remains the
    **reasoning** step — it forces the question of *why* a given return is required.
    But **present the output as a sensitivity sweep** (default 8 / 9 / 10 / 11 / 12%)
    rather than as a single false-precision figure, and **state where in that range the
    component build lands and why**. Beta is noisy and backward-looking; a sweep is
    honest about that without abandoning the reasoning.
    **For a multi-engine hybrid, sweep EACH ENGINE SEPARATELY.** A single blended sweep
    across engines of genuinely different risk destroys the per-engine distinction that
    is the entire purpose of an SOTP (#11–13) — a contracted software annuity and a
    programme-concentrated ASIC business cannot share a rate. Terminal growth stays
    ≤ long-run nominal GDP (#23), applied consistently across the sweep.

## How to apply

Run all of the above before trusting any output. Treat only `hard` inputs as Base
movers; widen the spread for soft ones. The newest and most-missed: terminal
margin as an output (10), the SOTP surviving to valuation with the lender valued
as a lender (11–13), per-country / value-weighted EM treatment (14–15), and the
discount-rate/cash-flow framing block (18–24) — the right *method* for the
business (18), NOPAT-not-EBIT on operating earnings (20), and growth that ties to
reinvestment and clears the cost of capital (21–22). Always close with the two
triangulations (25–26): the intrinsic read is not trustworthy until the reverse-
DCF and a relative-value cross-check agree with it or the divergence is explained.
And the framing traps (27–28): the profit line must be consistent (EBIT vs EBITDA,
27) and a serial acquirer's M&A must sit in reinvestment (28). For a single-engine,
single-geography name, 11–15 simply don't trigger; 18–28 always do.

The consistency and construction gates (29–34) are newer and are the ones most often
skipped: the share sum (29) and the TAM reconciliation (30) catch errors no
single-company model can see; the ROIC definition (31) stops it being re-derived
differently every run; the twin DCFs (32) make growth investment visible rather than
asserted; the reverse-DCF phrasing (33) is the only permitted pre-verdict use of price;
and the swept, per-engine discount rate (34) replaces false precision without losing
the reasoning behind the rate.

### 30b. ★ The TAM reconciliation must run FORWARD, not just at t0

#30 is routinely applied to the base year and then forgotten. **Unwind the TERMINAL-year
revenue back through the demand chain and state what it implies about the market.** A typed
fade can look reasonable year by year and still imply an absurdity at the end.

Where a market is growing fast, do not type the company's growth at all: build
`market × segment share × company share` forward and let revenue be the OUTPUT — the
contentious assumption then sits on the face of the model instead of inside a decay rate.

(AVGO 2026-08: a Base fading E2 12%→6% implied **AI datacentre capex compounding at 4.0%/yr
for a decade**, below nominal GDP. Correcting it moved the valuation +43%.)

