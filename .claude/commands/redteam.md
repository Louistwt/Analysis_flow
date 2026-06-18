---
description: Attack the thesis and assumptions (isolated red team)
---

Delegate to the **`skeptic` subagent** in a clean context. Give it the evidentiary
base it needs to mount GROUNDED attacks — `07-assumptions.md`, the SOTP build
(`07b-sotp.md` if present), `06b-growth-decomposition.md` (the growth attack MUST
target a primitive from here), `06-tech.md` (competitor/structural data),
`05-industry-map.md`, `04c-primary-financials.md` (the hard numbers),
`framework/methodology-checks.md`, and `framework/capex-supercycle-hybrids.md` (if a
build-ahead name) — but withhold the bull NARRATIVE; the skeptic attacks the numbers,
it is not persuaded by the framing.

Write `08-redteam.md`:

1. **Three credible bear cases** — each: the value-destroying mechanism, the
   leading indicator, rough probability.
2. **Attack the four swing inputs** (Y1 growth, Y-end growth, terminal EBIT
   margin, WACC). For each: defensible? plausible adverse value? what evidence
   would justify it?
   The growth attack must target a SPECIFIC primitive — volume, price/take rate,
   or share — grounded in the 06b decomposition and competitor data, not a
   generic low CAGR. (e.g. "take rate compresses as Stripe undercuts", or
   "volume growth halves as penetration saturates" — with the peer evidence.)
3. **Grounded-fade test, both directions (do not skip).** Every bear number must
   trace to *observable deterioration*, not invented pessimism — AND the bear's
   fade endpoint is held to the same standard as the base's:
   - A revenue CAGR below industry TAM growth must name the share-loss evidence
     (churn, lost logos, displacement). No evidence = unfounded.
   - Anchor bear floors to mature comparables (mature payment networks still
     compound double-digit despite duopoly rivalry); a floor implying worse-than-
     mature decline must be justified by something specific to this name.
   - Flag any bear input that is just "a low number" with no deterioration story —
     it is as much an error as an ungrounded bull number.
   - Check the bear hasn't been manufactured by over-steepening the in-window fade
     or collapsing the terminal, rather than by a real deterioration thesis.
3b. **Build-ahead / terminal-heavy attacks (see `framework/capex-supercycle-hybrids.md`):**
   - **Attack the discount rate explicitly** — for a terminal-heavy name WACC is the
     dominant swing; run the WACC bridge and show the adverse value at a higher hurdle.
   - **Smuggled-bull check** — did a base revision lift the answer through the
     least-supported inputs? Is a segment CAGR set against peer *scale* with no
     share-bridge? Move it to the Bull.
   - **Margin-toward-a-falling-target** — is the base gliding "toward peer margins"
     while those peers are themselves compressing (AI-depreciation)? A relative cost
     edge against a falling absolute is not a rising margin. Flag double-counted
     tailwinds (lower-margin hardware mix is growth-up / margin-down).
   - **Re-center the spread** — flag a bear barely below the base (it understates risk).
4. **Steelman the market** — the strongest counter to the thesis, not a strawman.
5. **Underperformance test** — what must be true to lose to a global index over 10
   years?
6. **Recommended assumption changes** — concrete edits to `07-assumptions.md`
   (widen the spread, ground a floor, fix a framing error). List them so the user
   can re-run `/assumptions`.

The skeptic breaks the thesis but its bears must be grounded — an ungrounded low
number is as much an error as an ungrounded high one.