# ShitCodeImproveHard

A metacognition metaframework for software development. One AI, three roles, iterative cycle.

It's not a development methodology. It's the process that produces development methodologies.

The code is shit at first. Progress comes through structured iteration. Improvement is the result of feedback cycles closing between what you think and what you build.

---

> **Not limited to software.** This works for research, writing, design, strategy — anything that benefits from structured iteration. Builder can be whatever you need it to be. Blend it however you want. It's open source. It's flexible.

> **"ImproveHard"** means improve relentlessly, the hard way — through iteration, feedback, and metacognition. No shortcuts. No silver bullets. Just the loop.

## The Three Roles

| Role | Inspired by | Does |
|------|-------------|------|
| **Overseer** | Watches the whole system, analyzes patterns, produces analysis. Never builds. |
| **Strategist** | Proposes theory (cT → T → aT), debates with you, prepares specs. |
| **Builder** | Reads specs, builds the software, reports back. Does not theorize during execution. |

In single-AI mode, one AI plays all three roles in sequence. You tell it when to switch.

---

## Quickstart

1. Clone this repo
2. Open a chat with an AI
3. Paste this:

```
@ShitCodeImproveHard/ projectname: @my_project
```

Or, if you want to answer questions interactively:

> "Read the ShitCodeImproveHard methodology files. My project is @my_project."

The AI reads the protocol files, asks any needed questions, and proceeds.

4. Switch between roles anytime with:
   - `@Overseer` — analyze, observe, reflect
   - `@Strategist` — propose theory, debate, plan
   - `@Builder` — execute, build, deliver

---

## The Cycle

```
┌──────────────────────────────────────────────────┐
│  PRE — Strategist proposes, Overseer analyzes    │
│                                                  │
│  cT (craft theory) → debate → Overseer analyzes →│
│    "proceed" → ConsolidationOutcome.cT1.md       │
│  → T (theory) → debate → Overseer analyzes →     │
│    "proceed" → ConsolidationOutcome.T1.md         │
│  → aT (applied theory/specs) → debate →           │
│    Overseer analyzes → "proceed" →               │
│    ConsolidationOutcome.aT1.md                   │
└──────────────────────────────────────────────────┘
                         ↓
┌──────────────────────────────────────────────────┐
│  EXEC — Builder builds                           │
│  Reads PRE outcomes + specs, builds software,     │
│  produces handback.md                            │
└──────────────────────────────────────────────────┘
                         ↓
┌──────────────────────────────────────────────────┐
│  POST — Overseer + Strategist close the cycle     │
│  ConsolidationOutcome.C.md (raw)                  │
│  → Overseer.Analyze.md                            │
│  → CycleConsolidation.C.md (fused, travels next)  │
│  → feedback.md → loop                             │
└──────────────────────────────────────────────────┘
```

---

## Why "ShitCode"

Because the starting point doesn't matter. A mediocre completed iteration is worth more than a perfect aborted one. The loop is the point.

---

## License

MIT. Anyone can take it. If you make millions using this, at least buy me a coffee. Or don't. I'll never know.
