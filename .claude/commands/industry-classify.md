---
description: Frame an industry review — player archetypes, layers, and the value-capture question
---

Read `00-brief.md`. This is the INDUSTRY-track entry point (a divergent survey),
not the company funnel. The goal is not a verdict on one name — it is to find
**where durable economics pool and which named companies are then worth running
through the company pipeline**. Do not converge on a single subject.

Write `01-classification.md`:

1. **Scope & boundary.** State what is in and out of the industry as defined by
   the brief (e.g. for "physical AI": robot hardware, actuation/sensing, the
   software/foundation-model layer, simulation/synthetic-data, the data layer,
   integration/deployment). One sentence each on what's excluded and why.
2. **Provisional layer map (the "cake").** List the candidate layers end to end.
   For each: what it does, and a first guess at its margin structure and who
   holds pricing power. This is provisional — `/industry-layermap` confirms it
   against the report; here it just scopes the research.
3. **Player archetypes.** Classify the *kinds* of company competing, because each
   needs a different valuation lens later when it enters the company funnel:
   - **Cash-cow + optionality** — an existing profitable business funding
     robotics/AI R&D (e.g. an industrial/components incumbent). → SOTP candidate:
     value the legacy business first, treat the new bet as a real option.
     The brief flags these as the safer entry — capture them as a first-class
     archetype.
   - **Pure-play / early-stage** — value rests almost entirely on the new bet.
   - **Component / chokepoint supplier** — sells into the whole industry
     regardless of which application wins (the "picks and shovels" layer).
   - **Platform / software / simulation** — licensing or usage economics, network
     and data effects.
   Name the lens each archetype will take in the company funnel (Compounder,
   Resource, Infrastructure, Early-stage, etc. — see CLAUDE.md).
4. **The value-capture question.** State the central question this review must
   answer (CLAUDE.md value-capture discipline): which layer captures durable
   economics, is it the exciting layer or a boring one, and is that layer
   investable in public markets? Name the most likely commoditising layer and
   the most likely chokepoint up front as a hypothesis to test.
5. **Primary operating drivers, per layer.** The unit economics that will gate
   each layer's growth (units × ASP × attach, or seats/usage × ARPU, or
   simulation compute-hours × price, etc.). These tell `/industry-dr-prompt` what
   time series to demand.
6. **What the DeepResearch prompt must prioritise** — the layer taxonomy,
   patent/IP ownership per layer, supply-chain chokepoints, the simulation/data
   moat, existing real deployments, and a named-player roster per layer (public
   vs private, ticker where public).
7. **Open questions.**

If `00-brief.md` is too thin to scope the industry, say what's missing and stop.
