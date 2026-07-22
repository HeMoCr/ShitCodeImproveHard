# HANDOFF — Ciclo {C.v#}

Contexto para la siguiente sesión de AI que entre a este ciclo. Leer antes de comenzar.

## Arquitectura

Dos capas operando en paralelo:

- **Overseer** — alcance total, observa, analiza. No toca el mundo físico.
- **Strategist + Builder** — alcance del pipeline, ejecuta, construye, produce artefactos.

Tú (el humano) vives en ambas capas y traduces entre ellas.

## Roles

| Rol | Fase | Hace |
|-----|------|------|
| Overseer | PRE + POST | Analiza, produce overseer-analysis, Overseer.Analyze.md |
| Strategist | PRE + POST | Propone teoría (cT, T, aT), debate, produce ConsolidationOutcome |
| Builder | EXEC | Lee outcomes PRE, construye software, produce handback |

## Pipeline

```
[PRE]  Overseer + Strategist
  cT → debate → Overseer analiza → "proceder" → ConsolidationOutcome
  → T → debate → Overseer analiza → "proceder" → ConsolidationOutcome
  → aT → debate → Overseer analiza → "proceder" → ConsolidationOutcome

[EXEC] Builder
  Lee outcomes PRE, construye, produce handback

[POST] Overseer + Strategist
  Suma → ConsolidationOutcome.C → Overseer.Analyze → CycleConsolidation → Feedback → Loop
```

## Reglas Críticas

1. **No hay outcome antes de "proceder".** ConsolidationOutcome requiere tu autorización explícita después del debate y análisis del Overseer.
2. **Builder solo construye.** Sin teoría, sin análisis durante ejecución.
3. **Outcomes viven en directorios de etapa.** `dir_1_cT1.v#/`, `dir_2_T1.v#/`, `dir_3_aT1.v#/`.
4. **Declara tu rol.** Siempre di qué rol estás jugando. Si no lo haces, pregunta.

## Estado Actual

| Etapa | Estado |
|-------|--------|
| cT | ⏳ pendiente |
| T | ⏳ pendiente |
| aT | ⏳ pendiente |
| EXEC | ⏳ pendiente |
| POST | ⏳ pendiente |

---

*HANDOFF_C.v{#} — {Fecha}*
