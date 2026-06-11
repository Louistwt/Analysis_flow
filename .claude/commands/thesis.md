---
description: Distil a completed run into a living THESIS.md for ongoing monitoring
---

Run ONCE after `/verdict`. Read `07-assumptions.md`, `09-verdict.md`, and
`06b-growth-decomposition.md`. Distil them into `THESIS.md` at the company root —
the durable, living file you update each earnings report (NOT a numbered run
artifact; it outlives any single run). Compress; this is the at-a-glance thesis,
not a copy of the run.

Write `THESIS.md` with exactly this structure:

```
# THESIS — <TICKER>   (living file — updated each ER, not per run)

Last reviewed: <today> | Status: INTACT | Action: <verdict's action>

## Thesis in one paragraph
<why this compounds; the core bet>

## Quality / moat
<moat type; widening / stable / narrowing; the ONE thing that would change it>

## Swing inputs — assumed paths (check every ER)
| Driver | Thesis assumes | Latest actual | As of | On track? |
|--------|----------------|---------------|-------|-----------|
| Volume (e.g. TPV) growth | <from 06b/assumptions> | — | — | — |
| Take rate / price | <flat/declining/rising + why> | — | — | — |
| EBIT margin | <gliding to X> | — | — | — |
| <other key driver> | | — | — | — |

## Falsifiers (review / sell triggers)
1. <falsifier from verdict> — status: not yet
2. ...
3. ...

## Things to follow up on (watch list — you and /earnings-update both add here)
- [ ] <item> — why it matters; when it should resolve
- [ ] <e.g. competitor volume gap; a disclosure gap; an integration milestone>

## Earnings log (append-only)
(empty until first /earnings-update)
```

Seed the swing-input table from the four swing inputs + the volume × price
decomposition in 06b; the falsifiers from the verdict's three review triggers;
the watch list from the verdict's "what still needs verifying" + open questions.