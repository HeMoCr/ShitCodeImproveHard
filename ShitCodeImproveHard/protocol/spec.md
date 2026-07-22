# ShitCodeImproveHard — Single AI Mode

## 0. What It Is

A metacognition framework applied to software production. It is not a development methodology. It is the process that produces development methodologies.

Self-referential:
- **ShitCode** — starting point. The cycle improves it.
- **Improve** — the cT→T→aT pipeline forces movement through layers of abstraction.
- **Hard** — feedback loops close the cycle and correct between iterations.

This is the single-AI version: one AI plays all three roles (Overseer, Strategist, Builder) in sequence within the same session.

---

## 1. Architecture

```
┌─────────────────────────────────┐
│  Overseer                       │  ← Analyzes, evaluates, produces analysis
│  (sees the whole system)        │
└─────────────────────────────────┘
            │
            │ The same AI changes role
            ▼
┌─────────────────────────────────┐
│  Strategist                     │  ← Proposes theory, debates, builds specs
│  (schemes the plan)             │
└─────────────────────────────────┘
            │
            │ Then executes directly
            ▼
┌─────────────────────────────────┐
│  Builder                        │  ← Builds software according to specs
│  (builds the thing)             │
└─────────────────────────────────┘
```

### 1.1 Overseer

- Analyzes patterns the Strategist cannot see
- Produces `overseer-analysis-{stage}.v#.md` post-debate
- Produces `Overseer.Analyze.md` at cycle end
- Maintains `dir_overseer/journal.md`

### 1.2 Strategist

- Proposes theory (cT, T, aT)
- Debates with you
- Waits for "proceed" before producing ConsolidationOutcome
- Prepares specs for the Builder

### 1.3 Builder

- Reads the PRE outcomes produced by the same AI (now in Builder role)
- Builds software according to specs
- Produces `handback.v#.md`
- Does not produce theory or analysis during execution

### 1.4 The Bridge (You)

You remain the bridge between roles:
- Decide when the AI changes role
- Correct when a role steps out of its bounds
- Say "proceed" or "reject"
- Maintain memory between sessions

---

## 2. Pipeline Specification

### 2.1 The Cycle

```
CYCLE:

  [PRE]  AI (Overseer + Strategist)

  cT{#}.v# (craft theory)
    → debate-cT1.v# (Strategist + you)
    → overseer-analysis_cT1.v# (Overseer)
    → you: "proceed"
    → ConsolidationOutcome.cT1.v#.md (Strategist)

  → T{#}.v# (theory)
    → debate-T1.v#
    → overseer-analysis_T1.v#
    → you: "proceed"
    → ConsolidationOutcome.T1.v#.md

  → aT{#}.v# (applied theory — specs)
    → debate-pre-aT1.v#
    → overseer-analysis_pre-aT1.v#
    → you: "proceed"
    → ConsolidationOutcome.aT1.v#.md

  [EXEC]  AI (Builder role)

  Reads PRE outcomes + specs
  Builds the software
  Produces handback.v#.md

  [POST]  AI (Overseer + Strategist)

  ConsolidationOutcome.C.v#.md (raw — sum of all outcomes + handback)
  → Overseer.Analyze.md
  → CycleConsolidation.C.v#.md (fused — travels to next cycle)
  → feedback.v#.md
  → Loop
```

### 2.2 Stage Definitions

