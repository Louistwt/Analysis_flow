# Equity Research Pipeline (Claude Code)

A staged, human-gated research workflow that turns an industry or company idea into a defensible
set of **bear / base / bull** DCF assumptions, and then into a priced verdict. Each stage is a
Claude Code slash command you run **one at a time**, reviewing the output file before firing the
next. The model does not run ahead.

Two tracks share one brain (`CLAUDE.md`):

- **Company funnel** — converges on one priced verdict for a named issuer.
- **Industry sub-track** — a divergent survey that fans out across layers and ends in a ranked
  shortlist, each name then entering the company funnel at stage 1.

---

## How it works

1. Open a terminal at the repo root and run `claude`.
2. Copy `companies/_TEMPLATE/` to `companies/<TICKER>/` (or create `Industry/<Sector>/` for a
   survey).
3. Fill in `00-brief.md` — what you want to look at and why. Say what you already believe and
   what you want argued with; stage 1 will test your own claims rather than adopt them.
4. Run the stages in order, reviewing each output file before the next.

### Company funnel — **sourcing is primary-first**

The issuer's verified financial spine is extracted from the filings **before** DeepResearch runs.
Leading with an aggregator narrative anchors the model on consensus it then has to un-anchor from.
DeepResearch supplies qualitative and competitive *colour*, cross-checked against the spine —
never the reverse.

| Run | Command | Reads | Writes |
|---|---------|-------|--------|
| 1 | `/classify` | 00-brief.md | 01-classification.md |
| 2 | `/verify-primary` | 01, 04b-notebooklm-raw.md | **04c-primary-financials.md** |
| 3 | `/deepresearch-prompt` | 01, 04c | 02-dr-prompt.md |
| 4 | *(run the prompt in Gemini DeepResearch, paste output)* | — | 03-gemini-report.md |
| 5 | `/critique-report` | 03, 04c | 04-critique.md |
| 6 | `/industry-map` | 03, 04, 04c | 05-industry-map.md |
| 7 | `/operating-drivers` | 05, 04c | 06-operating-drivers.md |
| 8 | `/assumptions` | 04, 05, 06, 04c | 07-assumptions.md |
| 9 | `/redteam` | 07 (+ all) | 08-redteam.md |
| 10 | `/verdict` | all | 09-verdict.md |

> **The numeric filename prefix is a legacy artifact and does not match run order.** `04c` is
> produced at run-step 2. The table is in run order; the filenames are historical. Don't reorder
> the files to "fix" this — downstream commands reference them by name.

**Stage 2 for a non-SEC issuer.** `/verify-primary` pulls US filers straight from SEC XBRL
(`data.sec.gov`). Foreign issuers — BESI, ASML, TSMC, Disco, Advantest, Tokyo Electron, the whole
Japanese and Korean half of a supply chain — have **no XBRL and no fallback**. There, everything
routes through NotebookLM: the command first writes a `04b-notebooklm-request.md` question set,
you upload the issuer's own reports and paste the raw answers into `04b-notebooklm-raw.md`, and
only then does the spine get built. Paste it **raw and unedited** — the reconciliation pass
recomputes every derived ratio from its own inputs, and tidying on the way in destroys the
evidence that catches a mangled citation.

### Industry sub-track (survey, not valuation)

Use when `00-brief.md` asks to decompose an industry or find investable layers rather than to
value one company. Its terminal output is **not** a verdict — it is a routing artifact.

| Run | Command | Reads | Writes |
|---|---------|-------|--------|
| 1 | `/industry-classify` | 00-brief.md | 01-classification.md |
| 2 | `/industry-dr-prompt` | 01 | 02-dr-prompt.md |
| 3 | *(run the prompt in Gemini DeepResearch, paste output)* | — | 03-gemini-report.md |
| 4 | `/critique-report` | 03 | 04-critique.md |
| 5 | `/industry-layermap` | 03, 04 | 05-industry-map.md |
| 6 | `/operating-drivers` | 05 | 06-operating-drivers.md |
| 7 | `/industry-shortlist` | 05, 06, 04, 01 | 07-shortlist.md |

Each shortlisted name is copied into `companies/<TICKER>/`, seeded with its entry lens, and run
through `/classify` onward. **Cash-cow + optionality names go first** — an existing profitable
business funding the AI/robotics bet carries an SOTP valuation floor, so it fails safer.

---

## The single living register

Every stage appends to **`_open-questions.md`** at the run root; `/verdict` draws it down. There
are no per-stage open-questions lists. Items are routed:

- **[T1]** SEC XBRL / EDGAR — exact, free, and not reconstructable from memory
- **[T2]** NotebookLM — documents you upload yourself
- **[T3]** manual, indirect, or judgement

