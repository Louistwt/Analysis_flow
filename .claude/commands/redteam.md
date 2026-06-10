---
description: Attack the thesis and assumptions (isolated red team)
---

Delegate to the **`skeptic` subagent** in a clean context. Give it
`07-assumptions.md`, `05-industry-map.md`, and `framework/methodology-checks.md`
only — withhold any bull framing.

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
4. **Steelman the market** — the strongest counter to the thesis, not a strawman.
5. **Underperformance test** — what must be true to lose to a global index over 10
   years?
6. **Recommended assumption changes** — concrete edits to `07-assumptions.md`
   (widen the spread, ground a floor, fix a framing error). List them so the user
   can re-run `/assumptions`.

The skeptic breaks the thesis but its bears must be grounded — an ungrounded low
number is as much an error as an ungrounded high one.