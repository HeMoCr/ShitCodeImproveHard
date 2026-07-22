# ShitCodeImproveHard

Un metaframework de metacognición para desarrollo de software. Un AI, tres roles, ciclo iterativo.

No es una metodología de desarrollo. Es el proceso que produce metodologías de desarrollo.

El código es una mierda al principio. El progreso viene con iteración estructurada. La mejora es el resultado de ciclos de retroalimentación entre lo que piensas y lo que construyes.

---

## Los Tres Roles

| Rol | Hace |
|-----|------|
| **Overseer** | Observa todo el sistema, analiza patrones, produce meta-análisis. Nunca construye. |
| **Strategist** | Propone teoría (cT → T → aT), debate contigo, prepara especificaciones. |
| **Builder** | Lee especificaciones, construye el software, reporta resultados. No teoriza durante ejecución. |

En modo single-AI, un solo AI juega los tres roles en secuencia. Tú le dices cuándo cambiar.

---

## Inicio Rápido

1. Clona este repositorio
2. Abre un chat con un AI
3. Pega esto:

```
@ShitCodeImproveHard/ projectname: @mi_proyecto
```

O si prefieres responder preguntas:

> "Lee los archivos de ShitCodeImproveHard. Mi proyecto es @mi_proyecto."

El AI lee los archivos de protocolo, pregunta lo necesario, y procede.

4. Cambia de rol en cualquier momento con:
   - `@Overseer` — analizar, observar, reflexionar
   - `@Strategist` — proponer teoría, debatir, planificar
   - `@Builder` — ejecutar, construir, entregar

---

## El Ciclo

```
┌──────────────────────────────────────────────────┐
│  PRE — Strategist propone, Overseer analiza      │
│                                                  │
│  cT (teoría artesanal) → debate → Overseer       │
│    analiza → "proceder" → ConsolidationOutcome   │
│  → T (teoría) → debate → Overseer analiza →      │
│    "proceder" → ConsolidationOutcome             │
│  → aT (teoría aplicada/especificaciones) →       │
│    debate → Overseer analiza → "proceder" →      │
│    ConsolidationOutcome                          │
└──────────────────────────────────────────────────┘
                         ↓
┌──────────────────────────────────────────────────┐
│  EXEC — Builder construye                        │
│  Lee outcomes PRE + especificaciones, construye,  │
│  produce handback.md                             │
└──────────────────────────────────────────────────┘
                         ↓
┌──────────────────────────────────────────────────┐
│  POST — Overseer + Strategist cierran el ciclo   │
│  ConsolidationOutcome.C.md (crudo)               │
│  → Overseer.Analyze.md                            │
│  → CycleConsolidation.C.md (fusionado, viaja)    │
│  → feedback.md → loop                            │
└──────────────────────────────────────────────────┘
```

---

## Por Qué "ShitCode"

Porque el punto de partida no importa. Una iteración mediocre completada vale más que una perfecta abortada. El loop es el objetivo.

---

## Licencia

MIT. Cualquiera puede usarlo. Si haces millones con esto, al menos cómprame un café. O no. Nunca lo sabré.
