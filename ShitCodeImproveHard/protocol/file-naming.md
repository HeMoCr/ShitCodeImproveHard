# ShitCodeImproveHard — File Naming & Directory Structure

## Naming Pattern

```
{category}.{identifier}.v#.{ext}
```

## Files by Stage

### PRE — Overseer + Strategist

| File | Where | Creator |
|------|-------|---------|
| `ENTRY_C.v#.md` | `dir_C.v00X/` | Overseer |
| `HANDOFF_C.v#.md` | `dir_C.v00X/` | Overseer |
| `cT{#}.v#.md` | `dir_1_cT1.v#/` | Strategist |
| `T{#}.v#.md` | `dir_2_T1.v#/` | Strategist |
| `pre-aT1.v#.md` | `dir_3.1_pre-aT1.v#/` | Strategist |
| `debate-cT1.v#.md` | `dir_1_cT1.v#/` | Strategist + you |
| `debate-T1.v#.md` | `dir_2_T1.v#/` | Strategist + you |
| `debate-pre-aT1.v#.md` | `dir_3.1_pre-aT1.v#/` | Strategist + you |
| `overseer-analysis_cT1.v#.md` | `dir_1_cT1.v#/` | Overseer |
| `overseer-analysis_T1.v#.md` | `dir_2_T1.v#/` | Overseer |
| `overseer-analysis_pre-aT1.v#.md` | `dir_3.1_pre-aT1.v#/` | Overseer |
| `ConsolidationOutcome.cT1.v#.md` | `dir_1_cT1.v#/` | Strategist |
| `ConsolidationOutcome.T1.v#.md` | `dir_2_T1.v#/` | Strategist |
| `ConsolidationOutcome.aT1.v#.md` | `dir_3_aT1.v#/` | Strategist |
| `ENTRY_cT1.v#.md` | `dir_1_cT1.v#/` | Overseer |
| `HANDOFF_cT1.v#.md` | `dir_1_cT1.v#/` | Overseer |
| `ENTRY_T1.v#.md` | `dir_2_T1.v#/` | Overseer |
| `HANDOFF_T1.v#.md` | `dir_2_T1.v#/` | Overseer |
| `ENTRY_aT1.v#.md` | `dir_3_aT1.v#/` | Overseer |
| `HANDOFF_aT1.v#.md` | `dir_3_aT1.v#/` | Overseer |

### EXEC — Builder

| File | Where | Creator |
|------|-------|---------|
| `build-aT1.v#.md` | `dir_3.2_build-aT1.v#/` | Builder |
| `handback.v#.md` | `dir_C.v00X/` | Builder |

### POST — Overseer + Strategist

| File | Where | Creator |
|------|-------|---------|
| `post-aT1.v#.md` | `dir_3.3_post-aT1.v#/` | Strategist |
| `ConsolidationOutcome.C.v#.md` | `dir_C.v00X/` | Strategist |
| `Overseer.Analyze.md` | `dir_C.v00X/` | Overseer |
| `CycleConsolidation.C.v#.md` | `dir_C.v00X/` | Overseer |
| `feedback.v#.md` | `dir_C.v00X/` | Overseer |

## Rules

1. **ConsolidationOutcome.*.md** is produced only after you say "proceed"
2. **aT sub-stages use prefix** — `pre-aT`, `build-aT`, `post-aT`
3. **Outcome lives at stage root** — `ConsolidationOutcome.aT1.v#.md` goes in `dir_3_aT1.v#/`, not in a sub-stage
4. **Cycle root files** — handback, ConsolidationOutcome.C, Overseer.Analyze, CycleConsolidation, feedback live in `dir_C.v00X/`
5. **Protocol files live in `protocol/`** — manifesto.md, spec.md, file-naming.md, flowchart-script.md, role-Overseer.md, role-Strategist.md, role-Builder.md, ENTRY.template.md, HANDOFF.template.md
6. **Overseer files live in `dir_overseer/`** — journal.md, patterns.md, overseer-analysis.history.md, pipeline-status.md, preferences.md, creation-log.md (persist across cycles)

## Full Directory Structure

```
project-root/
├── protocol/
│   ├── manifesto.md
│   ├── spec.md
│   ├── file-naming.md
│   ├── role-Overseer.md
│   ├── role-Strategist.md
│   ├── role-Builder.md
│   ├── ENTRY.template.md
│   └── HANDOFF.template.md
│
├── dir_overseer/
│   ├── journal.md
│   ├── patterns.md
│   ├── overseer-analysis.history.md
│   ├── pipeline-status.md
│   ├── preferences.md
│   └── creation-log.md
│
├── dir_C.v001/
│   ├── ENTRY_C.v001.md
│   ├── HANDOFF_C.v001.md
│   ├── dir_1_cT1.v1/
│   │   ├── ENTRY_cT1.v1.md
│   │   ├── HANDOFF_cT1.v1.md
│   │   ├── cT1.v1.md
│   │   ├── debate-cT1.v1.md
│   │   ├── overseer-analysis_cT1.v1.md
│   │   ├── ConsolidationOutcome.cT1.v1.md
│   │   └── (meta-feedback optional)
│   ├── dir_2_T1.v1/
│   │   ├── ENTRY_T1.v1.md
│   │   ├── HANDOFF_T1.v1.md
│   │   ├── T1.v1.md
│   │   ├── debate-T1.v1.md
│   │   ├── overseer-analysis_T1.v1.md
│   │   ├── ConsolidationOutcome.T1.v1.md
│   │   └── (meta-feedback optional)
│   ├── dir_3_aT1.v1/
│   │   ├── ENTRY_aT1.v1.md
│   │   ├── HANDOFF_aT1.v1.md
│   │   ├── dir_3.1_pre-aT1.v1/
│   │   │   ├── pre-aT1.v1.md
│   │   │   ├── debate-pre-aT1.v1.md
│   │   │   └── overseer-analysis_pre-aT1.v1.md
│   │   ├── dir_3.2_build-aT1.v1/
│   │   │   └── build-aT1.v1.md
│   │   ├── dir_3.3_post-aT1.v1/
│   │   │   └── post-aT1.v1.md
│   │   ├── ConsolidationOutcome.aT1.v1.md
│   │   └── (meta-feedback optional)
│   ├── handback.v1.md
│   ├── ConsolidationOutcome.C.v1.md
│   ├── Overseer.Analyze.md
│   ├── CycleConsolidation.C.v1.md
│   └── feedback.v1.md
│
├── dir_C.v002/
└── README.md
```
