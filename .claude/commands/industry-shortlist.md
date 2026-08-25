---
description: Terminal artifact — ranked named candidates per investable layer, handed to the company funnel
---

Read `05-industry-map.md`, `06-operating-drivers.md`, `04-critique.md`, and
`01-classification.md`.

This is the TERMINAL stage of the industry track. An industry review does not end
in a verdict on one name — it ends in a **ranked shortlist of named candidates,
each routed into the company pipeline at stage 1 with its lens pre-chosen.** Do
not value anything here; sizing a business is the company funnel's job.

Write `07-shortlist.md`:

1. **Where to fish.** One short paragraph: which 1–2 layers the profit pool sits
   in and is investable (from `05`), and therefore where the candidates below are
   concentrated. State plainly any layer you are deliberately skipping (durable
   but private, or investable but commoditising).
2. **Shortlist table.** One row per candidate, ranked. Columns:
   - **Name / ticker** (public only — flag private names separately in §4).
   - **Layer(s)** it occupies.
   - **Archetype** (cash-cow + optionality / pure-play / component-chokepoint /
     platform-software — from `01`).
   - **Why it's on the list** — its claimed edge in the profit-pool/chokepoint
     layer, one line, with the reliability tag of the evidence.
   - **Entry lens for the funnel** — the valuation lens it will take at `/classify`
     (e.g. SOTP: legacy business + robotics option; Compounder; Early-stage).
   - **Route & floor quality** (from `05` step 3) — Route A (pure-play/high-beta)
     or Route B (quality survivor + embedded option), with floor quality
     STRONG/MEDIUM/WEAK. For a *development-stage* theme, do NOT pass a name just
     because the bet is small, nor reject it for the same reason — judge the FLOOR.
     A Route-B name on a WEAK floor (low-margin, structurally-declining legacy with
     a press-release option) is a value trap and should be flagged, not ranked high,
     however exciting the option. A LOW-dependence bet on a STRONG floor is the
     asymmetric setup and should rank high.
3. **Per-candidate one-liner: what to verify first.** For each shortlisted name,
   the single load-bearing thing the company-funnel research must confirm or kill
   (e.g. "is the legacy industrial margin actually defensible — the SOTP floor",
   or "is the data moat proprietary or licensable by anyone").
4. **Watch list (not yet investable).** Durable-pool names that are private,
   pre-revenue, or where exposure is too small today — with the trigger that would
   promote them (IPO, a segment crossing materiality, a named contract).
5. **Hand-off to the company funnel.** State explicitly, per shortlisted name:
   copy `companies/_TEMPLATE` to `companies/<TICKER>/`, seed `00-brief.md` with the
   thesis + entry lens from this file, and run `/classify`. The cash-cow +
   optionality names go in first — they carry a valuation floor (SOTP) and so fail
   safer, exactly as the brief intends.
6. **Open questions.**

Rank by a combination of profit-pool durability, investability, and — for a
development-stage theme — **floor quality + how cheap the embedded option is**,
not by how exciting the technology is. The exciting name is often the
commoditising one; the best risk-adjusted entry is often a quality survivor
carrying the theme as a cheap call, where you win if it scales and survive if it
doesn't.

## Price discipline (binding — added 2026-08-18)

Per CLAUDE.md prime directive #4, this stage ranks on **business quality and evidence**, never
on price. Do NOT rank, tier, order, or exclude any candidate using a current multiple, a
percentile of its own historical range, or its distance from an all-time high. Those are
statements about the past price series, not the business, and they systematically discard the
best compounders — a winner sits near its own historical highs *because* it is winning.

Rank on: moat mechanism and its direction · margin level and stability · recurring/annuity
share · revenue and operating-margin drawdown through real downturns · realised pricing
achieved · **materialised orders** (booked units, backlog, capacity commitments, installed
base) · reinvestment runway · floor quality for Route B names.

Each shortlisted name then ENTERS the company funnel at `/classify`, where its own valuation is
built from its drivers. **Price is compared to that valuation only at `/verdict`**, as the upside
check and the margin of safety. **Do not record price data in any stage artifact — not even quarantined.**
`/verdict` retrieves it fresh at the decision.
