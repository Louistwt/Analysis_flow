# Model refinements — lessons from the GOOGL run (apply to MSFT, then NVDA)

Cross-company feedback distilled from valuing Alphabet. The next two names (MSFT,
NVDA) are AI-era hybrids with the same structural traps — most of these are
reusable, a few invert. Ordered by impact.

---

## A. The DCF template needs structural fixes (do these before MSFT)

1. **Capex % and D&A % must GLIDE (start → terminal), not be flat.** The single
   biggest mechanical failure: a flat 40%-of-revenue capex held for 10 years gave
   GOOGL a *negative* enterprise value. The template glides revenue growth and EBIT
   margin but not capex/D&A — fatal for any capex-super-cycle name. *MSFT/Azure: same
   fix required. NVDA: largely moot (fab-light) — see §F.*

2. **Extend the explicit horizon to 15 years (10 growth + 5 stable) for build-ahead
   names.** GOOGL Cloud had 8 years of negative FCF, dumping ~85% of value into the
   terminal (methodology check #7 fails). A 5-year stable phase captures the FCF
   recovery *explicitly* and cuts TV-reliance below ~65%. The H-model alone is not
   enough when the J-curve is this deep.

3. **Add an owner-earnings line (OCF − maintenance capex) beside headline FCF.**
   Headline FCF is meaningless mid-build. But maintenance capex is NOT the current
   depreciation — depreciation *lags* the build (assets-not-yet-in-service), so
   maintenance capex is *rising* toward a higher AI-era steady state, not reverting to
   the pre-AI ~12% of revenue. Model it between the two.

4. **WACC: per-engine + a sensitivity that spans the *required-return* debate
   (≈8%–11%).** For a terminal-heavy AI name the discount rate dominates everything —
   see §D. Make it the first thing you flex, not an afterthought.

---

## B. SOTP is PRIMARY for a hybrid; the consolidated DCF MIS-FRAMES it

The most important valuation insight of the run. A single blended DCF **charges the
entire AI build against the low-capex cash-cow engine** and applies one terminal
multiple — it crushed GOOGL to a nonsensical −54%. The SOTP (value Services and Cloud
separately, charge the build only to Cloud) is the correct primary; the consolidated
DCF is a cross-check only.

- **Allocate build-ahead capex to the engine that owns the backlog.** The *total* is
  robust to the split; the per-engine split only shifts value between engines. Flag
  the split as the #1 assumption and a /redteam target.
- **Reusable structure (built live in Drive):** one tab per engine + a central-cost
  tab (capitalised after-tax R&D/corporate drag) + a SOTP-bridge tab that sums engine
  EVs and adds net cash, strategic stakes, and non-marketable equity.
- **Re-run the consolidated cross-check after ANY base revision.** We left it stale at
  the pre-revision number — caught only by the red team. Automate the reconciliation.

---

## C. Growth must reconcile to a disclosed primitive — and where it can't, SAY SO

- Only **Search** had a disclosed volume×price (paid clicks × CPC). Cloud/YouTube/Subs
  primitives are **undisclosed** → their forward paths are *bounded* (penetration,
  peers) but *not reconciled* to volume×price. Label these "assertion-grade," not
  primitive-reconciled. Don't let an undisclosed-primitive engine look as solid as a
  reconciled one.
- **Ground growth to NAMED competitor primitives** (AWS/Azure histories anchored the
  Cloud call). But beware the **"smuggled bull": a CAGR set against peer *scale* then
  back-solved to revenue, with no share-bridge.** GOOGL Cloud's "$462bn in Y10" assumed
  Google takes share AWS/Azure don't give up — require a share-bridge (named logo wins /
  displacement) or relabel as "riding TAM," and move the unsupported version to the Bull.
- **Companies measure differently — only compare like-for-like.** Meta reports
  impressions × price-per-impression; Google reports clicks × CPC. The volume/price
  *halves* aren't comparable; only *total revenue growth* is. (We initially compared
  them wrongly.)
- **Pull competitor primitives EARLY**, before setting the base — we did AWS/Azure late
  and had to re-open the base.

---

## D. The discount rate is the dominant swing for terminal-heavy AI names

