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
  state the gap. **Confirm the consolidated cross-check was re-run on the latest
  base (it goes stale after a revision).**
- **Build-ahead horizon (#3/#7).** For a capex-super-cycle name, high TV-reliance
  from *suppressed near-term FCF* is a HORIZON problem — confirm the ~15yr window was
  used, not a 10yr window that dumps the J-curve recovery into the terminal.
- **Load-bearing primitive (#13).** Do NOT pass-to-grade if a material engine's
  load-bearing primitive is unsupported (e.g. a lender's cost of funds / NIM /
  loss curves). Grade only with an explicit, sized caveat.
- **EM treatment (#14–#15)** where flagged: per-country real-vs-inflation; value-
  weighted country-risk premium.
- **Discount-rate method + cost of capital (#18–#19).** The rate matches the
  cash-flow definition (FCFF→WACC / FCFE→CoE / residual income / APV), net debt is
  bridged exactly once, and the rate is component-built (through-cycle beta), not
  scraped.
- **NOPAT + returns (#20–#22).** Value rests on NOPAT (operating-EBIT × cash tax),
  not bundled EBIT; growth ties to reinvestment × ROIC; incremental ROIC clears the
  discount rate (else growth earns no premium).
- **Base year + terminal return (#23–#24).** Y0 normalised (mid-cycle); incremental
  ROIC fades toward the discount rate in the terminal.

If any check FAILS, do not issue a verdict. State the failure and what to fix
first. Framing errors outrank data.

## Step 1b — Triangulate the intrinsic read (methodology #25–#26)

The DCF/SOTP output is one read, not the answer. Before grading, cross-check it two ways:
- **Reverse-DCF.** Back out what the *current price* implies for growth / margin /
  take rate. State it plainly ("at €X the market is paying for Y% growth at Z%
  margin") and judge whether that is beatable. This is the primary framing for a
  high-multiple compounder — own-model expectations only, never banned consensus.
- **Relative-valuation cross-check.** Put the intrinsic output beside a peer set on
  same-primitive economics (EV/NOPAT, EV/EBIT, growth-adjusted) and the company's
  own multiple history. If intrinsic and relative diverge materially, explain why
  (genuine mispricing vs a model error) — do not bury it. Note the peer scorecard
  the cross-check needs (competitor volume/growth/margin/multiple) if it is missing.

## Step 2 — Verdict (only if the gate passes)

Write `09-verdict.md`:
1. Quality grade — A / B / C / Fail, with the deciding facts (per engine if hybrid).
2. Valuation read — a *range* vs current price, reconciling **all methods that
   apply**: the DCF bear/base/bull per share, the **reverse-DCF** (what the price
   implies — the primary lens for a compounder), the **relative-value** read (peers
   + own history) from Step 1b, and the **SOTP** if a hybrid. State them side by
   side and say which wins where they diverge (SOTP over consolidated for a hybrid;
   reverse-DCF frames "is it cheap"). **Frame the discount rate as a RANGE — "fair
   value at hurdle X to Y," not a point** (the rate is usually the dominant swing).
   Treat notable-investor activity as *disconfirming data to stress your hurdle*,
   not confirmation.
3. Margin of safety — present or not, given quality and spread width.
4. Action — Buy now / Watchlist with target entry / Pass (give the band).
5. The three falsifiers that would trigger a review.
6. Where you disagree with the research, and why.
7. What still needs verifying before this is defensible — **draw this down from the
   `_open-questions.md` register**: resolve what the run closed, carry the live
   items (sized by how much each could move the verdict), and hand the survivors to
   `/thesis` for the watch list.

## Step 3 — The coverage report (the deliverable)

The staged `.md` files are working papers; the *deliverable* is a synthesised
**initiating-coverage report** — `10-coverage-report.md` (or a Drive Doc/Sheet). It
is a complete investment document, not a recap. Include:
- **Header block:** rating, reference price, intrinsic-value target + range,
  valuation basis (DCF / Reverse-DCF / Relative / SOTP), and a key-data box
  (ticker, shares, net cash, base- and terminal-year revenue, revenue CAGR, margin
  path, discount-rate range).
- **Investment thesis** as a few named pillars (structural driver / moat /
  operating leverage / valuation), one paragraph each.
- **Financial summary** — the *explicit* multi-year forecast (not just a CAGR):
  revenue by segment, EBIT + margin, FCFF, and the key primitive (TPV/GMV/units) at
  ~2-year intervals across the window.
- **Risk matrix** — categorised (company / industry / financial / macro / data),
  each risk one line, mapped to the falsifiers.
- **Company description + history + the flywheel/moat map.**
- The method reconciliation from Step 2 and the falsifiers.

Keep the numbers identical to the model; the report *presents* the verdict, it does
not re-derive it. Anchor on business performance and the assumption spread, not the
point estimate. Research, not advice.


---

## Added 2026-08-18 — additional gates before any grade

- **★ Share sum ≤ 100% (methodology #29).** Reject the model if any share assumption exists
  without a named competitive set and a stated sum. This catches the error no single-company
  model can see.
- **★ TAM ↔ units × ASP reconciliation (methodology #30).** Both numbers must be stated, with the
  gap and the binding constraint named.
- **★ Reverse-DCF, phrased as a required operating assumption (methodology #33).** State it as:
  *"at the current price, what revenue CAGR and terminal margin must this business deliver?"*
  Then judge that path against the driver build, the TAM ceiling and the share check. This is the
  ONLY form in which price may enter before the final margin-of-safety step.
- **Twin-DCF gap (methodology #32).** Read the difference between the reported-capex and
  maintenance-capex valuations as the implied growth investment, and check it is actually funded.
- **ROIC stated with its formula (methodology #31)**, not just its value.
