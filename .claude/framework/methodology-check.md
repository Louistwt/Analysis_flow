# Methodology checks — framing dominates the output

Across real valuations, the inputs that swing the per-share answer most are
**methodology/framing errors, not individual data points**. A correctly sourced
number in a mis-framed model still gives the wrong verdict. Run these before
trusting any DCF output. Getting the data right is necessary but not sufficient.

## Revenue construction

1. **Project constant-currency, hold FX flat.** Anchoring revenue CAGR on
   *reported* growth bakes the current FX move into every forward year — a one-
   off translation headwind becomes an implicit forecast of perpetual currency
   depreciation. Grow the actual base year at the underlying constant-currency
   rate, FX held flat or modelled explicitly.

2. **Glide each segment year-by-year; let group CAGR be an output.** One flat
   rate per segment for years over-states the fast segments (hyper-growth
   decays) and ignores mix shift. Glide each segment, sum to group, read the
   top-level CAGR off the result. A glide runs from a Y1 growth input to a
   Y-end growth input, interpolated — not flat blocks with a terminal cliff.

3. **Match the explicit horizon to company type — the standard, not a longer
   window.** ~10 years for a growth company, ~5 for a stable one, set by the
   stage-1 classification. Do NOT extend to 15–20 years. The durability of a
   franchise that still out-grows GDP at the end of the window is captured in the
   *terminal*, not by lengthening the explicit forecast: if final-year growth is
   materially above the perpetual rate, use a two-stage / H-model terminal (fade
   from final-year growth down to the perpetual rate) instead of a single Gordon
   jump. And never steepen the in-window fade to force convergence to a low
   number — that manufactures understatement.

## Growth & fade discipline — applies to ALL scenarios, both directions

4. **No ungrounded numbers in either direction.** A low fade endpoint imposed
   without evidence of deterioration (competition, churn, saturation, lost
   logos) is as much an error as an ungrounded bear. Anchor late-stage growth to
   mature comparables: e.g. payment networks have sustained low-double-digit
   growth for many years — treat that as a *generous ceiling* for an adjacent-
   layer name, adjusting down for its different economics and more competitive
   position, not as a floor. A bear CAGR below industry TAM growth assumes
   persistent share loss and needs evidence.

5. **Y-end growth is not terminal growth.** The last explicit year can stay well
   above GDP (a durable compounder is still growing fast at year 10). The terminal
   *perpetual* rate must be ≤ long-run nominal GDP — arithmetic, not a judgment
   call. Bridge the gap with a two-stage / H-model terminal; never capitalise an
   above-trend final year straight into perpetuity (the "growth cliff").

## EV → equity bridge

6. **Net-cash sign, single t0 figure, strip settlement balances.** Confirm the
   bridge ADDS net cash / SUBTRACTS net debt with the right sign (a sign error is
   a ~2× swing and nothing looks broken). Net cash is one t0 number — same across
   all scenarios; flexing it manufactures spread out of the bridge. For an
   acquirer or regulated entity, strip merchant settlement balances and
   regulatory/restricted capital first; gross cash is not distributable cash.

## Terminal value & cost structure

7. **Terminal value sanity.** TV is usually the majority of value. Back out the
   implied terminal exit multiple (EV/NOPAT at the final year) and sanity-check
   it vs mature comparables; an implied 40x+ multiple is a hidden error. A
   healthy model keeps TV well under ~65% of EV — a longer explicit horizon
   lowers TV-reliance, which is the structurally sounder fix.

8. **SBC / dilution consistency.** If FCF adds back stock-based compensation,
   model share-count growth or treat SBC as a cash cost — not neither. (If SBC is
   already expensed inside the EBIT you use, no add-back/dilution adjustment is
   needed — confirm which.)

9. **Operating vs non-operating income.** Do not anchor growth on a headline
   profit/EPS line carrying a rate-sensitive or one-off non-operating component.
   Value the operating business; model financial/non-operating income separately.

## How to apply

Before trusting any DCF output, run all of the above. Treat only `hard` inputs
as Base movers; express soft-input uncertainty by widening the Bear–Bull spread.
Each of these moved a real verdict a full notch — more than any single sourced
figure did. Checks 3–5 are the newest and most commonly missed: keep the standard
horizon, ground the final-year growth, and let a two-stage terminal — not a longer
window or an over-steep in-window fade — carry a durable franchise's runway.