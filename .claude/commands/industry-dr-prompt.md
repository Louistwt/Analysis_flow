---
description: Write a source-disciplined DeepResearch prompt for an INDUSTRY survey
---

Read `01-classification.md`.

Write `02-dr-prompt.md`: a single, self-contained prompt the user pastes into
Gemini DeepResearch. Unlike the company-track prompt, this surveys an INDUSTRY —
it must fan out across layers and players, not drill one issuer. It does NOT ask
for WACC, net cash, share counts, or a DCF; the goal is a layer map, profit-pool
evidence, and a named-player roster that feeds `/industry-shortlist`.

The prompt you produce MUST open with these non-negotiable rules:

1. A claim is UNSUPPORTED by default; it is HARD only with a citation to a primary
   or authoritative source + date. For a financial figure on a named player, the
   source is that company's own filing/report + period + page/note. For market
   structure, cite a named industry body, standards org, patent office, or an
   analyst report whose METHOD is shown — never an aggregator's bare number. No
   citation = write "NOT FOUND." Never substitute a content-farm value.
2. BAN as a cited source for any figure: stockanalysis.com, macrotrends,
   simplywall.st, koyfin, investing.com, marketing blogs, vendor/teaser decks,
   Wikipedia. They may locate a primary source, never source a number.
3. USE THE LATEST AVAILABLE PERIOD for every player figure.
4. TAM DISCIPLINE: any market-size or CAGR number must show its method (top-down
   vs bottom-up) and base year. A TAM with no method stated is tagged `soft` at
   best. Prefer a bottom-up build (installed base × price × attach) where possible.
5. Tag every claim `hard` / `soft` / `unsupported`. Flag any internal
   CONTRADICTION and leave it unresolved.

Then tailor the body to the layers and value-capture question from stage 1.
Require, with the rules above:

- **Layer taxonomy.** Confirm or revise the provisional layers from stage 1.
  Per layer: what it does, representative players (public + private), the margin
  structure (gross/operating where disclosed), and who sets price.
- **Where economics pool.** Evidence on which layer captures durable margin and
  WHY it resists commoditising (switching costs, IP, a scarce input, qualification
  cycles). Call out where the excitement and the money diverge.
- **Patent / IP ownership per layer.** Who holds the load-bearing patents
  (actuation, sensing, manipulation, foundation models, sim)? Concentration vs
  fragmentation; expiries; litigation.
- **Supply-chain chokepoints.** Scarce or single-sourced inputs (precision
  reducers/actuators, specific sensors, compute) and who controls them.
- **Simulation / synthetic-data and the data moat.** Who owns the leading
  simulation environments and the training-data pipelines; how defensible is a
  proprietary real-world data corpus, and can a domain incumbent generate
  training data a generalist cannot.
- **Existing real deployments.** Named, in-production implementations (logistics,
  manufacturing, construction, surgical, etc.) with scale where disclosed —
  separate shipping revenue from pilots and from announcements.
- **Named-player roster, per layer.** For each material player: public/private,
  ticker if public, which layer(s) it sits in, and — critically — whether it is a
  **cash-cow + optionality** name (an existing profitable business funding the
  robotics/AI bet, suitable for a SOTP) vs a pure-play. Where public, give the
  most recent revenue and operating margin (sourced) so the legacy business can be
  sized later — but no valuation, no DCF.
- **Strongest bear case for the whole theme** and what bulls are likely pricing
  that the evidence does not yet support.

Output the prompt in one fenced block for easy copy. Keep it focused — breadth
across layers, depth only on the profit-pool and chokepoint layers; a prompt that
asks for everything at full depth gets shallow answers on everything.

Outside the block, remind the user to paste Gemini's output into
`03-gemini-report.md` before running `/critique-report`.
