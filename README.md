# Equity Research Pipeline (Claude Code)

A staged, human-gated research workflow that turns an industry/company idea into
a defensible set of **bear / base / bull** DCF assumptions. Each stage is a
Claude Code slash command you run **one at a time**, reviewing the output file
before firing the next.

The DCF model itself lives in Google Sheets and stays the single source of
truth. This pipeline produces *inputs* for it — it never rewrites the model.

---

## How it works

1. Open a terminal in `companies/<TICKER>/` (copy `companies/_TEMPLATE` to start).
2. Run `claude`.
3. Fill in `00-brief.md` (what you want to look at and why).
4. Run the stages in order, reviewing each output file before the next:

| # | Command | Reads | Writes |
|---|---------|-------|--------|
| 1 | `/classify` | 00-brief.md | 01-classification.md |
| 2 | `/deepresearch-prompt` | 01 | 02-dr-prompt.md |
| 3 | *(run the prompt in Gemini DeepResearch, paste output)* | — | 03-gemini-report.md |
| 4 | `/critique-report` | 03 | 04-critique.md |
| 5 | `/industry-map` | 03, 04 | 05-industry-map.md |
| 6 | `/tech-deepdive` | 05 | 06-tech.md |
| 7 | `/assumptions` | 04, 05, 06 | 07-assumptions.md |
| 8 | `/redteam` | 07 (+ all) | 08-redteam.md |
| 9 | `/verdict` | all | 09-verdict.md |

5. Paste the numbers from `07-assumptions.md` into the **blue input cells** of
   your Google Sheet DCF (one scenario per column). Re-run `/assumptions` after
   `/redteam` if the red team moved anything.

Stages 4 and 8 run in an **isolated subagent** (`skeptic`) so the bull-case
reasoning can't contaminate the critique. That isolation is the whole point —
not speed.

---

## Why the manual Sheet hand-off (and how to automate later)

42 input cells take ~2 minutes to paste, and pasting by hand means you review
every number and never risk clobbering a formula cell. Keep it manual to start.

**Optional automation (later):** add a Google Sheets MCP server to this Claude
Code project and point it *only* at the input range. Then `/assumptions` can
write the blue cells directly. Keep a versioned copy of the sheet first, and
never give the MCP write access to formula cells. Setup: see
`https://docs.claude.com/en/docs/claude-code/overview` → MCP.

---

## Core principles baked into every stage (see CLAUDE.md)

- **Base case is indicative, not an answer.** A DCF is a hypothesis; risk is
  managed through the *width* of the Bear–Bull spread, not a precise point.
- **Provenance travels with every number.** Each assumption cites its source.
- **Reliability tagging.** Only `hard` figures move the Base case; `soft` and
  `unsupported` ones widen the spread instead.
- **Quality gate before valuation.** A cheap price on a narrowing moat is a pass.

---

## Files

```
CLAUDE.md                     # shared brain: framework, substitution model, conventions
.claude/commands/*.md         # the 8 pipeline stages (your /commands)
.claude/agents/skeptic.md     # isolated adversarial subagent
companies/_TEMPLATE/          # copy this per company
```

Not investment advice. Research scaffolding only.