For a non-SEC issuer, everything that would have been [T1] becomes [T2]. That single fact
reshapes the whole run and is worth stating in `01-classification.md`.

---

## Where the isolated subagent runs

Four commands delegate to the **`skeptic`** subagent, which runs in a clean context with no
exposure to the bull-case reasoning:

| Command | What the isolation is for |
|---|---|
| `/verify-primary` | Turning raw, possibly-mangled RAG extraction into trustworthy inputs — not trusting it |
| `/critique-report` | Triaging the DeepResearch report without having read the thesis that motivated it |
| `/redteam` | **Two-sided** assumption review — an unsupported conservative input is as much a flaw as an unsupported aggressive one |
| `/earnings-update` | Fighting the disposition effect: explaining away bad news to avoid selling, or panicking on one noisy quarter |

The isolation is the whole point — not speed. Note that `/redteam` is an *assumption review*, not
a demolition; it hunts errors in reasoning in **both directions**.

---

## Monitoring after a run (the maintenance loop)

A verdict is a snapshot. A multi-year hold is *maintained*, not decided once.

| Command | When | Reads | Writes |
|---------|------|-------|--------|
| `/thesis` | once, after `/verdict` | 07, 09, 06 | THESIS.md (living) |
| `/earnings-update` | each ER, guidance change, M&A, or management change — **never on a price move** | THESIS.md, `_er-input.md` | THESIS.md (appends a dated log) |

`THESIS.md` holds the swing inputs and their assumed paths, the falsifiers, the moat call, and a
watch list. `/earnings-update` marks each falsifier (not-yet / WATCH / TRIPPED), distinguishes a
trend from a noisy quarter, and returns a HOLD / ADD / TRIM / SELL delta — re-running the model
only when a falsifier trips or a swing input materially deviates. **A price fall on an intact
thesis is an ADD candidate, not a sell.**

---

## The model artifact

`/assumptions` outputs the markdown assumptions contract **and**, where the run is proceeding to a
decision, builds the live spreadsheet with adjustable inputs and the discount-rate sensitivity
grid. **Markdown is the contract; the sheet is the model.**

Two rules from hard experience:

- **A superseded model must not stay runnable.** Delete it, or make it print its own obsolescence.
  A script that confidently reports last week's answer is how a wrong number outlives its
  correction.
- **Generated artefacts must come from ONE source.** A sheet and the script that styles it drift
  apart silently otherwise. See `companies/AVGO/model/` for the pattern that works: Python
  modules generate the CSV and the Apps Script from shared definitions.

---

## Core principles baked into every stage (see `CLAUDE.md` for the full text)

1. **The Base case is the EXPECTED path — not a conservative one.** Risk is managed through the
   *width and reasoning* of the Bear–Bull spread, not a precise number. **Conservatism is applied
   ONCE** — in the Bear and in the margin of safety demanded at the decision — never baked into
   the Base as well. Baking caution into the Base, red-teaming it downward, *then* demanding a
   discount below it triple-counts caution and makes every quality compounder look fairly valued.
2. **Provenance with every number.** No orphan figures.
3. **Reliability tagging.** Only `hard` inputs move the Base. `soft` and `unsupported` widen the
   spread instead.
4. **Quality before price — and price enters LAST.** A low valuation on a narrowing moat is a
   pass, not a bargain; **the inverse is equally binding** — a high price on a durable compounder
   is not a reason to rank it down. See the price discipline below.
5. **Distinguish maintenance from growth capex — and run BOTH DCFs.** The gap between the two
   valuations *is* the growth investment, made visible rather than asserted.
6. **State uncertainty plainly.** Never fabricate or interpolate to fill a section.
7. **Decompose growth into unit economics before setting a CAGR.** A CAGR not reconciled to
   volume × price × penetration is an assertion, not an estimate.

### ★ The price discipline (strengthened Aug 2026)

`quality gate → operating drivers → assumptions → our own valuation → THEN price`

**Price is not written into any artifact before `/verdict` — not even quarantined.** A number
sitting in the file is an anchor whether or not it carries a warning label, and this framework's
own premise is that framing dominates the output. No pre-`/verdict` stage records a price, cites
one, or computes a multiple — including on a normalised or peak-year denominator. `/verdict`
retrieves the price fresh at decision time.

**Never used as a screen, a ranking input, or a reason to drop a name:** current multiple vs its
own history, percentile-of-own-range, distance from an all-time high. These describe a past price
series, not a business — and a compounder whose earnings power has structurally improved sits near
the top of its own range *precisely because it is winning*.

