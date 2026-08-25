---
description: Write a DeepResearch prompt for QUALITATIVE color and document discovery (never the numbers)
---

Read `01-classification.md`.

**What DeepResearch is for.** Gemini is a search-first tool. It is genuinely good at
finding, reading and synthesising *published text*: who does what, why a mechanism
works, what management actually said, which entities exist, how a market is
structured, what the disputes are, and **where the primary documents live**. It is
reliably bad at *reproducing figures out of filings* — it has no access to them and
reconstructs from memory, so its numbers are plausible-shaped fabrications. Two rounds
of escalating sourcing rules on the Semiconductor survey proved this cannot be
prompted away: hardening only traded gap-filling for performative skepticism.

**So do not ask it for numbers.** The financial spine comes from `/verify-primary`
(filings via NotebookLM + SEC XBRL) into `04c-primary-financials.md`. This prompt asks
for two things only:

1. **Qualitative color** — moat mechanism, capital-allocation narrative, competitive
   dynamics, industry structure, regulation, the bear case.
2. **A document map** — the exact primary sources, with links, where each open
   quantitative question can be answered. This is the highest-value output: it makes
   the subsequent XBRL pull and NotebookLM upload targeted instead of speculative.

Write `02-dr-prompt.md`: a single, self-contained prompt the user pastes into Gemini
DeepResearch, tailored to the classification and lens from stage 1.

First, name the issuer's primary documents (IR page, latest annual report, latest
interim, shareholder letters, transcripts) and their dates, so Gemini has an anchor and
cannot default to a stale period.

The prompt MUST open with these rules:

1. **DO NOT STATE FINANCIAL FIGURES.** No financial tables, no computed ratios, no
   margins, no market sizes, no CAGRs. If a number is essential to a point, **quote the
   sentence containing it verbatim from the source and link the source** — mark it
   `QUOTED`, and it is understood to be a quotation, not data. We extract every figure
   ourselves from the filings.
2. **GIVE THE DOCUMENT, NOT THE NUMBER.** For each quantitative question raised, name
   the exact document (issuer, document type, period) and *where inside it* the answer
   lives — the statement, note, or segment disclosure. A precise pointer is worth far
   more to us than a figure.
3. **PREFER VERBATIM MANAGEMENT QUOTES** for any claim about pricing, capacity,
   demand, competition or strategy — from earnings-call transcripts, annual-report
   letters, or investor days, with the speaker, date and forum. Paraphrase loses the
   hedging, and the hedging is usually the information.
4. **SEPARATE SHIPPING IN VOLUME / QUALIFIED / SAMPLING / ANNOUNCED-ONLY** wherever a
   product, capacity or technology is discussed. A roadmap is not a shipment.
5. **SAY WHEN YOU DON'T KNOW.** "Not established" is a useful answer and will not be
   held against the report. Do not fill a gap with a plausible-sounding number or a
   content-farm claim. Do not manufacture uncertainty either — if something is well
   documented, say so plainly.
6. **FLAG DISAGREEMENT.** Where credible sources conflict on a *qualitative* point,
   present both and say who says which. Do not average or silently pick.
7. For structural and market-structure claims, prefer named industry bodies, standards
   orgs, regulators, patent offices, court filings, and trade press with a named author.
   Content farms, SEO "market research" pages and stock blogs are not usable even as
   colour — they are themselves LLM-generated in most cases.

Then tailor the BODY to the classification. Ask for:

- **Moat mechanism, told as a causal story.** Which of switching costs / network
  effects / intangibles / cost advantage / efficient scale, *how it actually operates
  in this business*, and what evidence would show it widening or narrowing. Specific
  episodes: customers won and lost, a price increase that stuck or didn't, a
  competitor that tried and failed to enter.
- **Capital allocation as narrative.** The 10-year record told as episodes — what was
  acquired and whether it delivered what was promised, when buybacks happened relative
  to the cycle, how debt was handled through a stress. No figures; the *judgement
  pattern* is what we want, and we will price it ourselves.
- **Competitive landscape — named entities and their posture.** Who competes on what,
  who is gaining, who is retreating, who is private and how funded. Where a competitor
  discloses the same operating primitive as the subject, **point to the document that
  discloses it** rather than stating the value.
- **Industry structure and regulation.** Where economics pool and why; the regulatory
  trajectory; any structural or technological shift that could re-route the subject's
  economics. Cite regulatory text and consultation documents directly where they exist.
- **The bear case**, and what bulls are assuming that the *documented evidence* does
  not yet support.
- **The document map (required closing section).** A table: open question | issuer |
  document and period | where in it the answer sits | link. Every quantitative question
  the report raised but did not answer goes here. This section is the deliverable that
  feeds `/verify-primary`.

Output the prompt in one fenced block. Keep it focused — breadth of mechanism, not
depth of data.

Outside the block, remind the user to paste Gemini's output into `03-gemini-report.md`
before running `/critique-report`.


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