GOOGL base = **$296 at 9% WACC vs $381 at 8%** — the *entire* gap between our verdict
and the market price (and Berkshire's $350 accumulation) was the hurdle rate, not the
business. Lessons:
- Always run the **WACC bridge** and frame the verdict as "fair value at hurdle X,"
  never a single point.
- **Distinguish through-cycle beta from spot beta** — spot is inflated by the AI run-up
  (GOOGL 5Y β 1.24 vs through-cycle ~1.0–1.1).
- A fortress-balance-sheet compounder rationally warrants a *lower* hurdle (the
  permanent-capital / quality-compounder lens) than an active-investor margin-of-safety
  hurdle. State which lens you're using.

---

## E. Margins-as-output, plus the AI-depreciation industry headwind

- Terminal margin must be a **mix-weighted output**, not a top-down number.
- **Don't glide "toward peer margins" when peer margins are themselves compressing.**
  AWS fell 39.5%→32.9% within 2025 from AI-depreciation. A *relative* cost edge (TPU)
  against a *falling absolute* does not produce a *rising* margin.
- **Don't double-count one story as two tailwinds.** The TPU-hardware-supply deals are
  growth-up *and* margin-down (lower-margin mix) — the base wrongly treated them as both
  a revenue and a margin tailwind.

---

## F. Specifically for MSFT (next)

- **Same hybrid + same Azure build-ahead dynamics as Google Cloud** → §A and §B apply
  almost verbatim. Capex glide essential.
- **Engines:** Productivity & Business Processes (Office/LinkedIn/Dynamics — SaaS:
  seats × ARPU × NRR) / Intelligent Cloud (Azure — the build-ahead engine) / More
  Personal Computing (Windows/Search/Gaming — mature-to-declining mix). **Per-segment
  operating income IS disclosed** → a cleaner SOTP spine than GOOGL.
- **Azure discloses growth % not $** — reconstruct the $ base from Intelligent Cloud.
  Same TV-reliance + J-curve as Google Cloud.
- **The OpenAI stake is NOT a clean equity line** — model the capped-profit / economic-
  interest structure and the **circularity** (MSFT funds OpenAI, OpenAI buys Azure
  compute) — the same related-party flag we raised on Anthropic↔Google, but *larger and
  more material*. This is the load-bearing primitive to scrutinise for MSFT.

## G. Specifically for NVDA (after) — where the lessons INVERT

- **NOT a capex-super-cycle name (fab-light)** → the §A capex/D&A-glide fix and the
  J-curve are largely moot. Different model shape.
- **One dominant engine** (Data Center ~90% of value) + tails (Gaming/ProViz/Auto).
  SOTP matters less; the swing is **Data-Center cyclicality + substitution risk**, not
  capex allocation.
- **Model the cross-company linkage (a consistency discipline):** NVDA is the
  *beneficiary* of the very AI capex our GOOGL/MSFT models charge. The same hyperscaler
  capex *normalisation* that *recovers* GOOGL/MSFT FCF *compresses* NVDA revenue. A bear
  on hyperscaler capex must be a bear on NVDA — keep the three models mutually consistent.
- **Custom-ASIC substitution is NVDA's threat, not its edge.** The TPU/Trainium/Maia
  share-gain we credited to GOOGL/MSFT is merchant-GPU share *loss* for NVDA. Model it.
- **Stress the 75% gross margin** — can it hold as custom silicon scales and hyperscalers
  in-source? And **customer concentration is extreme** (a few hyperscalers = most of
  Data Center).
- **Use reverse-DCF / what's-priced-in** rather than forward-DCF for a hyper-growth,
  cyclical, sentiment-driven name. Beware capitalising a cyclical *peak* into the terminal.

---

## H. Process / discipline refinements
- Ground the **bear in observed deterioration**, and hold the **base's fade endpoints to
  the same standard** — don't let the base be optimistic while the bear is grounded.
- **Re-center spreads** — a bear barely below the base (Cloud margin 25 vs 33) is
  mis-centered and understates risk.
- Treat **external signals (Berkshire) as disconfirming data, not confirmation** — use
  them to stress your hurdle, not to anchor your answer.
- Watch for a **"smuggled bull"**: a revision that lifts the answer through the
  least-supported inputs (GOOGL's $237→$323 came entirely from the two soft engines).
