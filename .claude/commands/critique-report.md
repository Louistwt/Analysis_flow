---
description: Triage the DeepResearch report into a routed research worklist (not a number audit)
---

**This stage is a TRIAGE, not an audit.** The DeepResearch report is a junior
researcher's orientation memo: useful for structure, mechanism and named entities;
worthless as a source of figures, because the model cannot read the filings and
reconstructs numbers from memory. Auditing its figures claim-by-claim costs more effort
than extracting them fresh and produces nothing usable either way. Do not do it.

Your job is to convert the report into **(a) the mechanism claims worth testing** and
**(b) a routed worklist that says who answers each open question.**

Delegate to the **`skeptic` subagent** so it runs in a clean context with no exposure to
bull-case reasoning. Pass it `03-gemini-report.md`, `01-classification.md`, the brief,
and `04c-primary-financials.md` **if it exists** (it does in the company track, where the
spine is extracted first; it does not in the industry track, where this stage runs
earlier — say which situation applies).

Instruct the skeptic to write `04-critique.md` with these sections:

1. **What is worth keeping.** The mechanism claims, structural insights and named
   entities that survive as *hypotheses*. For each: what would confirm or kill it, and
   which disclosed data would do that. This is the section that matters — a good
   mechanism claim with a named test is the whole value of the DR stage.
2. **What to discard without correcting.** Figures, computed ratios, market sizes and
   drawdowns are not used. List them briefly so nobody downstream mistakes them for
   data, and move on. **Do not audit them, do not re-source them, do not tabulate their
   provenance.** One line each is enough.
3. **Internal incoherence.** Where the report's *narrative* contradicts itself — a
   verdict its own evidence reverses, two sections answering the same question opposite
   ways, a mechanism claimed in one place and denied in another. This is a genuine check
   and stays: an incoherent story signals the model had no underlying model of the
   business, which devalues the qualitative content too.
4. **Promotional echo and framing bias.** Where the report has laundered an industry's
   own marketing frame ("total pricing power", "absolute immunity", "the cycle is
   broken") instead of describing a mechanism. Check confirmation bias in both
   directions — whether it merely confirmed stage 1's hypotheses rather than testing
   them, AND whether it over-corrected into unsupported bearishness. An unsupported
   bearish call costs as much as an unsupported bullish one.
5. **Omissions that matter qualitatively.** Competitor response, customer concentration
   as a *structural* exposure, regulatory trajectory, accounting flags worth watching,
   refinancing and dilution risk — things a skeptic expects to see discussed at all.
6. **★ The routed worklist** (the terminal deliverable — append to `_open-questions.md`).
   Every open quantitative question, split by **who answers it**:
   - **[T1] Pull from SEC XBRL / EDGAR** — revenue, gross profit, operating income,
     segment lines, customer concentration, per fiscal year back to ~2009, for any US or
     20-F filer. Free and exact; this is usually most of the map and should be listed
     first and exhaustively. See [[sec-xbrl-primary-extraction]].
   - **[T2] NotebookLM** — only names not on EDGAR (Japanese, Korean, HK, Taiwan,
     European local listings). Give a *minimal ranked document shopping list*, 2–4
     documents per name, with the specific question to ask each. See
     [[notebooklm-curated-primary]].
   - **[T3] Manual, indirect, or judgement** — what no single filing contains. Prefer
     an **indirect verification chain** over a paid data series: a disclosed number at
     one layer often pins an undisclosed one elsewhere (inventory and purchase
     commitments at a chain anchor read through to supplier revenue; consumable revenue
     reveals real production where tool revenue only reveals intended capacity;
     monthly-reporting jurisdictions give near-real-time chain visibility). State the
     anchor, the inference, and the falsification signal. Explicitly name what is **not
     worth buying** because a derived proxy substitutes.

The skeptic must not soften findings, and must not pad. A short, sharply routed worklist
beats a long ledger. If the report is qualitatively useless, say so in one line and go
straight to the worklist — the worklist is valuable even when the report is not.