| Stage | Phase | Input | Process | Output |
|-------|-------|-------|---------|--------|
| **craftTheory (cT)** | PRE | Signal | Strategist proposes craft theory | `cT{#}.v#.md` |
| **cT Debate** | PRE | `cT{#}.v#.md` | Strategist + you discuss | `debate-cT1.v#.md` |
| **cT Analysis** | PRE | `debate-cT1.v#.md` | Overseer analyzes | `overseer-analysis_cT1.v#.md` |
| **cT Outcome** | PRE | cT + debate + analysis | You "proceed" → Strategist produces | `ConsolidationOutcome.cT1.v#.md` |
| **Theory (T)** | PRE | cT outcome | Strategist formalizes theory | `T{#}.v#.md` |
| **T Debate** | PRE | `T{#}.v#.md` | Strategist + you discuss | `debate-T1.v#.md` |
| **T Analysis** | PRE | `debate-T1.v#.md` | Overseer analyzes | `overseer-analysis_T1.v#.md` |
| **T Outcome** | PRE | T + debate + analysis | You "proceed" → Strategist produces | `ConsolidationOutcome.T1.v#.md` |
| **appliedTheory (aT)** | PRE | T outcome | Strategist prepares specs | `pre-aT1.v#.md` |
| **aT Debate** | PRE | `pre-aT1.v#.md` | Strategist + you discuss | `debate-pre-aT1.v#.md` |
| **aT Analysis** | PRE | `debate-pre-aT1.v#.md` | Overseer analyzes | `overseer-analysis_pre-aT1.v#.md` |
| **aT Outcome** | PRE | aT + debate + analysis | You "proceed" → Strategist produces | `ConsolidationOutcome.aT1.v#.md` |
| **Build** | EXEC | PRE outcomes + specs | Builder builds software | Code, `handback.v#.md` |
| **Sum (∑)** | POST | All outcomes + handback | AI consolidates | `ConsolidationOutcome.C.v#.md` |
| **Overseer Analysis** | POST | Cycle outcome | Overseer analyzes | `Overseer.Analyze.md` |
| **Cycle Consolidation** | POST | Outcome + Overseer analysis | AI fuses | `CycleConsolidation.C.v#.md` |
| **Feedback** | POST | Cycle Consolidation | AI identifies learnings | `feedback.v#.md` |
| **Loop** | POST | Feedback | Copy to next cycle | Next `dir_C.v00X/` |

### 2.3 All Outcomes Are Valid

| Outcome | Meaning | Value |
|---------|---------|-------|
| Success | The theory worked | Validation |
| Failure | It did not work | Data on what does not work |
| Blockage | Could not execute | Reveals bottleneck |
| Discovery | Something unexpected | New pattern |
| Negotiation | Execution became conversation | Trust > code |

---

## 3. Artifact Convention

### 3.1 Naming

```
{category}.{identifier}.v#.{ext}
```

Examples: `cT1.v3.md`, `T1.v2.md`, `pre-aT1.v4.md`

### 3.2 File Reference by Role

#### PRE — Overseer + Strategist

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

#### EXEC — Builder

| File | Where | Creator |
|------|-------|---------|
| `build-aT1.v#.md` | `dir_3.2_build-aT1.v#/` | Builder |
| `handback.v#.md` | `dir_C.v00X/` | Builder |

#### POST — Overseer + Strategist

| File | Where | Creator |
|------|-------|---------|
| `post-aT1.v#.md` | `dir_3.3_post-aT1.v#/` | Strategist |
| `ConsolidationOutcome.C.v#.md` | `dir_C.v00X/` | Strategist |
| `Overseer.Analyze.md` | `dir_C.v00X/` | Overseer |
| `CycleConsolidation.C.v#.md` | `dir_C.v00X/` | Overseer |
| `feedback.v#.md` | `dir_C.v00X/` | Overseer |

### 3.3 Key Rules

1. **No outcome without debate.** ConsolidationOutcome is produced only after you say "proceed"
2. **No analysis without debate.** Overseer only analyzes after Strategist + you discuss
3. **Outcome lives in stage dir** (`dir_1_cT1.v#/`, `dir_2_T1.v#/`, `dir_3_aT1.v#/`)
4. **Builder builds only.** No theory, no analysis during execution
5. **Cycle root files** — handback, ConsolidationOutcome.C, Overseer.Analyze, CycleConsolidation, feedback live in `dir_C.v00X/`

---

## 4. Directory Structure

