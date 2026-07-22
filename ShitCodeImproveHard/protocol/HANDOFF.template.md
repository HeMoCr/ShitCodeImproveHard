# HANDOFF — Cycle {C.v#}

Context for the next AI session entering this cycle. Read before starting.

## Architecture

Two layers operating in parallel:

- **Overseer** — total scope, observes, analyzes. Does not touch the physical world.
- **Strategist + Builder** — pipeline scope, executes, builds, produces artifacts.

You (the human) live in both layers and translate between them.

## Roles

| Role | Phase | Does |
|------|-------|------|
| Overseer | PRE + POST | Analyzes, produces overseer-analysis, Overseer.Analyze.md |
| Strategist | PRE + POST | Proposes theory (cT, T, aT), debates, produces ConsolidationOutcome |
| Builder | EXEC | Reads PRE outcomes, builds software, produces handback |

## Pipeline

```
[PRE]  Overseer + Strategist
  cT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
  → T → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
  → aT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome

[EXEC] Builder
  Reads PRE outcomes, builds, produces handback

[POST] Overseer + Strategist
  Sum → ConsolidationOutcome.C → Overseer.Analyze → CycleConsolidation → Feedback → Loop
```

## Critical Rules

1. **No outcome before "proceed".** ConsolidationOutcome requires your explicit authorization after debate and Overseer analysis.
2. **Builder builds only.** No theory, no analysis during execution.
3. **Outcomes live in stage dirs.** `dir_1_cT1.v#/`, `dir_2_T1.v#/`, `dir_3_aT1.v#/`.
4. **State your role.** Always state which role you are playing. If not stated, ask.

## Current State

| Stage | Status |
|-------|--------|
| cT | ⏳ pending |
| T | ⏳ pending |
| aT | ⏳ pending |
| EXEC | ⏳ pending |
| POST | ⏳ pending |

---

*HANDOFF_C.v{#} — {Date}*
