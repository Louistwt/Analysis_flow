---
description: Check a new earnings report against the thesis — without re-running the pipeline
---

Read `THESIS.md`. The user has pasted the new report's key figures into
`_er-input.md` (or given them in chat), plus any follow-up items they want added
to the watch list. This loop reads the living thesis only — it does NOT re-run
stages 1–9.

Delegate the assessment to the **`skeptic` subagent**. Its job here is specific:
stop the user explaining away bad news to avoid selling, and stop them panicking
on a single noisy quarter. Clean context, no bull framing.

The skeptic appends a dated entry to the earnings log and updates the live
sections of THESIS.md:

1. **Reconcile the actuals.** Reliability-tag and recompute derived figures;
   prefer the issuer's own release (NotebookLM the report if a clean pull is
   needed). A figure that doesn't tie out is not usable. **Adjust interim figures
   for seasonality and one-offs before comparing to a full-year assumption:** an
   H2-weighted company's H1 margin is structurally lower (Adyen H1'26 EBIT 43.3% vs
   FY ~47% — not a miss); a blended rate can be flattered/depressed by a large
   customer entering or exiting. Compare like-for-like (EBIT to EBIT, not to the
   EBITDA headline — #27).
2. **Compare each swing input vs the thesis** and update the table (latest actual
   + as-of + on-track?). Decompose the revenue move into volume × price as in
   06-operating-drivers — a beat driven by price/take rate is more fragile than one
   driven by volume.
3. **Check each falsifier:** not-yet / WATCH (one data point toward it) / TRIPPED.
4. **Trend vs noise.** One miss is not a broken thesis; a direction sustained
   across 2–3 periods is. State which this is — resist both rationalising and panic.
5. **Watch list:** mark items resolved, raise new ones the ER surfaced, and fold
   in any the user added.
6. **Verdict delta + action**, mapped to the sell discipline in CLAUDE.md:
   - Falsifier TRIPPED, or a swing driver structurally deteriorating → WEAKENING /
     BROKEN → TRIM / SELL.
   - Swing inputs on track or improving → INTACT → HOLD / ADD.
   - Price moved but thesis unchanged → no thesis action. If price fell materially
     while the thesis is intact, flag the improved margin of safety (ADD candidate).
     Never sell on price alone.
7. **Re-model?** Only if a falsifier tripped or a swing input materially deviated —
   then say "re-run /assumptions + update the Sheet for inputs X, Y," not the whole
   pipeline. Otherwise the tracker update IS the whole job. **The trigger is
   SYMMETRIC:** a swing input that materially BEATS (delivered growth above the Base,
   a raised guide) updates the Base *up*, exactly as a miss updates it down — the
   Base is the expected case, so it tracks reality both ways (Prime Directive 1).
   Anchoring to a stale conservative Base while performance beats is the disposition
   error inverted. Hold like-for-like: a *growth* beat raises growth on evidence, not
   a licence to bump EBIT toward the EBITDA headline (#27).

Finally, update the THESIS.md header (last reviewed, status, action). Keep the
earnings log append-only — the point is a time series of thesis-vs-reality.