```
project-root/
├── protocol/                         ← Methodology source (copy from repo)
│   ├── manifesto.md
│   ├── spec.md
│   ├── file-naming.md
│   ├── flowchart-script.md
│   ├── role-Overseer.md
│   ├── role-Strategist.md
│   ├── role-Builder.md
│   ├── ENTRY.template.md
│   └── HANDOFF.template.md
│
├── dir_overseer/                     ← Overseer's workspace (across cycles)
│   ├── journal.md
│   ├── patterns.md
│   ├── overseer-analysis.history.md
│   ├── pipeline-status.md
│   ├── preferences.md
│   └── creation-log.md
│
├── dir_C.v001/                       ← Cycle workspace
│   ├── ENTRY_C.v001.md
│   ├── HANDOFF_C.v001.md
│   │
│   ├── dir_1_cT1.v1/                 ← Stage 1: Craft Theory
│   │   ├── cT1.v1.md
│   │   ├── debate-cT1.v1.md
│   │   ├── overseer-analysis_cT1.v1.md
│   │   ├── ConsolidationOutcome.cT1.v1.md
│   │   └── ENTRY_cT1.v1.md
│   │
│   ├── dir_2_T1.v1/                  ← Stage 2: Theory
│   │   ├── T1.v1.md
│   │   ├── debate-T1.v1.md
│   │   ├── overseer-analysis_T1.v1.md
│   │   ├── ConsolidationOutcome.T1.v1.md
│   │   └── ENTRY_T1.v1.md
│   │
│   ├── dir_3_aT1.v1/                 ← Stage 3: Applied Theory
│   │   ├── dir_3.1_pre-aT1.v1/       ← PRE (specs)
│   │   │   ├── pre-aT1.v1.md
│   │   │   ├── debate-pre-aT1.v1.md
│   │   │   └── overseer-analysis_pre-aT1.v1.md
│   │   ├── dir_3.2_build-aT1.v1/     ← EXEC (Builder)
│   │   │   └── build-aT1.v1.md
│   │   ├── dir_3.3_post-aT1.v1/      ← POST (analysis)
│   │   │   └── post-aT1.v1.md
│   │   ├── ConsolidationOutcome.aT1.v1.md
│   │   └── ENTRY_aT1.v1.md
│   │
│   │   (After EXEC)
│   │
│   ├── handback.v1.md
│   │
│   │   (After POST)
│   │
│   ├── ConsolidationOutcome.C.v1.md
│   ├── Overseer.Analyze.md
│   ├── CycleConsolidation.C.v1.md
│   └── feedback.v1.md
│
├── dir_C.v002/                       ← Next cycle (history grows here)
├── dir_C.v003/
└── README.md
```

---

## 5. Roles (Single AI)

### 5.1 You

- Start each session
- Decide when the AI changes role
- Correct when a role steps out of bounds
- Say "proceed" or "reject"

### 5.2 AI — Overseer Role

- Analyzes patterns
- Produces overseer-analysis post-debate
- Produces Overseer.Analyze.md at cycle end
- Maintains `dir_overseer/journal.md`

### 5.3 AI — Strategist Role

- Proposes theory (cT, T, aT)
- Debates with you
- Waits for "proceed"
- Prepares specs for Builder

### 5.4 AI — Builder Role

- Builds software
- Produces handback
- Does not produce theory or analysis

### 5.5 Rules

1. **Do not change role without you indicating it**
2. **In Overseer role:** only analyze, do not propose theory
3. **In Strategist role:** only propose and debate, do not analyze as Overseer
4. **In Builder role:** only build, do not theorize or analyze
5. **Wait for "proceed" before producing ConsolidationOutcome** (always)
6. **Ask when you do not understand** (always)

---

## 6. Communication Protocol

### AI → You

- Reports which role it is using
- Asks when it does not understand
- Warns about patterns it sees
- Does not act without authorization (except building in EXEC)

### You → AI

- Provides context at start of session
- Indicates which role to use
- Corrects when the AI steps out of bounds
- Says "proceed" or "reject"
- Closes the session

### AI → Future AI (via Files)

The AI does not persist between sessions. But its files do:
- `HANDOFF_C.v#.md` — context for the next session
- `CycleConsolidation.C.v#.md` — fused analysis that travels to next cycle
- `dir_overseer/journal.md` — diary

---

## 7. Cycle Lifecycle

### 7.1 Start

1. Clone/get the protocol files
2. Open an AI session
3. Say: `"Read the ShitCodeImproveHard methodology files. My project is @my_project."`
4. The AI reads the protocol, asks any questions, begins Step 1

### 7.2 Cycle Execution

```
[PRE]  AI (Overseer + Strategist)
1. cT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
2. T → debate → Overseer analyzes → "proceed" → ConsolidationOutcome
3. aT → debate → Overseer analyzes → "proceed" → ConsolidationOutcome

[EXEC] AI (Builder)
4. Build → software → handback

[POST] AI (Overseer + Strategist)
5. Sum → ConsolidationOutcome.C.md
6. Overseer.Analyze.md
7. CycleConsolidation.C.md (fused)
8. Feedback
9. Loop → next cycle
```

### 7.3 Exit Criteria

1. PRE complete: 3 ConsolidationOutcomes produced
2. EXEC complete: handback produced
3. POST complete: ConsolidationOutcome.C.md produced
4. Overseer.Analyze.md produced
5. CycleConsolidation.C.md produced
6. Feedback produced
7. You decide to loop or stop

---

## 8. The Wise-Street Principle

This doesn't claim to be original. It claims to be necessary for those who do not have access to academia but have the hunger to build.

---

*ShitCodeImproveHard — Single AI Mode — July 2026*
