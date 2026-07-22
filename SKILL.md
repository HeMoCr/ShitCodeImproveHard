---
name: shitcode-improvehard
description: Metacognition framework for solo developers working with AI. Three roles (Overseer, Strategist, Builder) run a PRE→EXEC→POST pipeline with cT→T→aT theory progression. Use when starting a project, feeling lost in scope, hitting blockers, or needing structured iteration with your AI assistant.
---

# ShitCodeImproveHard

A metacognition metaframework. Not a development methodology — it's the process that produces methodologies.

## Quickstart

When you're ready to start a cycle, tell the AI:

```
@ShitCodeImproveHard/ projectname: @my_project
```

Then switch roles anytime:
- **`@Overseer`** — analyze, observe, reflect
- **`@Strategist`** — propose theory, debate, plan
- **`@Builder`** — execute, build, deliver

## The Three Roles

| Role | Does |
|------|------|
| **Overseer** | Sees the whole system, analyzes patterns, produces analysis. Never builds. Maintains `dir_overseer/`. |
| **Strategist** | Proposes theory (cT → T → aT), debates with you, prepares specs. |
| **Builder** | Reads specs, builds, produces `handback.md`. No theorizing during execution. |

One AI plays all three in sequence. You decide when it switches roles.

## The Pipeline

```
PRE   → cT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
      → T → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
      → aT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome

EXEC  → Builder reads outcomes + specs, builds, writes handback.md

POST  → ConsolidationOutcome.C.md → Overseer.Analyze.md
      → CycleConsolidation.C.md → feedback.md → loop
```

Every stage requires debate + Overseer analysis before "proceed". No shortcuts.

## Rules

1. No outcome without debate
2. No analysis without debate
3. Builder only builds — no theory, no analysis during EXEC
4. Wait for "proceed" before producing ConsolidationOutcome
5. Ask when you don't understand

## File Structure

```
protocol/             ← Methodology source (copy these into your project)
├── spec.md           ← Full pipeline specification
├── manifesto.md      ← Philosophy and principles
├── flowchart-script.md ← Process map with decision points
├── role-Overseer.md
├── role-Strategist.md
├── role-Builder.md
├── ENTRY.template.md
└── HANDOFF.template.md

dir_overseer/         ← Overseer workspace (between cycles)
├── journal.md
├── patterns.md
├── preferences.md
└── ...
```

## Deep Reference

- **Full spec**: See [protocol/spec.md](protocol/spec.md) for complete pipeline details, artifact naming, and directory structure
- **Philosophy**: See [protocol/manifesto.md](protocol/manifesto.md) for the principles and constraints
- **Overseer role**: See [protocol/role-Overseer.md](protocol/role-Overseer.md) for List:Yes/List:No services and what the Overseer can write
- **Strategist role**: See [protocol/role-Strategist.md](protocol/role-Strategist.md) for theory proposal rules
- **Builder role**: See [protocol/role-Builder.md](protocol/role-Builder.md) for build execution rules
- **Process map**: See [protocol/flowchart-script.md](protocol/flowchart-script.md) for Mermaid diagram and decision table
