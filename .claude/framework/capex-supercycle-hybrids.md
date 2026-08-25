# Capex-super-cycle / build-ahead hybrids — modelling playbook

Authoritative playbook for AI-platform hybrids that build infrastructure **ahead of
revenue** (hyperscaler cloud, AI compute). Distilled from the GOOGL run; applies to
MSFT (Azure) and inverts for NVDA (see §7). Companion to `methodology-checks.md` —
that file is the gate; this is the archetype-specific construction guide. Trigger it
whenever `/classify` flags a build-ahead engine.

## 1. The template must glide capex AND D&A (not just growth and margin)
A flat capex % held across the window produces a **negative EV** for a build-ahead
name (flat 40%-of-revenue capex did exactly this to GOOGL). Capex % and D&A % are
GLIDE inputs (start → terminal), exactly like EBIT margin. Capex glides DOWN from the
build peak toward a steady state; D&A glides UP as the build comes into service.

## 2. Extend the explicit horizon to ~15 years (10 growth + 5 stable)
A build-ahead engine can run **8+ years of negative FCF** before the J-curve turns. A
10-year window dumps ~85% of value into the terminal (fails methodology #7). A 5-year
stable phase captures the FCF recovery *explicitly*. The two-stage terminal alone is
not enough when near-term FCF is suppressed by construction.

## 3. Owner earnings, and maintenance capex that RISES
Headline FCF is meaningless mid-build. Carry **owner earnings = OCF − maintenance
capex** beside it. But maintenance capex is NOT current depreciation — depreciation
*lags* the build (assets-not-yet-in-service), so maintenance capex is *rising* toward a
higher AI-era steady state. Do NOT assume it reverts to the pre-AI level. Model
maintenance vs growth capex explicitly (CLAUDE.md #5).

## 4. SOTP is primary; allocate the build-ahead capex to the engine that owns the backlog
The consolidated DCF **mis-frames** a hybrid: it charges the whole AI build against the
low-capex cash-cow engine and applies one terminal multiple. Value engines separately;
charge the build-ahead capex (often >100% of that engine's current revenue) only to the
engine that owns the backlog. **The SOTP total is robust to the allocation; the split
only shifts value between engines** — flag the split as the #1 assumption, not a fatal
one. Re-run the consolidated cross-check after ANY base revision (it goes stale silently).

## 5. The discount rate is the dominant swing — frame the verdict around it
For a terminal-heavy build-ahead name the **discount rate dominates everything**: GOOGL
was $296 @9% vs $381 @8% — the entire gap to the market price (and to notable buyers) was
the hurdle, not the business. Always run the **rate bridge** and state the verdict as
"fair value at hurdle X," never a point. Distinguish **through-cycle beta from spot beta**
(spot is inflated by the AI run-up). A fortress-balance-sheet compounder rationally
warrants a lower hurdle than a margin-of-safety active hurdle — say which lens you use.

**Method note — WACC vs APV.** A constant-weight WACC assumes a *fixed* capital
structure. A build-ahead funded with debt that then **deleverages** as the J-curve turns
violates that assumption, and the WACC understates value early / overstates it late. Where
the debt path is material and time-varying, value with **APV** instead: unlevered FCFF at
the asset return + PV of the tax shields (and − PV of distress) discounted separately
(methodology #18). The SOTP framing (§4) already points here — the build-ahead engine's
financing is engine-specific, not a group constant.

## 6. Two recurring traps
- **The "smuggled bull":** a segment CAGR set against a peer's *scale* and back-solved to
  revenue, with no share-bridge (GOOGL Cloud "$462bn in Y10"). Require a named
  share-bridge (logo wins / displacement) or relabel as "riding TAM" and move the
  unsupported version to the Bull. Watch for a revision that lifts the answer through the
  least-supported inputs.
- **Margin gliding toward a FALLING target:** don't glide "toward peer margins" when
  those peer margins are themselves compressing from the same AI-depreciation wave (AWS
  39.5%→32.9% within 2025). A *relative* cost edge (custom silicon) against a *falling
  absolute* is not a *rising* margin. And don't double-count one story as two tailwinds
  (lower-margin hardware-supply mix is growth-up / margin-down).

## 7. NVDA inverts this playbook (apply for cross-company consistency)
NVDA is **fab-light** → §1–§3 (capex glide, J-curve, owner-earnings) are largely moot.
One dominant engine (Data Center). The swing is **cyclicality + substitution**, not
capex. Critically: NVDA is the *beneficiary* of the very hyperscaler capex the GOOGL/MSFT
models charge — so the capex *normalisation* that *recovers* GOOGL/MSFT FCF *compresses*
NVDA revenue. **Keep the three models mutually consistent.** Custom-ASIC substitution is
NVDA's *threat* (the same TPU/Trainium share-gain credited to the cloud engines). Stress
the ~75% gross margin against hyperscaler in-sourcing; prefer reverse-DCF; don't
capitalise a cyclical peak into the terminal.

## MSFT quick-reference (next run)
Same Azure build-ahead as Google Cloud (§1–§5 apply). Per-segment operating income IS
disclosed (cleaner SOTP spine than GOOGL). Azure discloses growth % not $ — reconstruct
the $ base. **The OpenAI stake is the load-bearing item**: capped-profit / economic-
interest structure + MSFT↔OpenAI↔Azure circularity (a larger version of the
Anthropic↔Google related-party flag) — scrutinise like a lender's primitive.