Price re-enters exactly twice, both at the end: the **upside check** against our own DCF, and the
**margin of safety** demanded at the decision.

**Not a price measure — stays in scope throughout:** historical drawdown of *revenue and operating
margin* is business performance. But its job is narrow: base-year normalisation (is this year a
trough?) and grounding the Bear in a downcycle the business actually lived through. It is not a
ranking input and not a prediction.

### ★ Margin is not moat

Margin measures rent **extracted**, not moat **width**. A monopolist may deliberately under-price
to keep customers healthy and avoid funding an entrant — understating itself on every margin
screen while making its position more durable. **Extracted rent attracts entry; unexercised rent
deters it.** Test instead for *latent* pricing power: rationing rather than price-clearing, customer
prepayments, value-per-unit-of-price rising, high and rising R&D intensity, and position on the
customer's critical path. The question to answer is: **what happens to the customer if this
supplier raises price 20%?**

---

## The methodology gate

`.claude/framework/methodology-checks.md` is the authoritative list — **34 checks**, run as a gate
by `/verdict` before any grade. These framing checks outrank any single data point: a mis-framed
model with clean data still gives the wrong verdict.

They cover constant-currency revenue, segment glide with group CAGR as an *output*, horizon by
company type, grounded fade endpoints in both directions, net-cash sign, terminal-value sanity,
SBC and dilution consistency, margins-as-outputs, SOTP surviving to valuation, EM country-risk
weighting, driver-narrative scenarios, **cash-flow ↔ discount-rate consistency** (FCFF→WACC /
FCFE→CoE / residual income / APV), the cost-of-capital contract, NOPAT not EBIT, reinvestment ↔
ROIC ↔ growth ties, a normalised base year, fading returns toward WACC, reverse-DCF and
relative-value triangulation, EBIT vs EBITDA never mixed, serial-acquirer M&A as reinvestment,
**competitive shares summing to ≤100%**, **TAM reconciled against units × ASP on the terminal
year**, one stated ROIC definition, the twin DCF, and a swept per-engine discount rate.

Two companion documents:

- **`.claude/framework/capex-supercycle-hybrids.md`** — the archetype playbook for build-ahead
  names (hyperscaler cloud, AI compute): glide capex *and* D&A, ~15yr horizon, owner earnings,
  APV over constant-weight WACC where the build deleverages. `/classify` flags the archetype.
- **`.claude/framework/improvement-backlog.md`** — pending and applied framework changes, with
  what landed where.

`MODEL-REFINEMENTS.md` at the root holds the cross-company lessons distilled from the GOOGL →
MSFT → NVDA runs.

---

## Files

```
CLAUDE.md                          # shared brain: framework, conventions, the assumptions contract
MODEL-REFINEMENTS.md               # cross-company model lessons (GOOGL → MSFT → NVDA)
README.md                          # this file

.claude/commands/*.md              # 15 pipeline stages (your /commands)
.claude/agents/skeptic.md          # isolated adversarial subagent
.claude/framework/
    methodology-checks.md          # the 34-check gate, run by /verdict
    capex-supercycle-hybrids.md    # build-ahead archetype playbook
    improvement-backlog.md         # framework change log

companies/_TEMPLATE/               # copy this per company
companies/<TICKER>/                # one company funnel run
    00-brief.md · 01-classification.md · 04b-notebooklm-*.md · 04c-primary-financials.md
    02-dr-prompt.md · 03-gemini-report.md · 04-critique.md · 05-industry-map.md
    06-operating-drivers.md · 07-assumptions.md · 08-redteam.md · 09-verdict.md
    _open-questions.md             # the living register
    THESIS.md                      # created by /thesis, outlives the run
    model/                         # the live spreadsheet and its generators

Industry/<Sector>/                 # one industry survey run (shared assets live here)
```

**Shared assets stay in `Industry/`, not in a company folder.** `Industry/Semiconductor/06-ai-demand-model.md`
is used by several deep dives; duplicating it into each one is how the copies drift apart.

---

## Context

UK investor, two family ISAs (~£40k/yr combined). No CGT inside an ISA, so rebalancing is
friction-free. 15% US dividend withholding (W-8BEN); Dutch withholding likewise 15%. Active sleeve
is 20–40% of capital, the rest broad index ETFs plus BRK.B. Sizing 8–15 names at 4–10% at cost.
Sell on broken thesis, deteriorating capital allocation, or structural ROIC decline — **not on
price moves or macro fear**.

Some foreign names are bought on **GETTEX (Munich) in EUR** rather than the home exchange: model
in the reporting currency, price-check in EUR, and treat the cross rate as a first-order swing.

Not investment advice. Research scaffolding only.
