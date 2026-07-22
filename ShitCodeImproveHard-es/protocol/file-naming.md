# ShitCodeImproveHard — Nombrado de Archivos y Estructura de Directorios

## Patrón de Nombrado

```
{categoría}.{identificador}.v#.{ext}
```

## Archivos por Etapa

### PRE — Overseer + Strategist

| Archivo | Dónde | Creador |
|---------|-------|---------|
| `ENTRY_C.v#.md` | `dir_C.v00X/` | Overseer |
| `HANDOFF_C.v#.md` | `dir_C.v00X/` | Overseer |
| `cT{#}.v#.md` | `dir_1_cT1.v#/` | Strategist |
| `T{#}.v#.md` | `dir_2_T1.v#/` | Strategist |
| `pre-aT1.v#.md` | `dir_3.1_pre-aT1.v#/` | Strategist |
| `debate-cT1.v#.md` | `dir_1_cT1.v#/` | Strategist + tú |
| `debate-T1.v#.md` | `dir_2_T1.v#/` | Strategist + tú |
| `debate-pre-aT1.v#.md` | `dir_3.1_pre-aT1.v#/` | Strategist + tú |
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

| Archivo | Dónde | Creador |
|---------|-------|---------|
| `build-aT1.v#.md` | `dir_3.2_build-aT1.v#/` | Builder |
| `handback.v#.md` | `dir_C.v00X/` | Builder |

### POST — Overseer + Strategist

| Archivo | Dónde | Creador |
|---------|-------|---------|
| `post-aT1.v#.md` | `dir_3.3_post-aT1.v#/` | Strategist |
| `ConsolidationOutcome.C.v#.md` | `dir_C.v00X/` | Strategist |
| `Overseer.Analyze.md` | `dir_C.v00X/` | Overseer |
| `CycleConsolidation.C.v#.md` | `dir_C.v00X/` | Overseer |
| `feedback.v#.md` | `dir_C.v00X/` | Overseer |

## Reglas

1. **ConsolidationOutcome.*.md** se produce solo después de "proceder"
2. **Sub-etapas de aT usan prefijo** — `pre-aT`, `build-aT`, `post-aT`
3. **Outcome vive en la raíz de la etapa** — `ConsolidationOutcome.aT1.v#.md` va en `dir_3_aT1.v#/`, no en una sub-etapa
4. **Archivos raíz del ciclo** — handback, ConsolidationOutcome.C, Overseer.Analyze, CycleConsolidation, feedback viven en `dir_C.v00X/`
5. **Archivos de protocolo viven en `protocol/`** — manifesto.md, spec.md, file-naming.md, flowchart-script.md, role-Overseer.md, role-Strategist.md, role-Builder.md, ENTRY.template.md, HANDOFF.template.md
6. **Archivos del Overseer viven en `dir_overseer/`** — journal.md, patterns.md, overseer-analysis.history.md, pipeline-status.md, preferences.md, creation-log.md (persisten entre ciclos)

## Estructura Completa de Directorios

```
project-root/
├── protocol/
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
│   ├── dir_2_T1.v1/
│   │   ├── ENTRY_T1.v1.md
│   │   ├── HANDOFF_T1.v1.md
│   │   ├── T1.v1.md
│   │   ├── debate-T1.v1.md
│   │   ├── overseer-analysis_T1.v1.md
│   │   ├── ConsolidationOutcome.T1.v1.md
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
│   ├── handback.v1.md
│   ├── ConsolidationOutcome.C.v1.md
│   ├── Overseer.Analyze.md
│   ├── CycleConsolidation.C.v1.md
│   └── feedback.v1.md
│
├── dir_C.v002/
└── README.md
```
