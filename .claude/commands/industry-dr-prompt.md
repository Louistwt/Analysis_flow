---
description: Write a DeepResearch prompt for an INDUSTRY survey — qualitative structure + document discovery (never the numbers)
---

Read `01-classification.md`.

**What DeepResearch is for.** Gemini is a search-first tool. It is genuinely good at
finding and synthesising *published text* — how an industry is structured, which
entities exist and what they do, why a mechanism works, what management said, where the
disputes are, and **where the primary documents live**. It is reliably bad at
reproducing figures out of filings, which it has no access to and reconstructs from
memory. Do not try to prompt this away: escalating sourcing rules only trade gap-filling
for performative skepticism (see the Semiconductor run, `04-critique-v1-report.md`).

**So do not ask it for numbers.** Figures are extracted afterwards — from SEC XBRL for
any US or 20-F filer, from NotebookLM for the rest — under the routed worklist that
`/critique-report` produces. This prompt asks for the industry's *shape* and for the
*document map* that makes that extraction targeted.

Write `02-dr-prompt.md`: a single, self-contained prompt the user pastes into Gemini
DeepResearch. Unlike the company-track prompt, this surveys an INDUSTRY — it fans out
across layers and players rather than drilling one issuer. It does NOT ask for WACC, net
cash, share counts, or a DCF. The goal is a layer map, the mechanism of value capture
per layer, a named-player roster, and a document map — feeding `/industry-layermap` and
`/industry-shortlist`.

The prompt you produce MUST open with these rules:

1. **DO NOT STATE FINANCIAL FIGURES.** No margins, market sizes, CAGRs, shares,
   capacities or drawdowns as data. If a number is essential to a point, **quote the
   sentence verbatim from its source and link it**, marked `QUOTED` — understood as a
   quotation, not a datapoint. Every figure we use is extracted from filings ourselves.
2. **GIVE THE DOCUMENT, NOT THE NUMBER.** For each quantitative question, name the exact
   document (issuer, type, period) and where inside it the answer sits — statement, note,
   or segment disclosure. A precise pointer beats a figure.
3. **PREFER VERBATIM MANAGEMENT QUOTES** for claims about pricing, capacity, demand,
   qualification or competition — with speaker, date and forum. The hedging in a
   transcript is usually the information.
4. **SEPARATE SHIPPING IN VOLUME / QUALIFIED / SAMPLING / ANNOUNCED-ONLY** everywhere.
   A roadmap, a demo and a "development complete" release are none of them shipments.
   This distinction is qualitative and is exactly what Gemini is good at.
5. **SAY WHEN YOU DON'T KNOW.** "Not established" is a useful answer. Do not fill a gap
   with a plausible number, and do not manufacture uncertainty about well-documented
   things either.
6. **FLAG DISAGREEMENT** on qualitative points — present both sides and say who says
   which. Do not average, do not silently pick.
7. For structure claims prefer named industry bodies, standards orgs, regulators, patent
   offices, court filings, conference papers, and trade press with a named author.
   Content farms and SEO "market research" pages are not usable even as colour.

Then tailor the body to the layers and value-capture question from stage 1.
Require, with the rules above:

- **Layer taxonomy.** Confirm or revise the provisional layers from stage 1, flagging any
  change explicitly — never drop a layer silently. Per layer: what it does, representative
  players (public AND private), **the pricing basis** (what unit the layer is actually paid
  per), and who holds pricing power. Describe the margin *structure* as a mechanism — why
  it is high or low, what protects or erodes it — without stating margin figures.
- **Where economics pool, and why they resist commoditising.** For each candidate layer,
  the specific resistance mechanism, tested rather than asserted: qualification lock-in
  (how long, and has anyone ever been displaced from a qualified position — name the
  episode), a scarce physical input, an IP thicket, switching costs in tooling or design
  databases, installed-base scale. Call out where the excitement and the money diverge.
- **Supply-chain chokepoints, with the substitution question.** For each claimed
  chokepoint: what exactly is scarce, who else could do it, at what cost, with what
  qualification lead time, and what would have to change for a substitute to be adopted.
  A chokepoint whose buyer can design it out, or fund a rival's capacity, is not one —
  test that explicitly.
- **Patent / IP ownership per layer.** Who holds the load-bearing patents in the domains
  stage 1 named; concentration vs fragmentation; identifiable expiries; live litigation
  **with docket and court**. A settlement or licence deal is not an enforcement win —
  label them differently.
- **The road-not-taken register.** Technologies that are technically credible but not the
  consensus path: the promise, the specific blocker (cost, yield, ecosystem, standards,
  qualification, capital), the realistic timeline, and **who would capture the economics**
  if it happened. Sort into ADOPTED / CREDIBLE-BUT-BLOCKED / HYPE. This is where a
  search-first tool genuinely outperforms us and should be given real space.
- **Existing real deployments.** Named, in-production implementations — with rule 4's
  distinction held rigorously, since separating a shipping product from a press release is
  the single most useful thing this stage produces.
- **Named-player roster, per layer.** Public/private, ticker AND listing venue, which
  layer(s) each occupies, and whether it is a **cash-cow + optionality** name (an existing
  profitable business funding the theme's bet, suitable for a SOTP floor) vs a pure-play.
  **No revenue, no margins, no multiples** — instead, for each name, point to the document
  and segment note where its legacy business can be sized. Flag names not listed in the
  investor's reachable venues (see [[gettex-eur-access]]) — access is a qualitative fact
  Gemini can establish and it decides whether a name is usable at all.
- **Strongest bear case for the whole theme**, and what bulls are assuming that the
  documented evidence does not yet support. Name the leading indicator for each bear
  vector — the observable series that would show it happening first, and where it is
  published.
- **The document map (required closing section).** A table: open question | issuer or body
  | document and period | where in it the answer sits | link. Every quantitative question
  the survey raised but did not answer belongs here. This section is what makes the
  subsequent XBRL pull and NotebookLM upload targeted, and it is the highest-value output
  of the stage.

Output the prompt in one fenced block for easy copy. Keep it focused — breadth across
layers, depth only on the profit-pool and chokepoint layers and the road-not-taken
register; a prompt that asks for everything at full depth gets shallow answers on
everything.

Outside the block, remind the user to paste Gemini's output into `03-gemini-report.md`
before running `/critique-report`, which triages it into a routed research worklist rather
than auditing its figures.


---

## Market sizing — added 2026-08-18

Where a market size or growth rate is needed, **do not ask for a number.** Ask for **what several
NAMED participants each say**, quoted, and where they agree:

- earnings-call, conference, investor-day and interview transcripts from **multiple companies
  across the value chain**, plus named industry bodies;
- the *commonalities* across those statements — the consensus is the overlap, not any one figure;
- each participant's own **assumed share of that market**, so the sum can be checked against 100%
  (methodology #29);
- **backlog, bookings and management's stated recognition timing**, which convert a market claim
  into a dated cash-flow claim.

A market size derived from the overlap of several participants' own statements is worth far more
than one figure with a stated method, and it is the kind of synthesis a search-first tool is
genuinely good at.
