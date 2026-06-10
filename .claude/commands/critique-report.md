---
description: Audit the Gemini DeepResearch report for reliability (isolated skeptic)
---

Delegate this entire task to the **`skeptic` subagent** so it runs in a clean
context with no exposure to any bull-case reasoning. Pass it `03-gemini-report.md`.

Instruct the skeptic to write `04-critique.md` containing:

1. **Reliability ledger** — a table of every material claim/number in the
   report, each tagged:
   - `hard` — primary-sourced, recent, and corroborated
   - `soft` — single source, estimate, or dated
   - `unsupported` — asserted with no traceable basis
   For each, note the source (or "none") and any internal contradiction.
2. **Unsupported confidence** — places where the report states something
   firmly that the evidence does not justify.
3. **Omissions** — what a skeptical professional would expect that the report
   skipped (competitor response, customer concentration, accounting flags,
   refinancing, dilution, regulatory exposure).
4. **Recency / narrative / confirmation bias** — where present.
5. **Verdict** — is this report a usable foundation, or does a section need
   re-running in Gemini before proceeding?

The skeptic must not soften findings. If a number is unsupported, it says so.
