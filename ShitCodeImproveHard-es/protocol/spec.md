# ShitCodeImproveHard — Modo Single AI

## 0. Qué Es

Un framework de metacognición aplicado a la producción de software. No es una metodología de desarrollo. Es el proceso que produce metodologías de desarrollo.

Auto-referencial:
- **ShitCode** — punto de partida. El ciclo lo mejora.
- **Improve** — el pipeline cT→T→aT fuerza movimiento a través de capas de abstracción.
- **Hard** — los ciclos de retroalimentación cierran el loop y corrigen entre iteraciones.

Versión single-AI: un solo AI juega los tres roles (Overseer, Strategist, Builder) en secuencia dentro de la misma sesión.

---

## 1. Arquitectura

```
┌─────────────────────────────────┐
│  Overseer                       │  ← Analiza, evalúa, produce análisis
│  (ve el sistema completo)       │
└─────────────────────────────────┘
            │
            │ El mismo AI cambia de rol
            ▼
┌─────────────────────────────────┐
│  Strategist                     │  ← Propone teoría, debate, prepara specs
│  (trama el plan)                │
└─────────────────────────────────┘
            │
            │ Luego ejecuta directamente
            ▼
┌─────────────────────────────────┐
│  Builder                        │  ← Construye según especificaciones
│  (construye la cosa)            │
└─────────────────────────────────┘
```

### 1.1 Overseer

- Analiza patrones que el Strategist no puede ver
- Produce `overseer-analysis-{stage}.v#.md` post-debate
- Produce `Overseer.Analyze.md` al final del ciclo
- Mantiene `dir_overseer/journal.md`

### 1.2 Strategist

- Propone teoría (cT, T, aT)
- Debate contigo
- Espera "proceder" antes de producir ConsolidationOutcome
- Prepara especificaciones para el Builder

### 1.3 Builder

- Lee los outcomes PRE producidos por el mismo AI (ahora en rol Builder)
- Construye software según especificaciones
- Produce `handback.v#.md`
- No produce teoría ni análisis durante ejecución

### 1.4 El Puente (Tú)

Tú sigues siendo el puente entre roles:
- Decides cuándo el AI cambia de rol
- Corriges cuando un rol se sale de sus límites
- Dices "proceder" o "rechazar"
- Mantienes la memoria entre sesiones

---

## 2. Especificación del Pipeline

### 2.1 El Ciclo

```
CICLO:

  [PRE]  AI (Overseer + Strategist)

  cT{#}.v# (teoría artesanal)
    → debate-cT1.v# (Strategist + tú)
    → overseer-analysis_cT1.v# (Overseer)
    → tú: "proceder"
    → ConsolidationOutcome.cT1.v#.md (Strategist)

  → T{#}.v# (teoría)
    → debate-T1.v#
    → overseer-analysis_T1.v#
    → tú: "proceder"
    → ConsolidationOutcome.T1.v#.md

  → aT{#}.v# (teoría aplicada — specs)
    → debate-pre-aT1.v#
    → overseer-analysis_pre-aT1.v#
    → tú: "proceder"
    → ConsolidationOutcome.aT1.v#.md

  [EXEC]  AI (rol Builder)

  Lee outcomes PRE + especificaciones
  Construye el software
  Produce handback.v#.md

  [POST]  AI (Overseer + Strategist)

  ConsolidationOutcome.C.v#.md (crudo — suma de outcomes + handback)
  → Overseer.Analyze.md
  → CycleConsolidation.C.v#.md (fusionado — viaja al siguiente ciclo)
  → feedback.v#.md
  → Loop
```

### 2.2 Definición de Etapas

| Etapa | Fase | Input | Proceso | Output |
|-------|------|-------|---------|--------|
| **craftTheory (cT)** | PRE | Señal | Strategist propone teoría artesanal | `cT{#}.v#.md` |
| **Debate cT** | PRE | `cT{#}.v#.md` | Strategist + tú discuten | `debate-cT1.v#.md` |
| **Análisis cT** | PRE | `debate-cT1.v#.md` | Overseer analiza | `overseer-analysis_cT1.v#.md` |
| **Outcome cT** | PRE | cT + debate + análisis | Tú "proceder" → Strategist produce | `ConsolidationOutcome.cT1.v#.md` |
| **Theory (T)** | PRE | outcome cT | Strategist formaliza teoría | `T{#}.v#.md` |
| **Debate T** | PRE | `T{#}.v#.md` | Strategist + tú discuten | `debate-T1.v#.md` |
| **Análisis T** | PRE | `debate-T1.v#.md` | Overseer analiza | `overseer-analysis_T1.v#.md` |
| **Outcome T** | PRE | T + debate + análisis | Tú "proceder" → Strategist produce | `ConsolidationOutcome.T1.v#.md` |
| **appliedTheory (aT)** | PRE | outcome T | Strategist prepara specs | `pre-aT1.v#.md` |
| **Debate aT** | PRE | `pre-aT1.v#.md` | Strategist + tú discuten | `debate-pre-aT1.v#.md` |
| **Análisis aT** | PRE | `debate-pre-aT1.v#.md` | Overseer analiza | `overseer-analysis_pre-aT1.v#.md` |
| **Outcome aT** | PRE | aT + debate + análisis | Tú "proceder" → Strategist produce | `ConsolidationOutcome.aT1.v#.md` |
| **Build** | EXEC | outcomes PRE + specs | Builder construye | Código, `handback.v#.md` |
| **Suma (∑)** | POST | Todos outcomes + handback | AI consolida | `ConsolidationOutcome.C.v#.md` |
| **Análisis Overseer** | POST | Outcome del ciclo | Overseer analiza | `Overseer.Analyze.md` |
| **Consolidación Ciclo** | POST | Outcome + análisis Overseer | AI fusiona | `CycleConsolidation.C.v#.md` |
| **Retroalimentación** | POST | CycleConsolidation | AI identifica aprendizajes | `feedback.v#.md` |
| **Loop** | POST | Retroalimentación | Copiar al siguiente ciclo | Siguiente `dir_C.v00X/` |

### 2.3 Todos los Outcomes Son Válidos

| Outcome | Significado | Valor |
|---------|-------------|-------|
| Éxito | La teoría funcionó | Validación |
| Fracaso | No funcionó | Datos sobre qué no funciona |
| Bloqueo | No se pudo ejecutar | Revela cuello de botella |
| Descubrimiento | Algo inesperado | Nuevo patrón |
| Negociación | La ejecución se volvió conversación | Confianza > código |

---

## 3. Convención de Artefactos

### 3.1 Nombrado

```
{categoría}.{identificador}.v#.{ext}
```

Ejemplos: `cT1.v3.md`, `T1.v2.md`, `pre-aT1.v4.md`

### 3.2 Referencia de Archivos por Rol

#### PRE — Overseer + Strategist

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

#### EXEC — Builder

| Archivo | Dónde | Creador |
|---------|-------|---------|
| `build-aT1.v#.md` | `dir_3.2_build-aT1.v#/` | Builder |
| `handback.v#.md` | `dir_C.v00X/` | Builder |

#### POST — Overseer + Strategist

| Archivo | Dónde | Creador |
|---------|-------|---------|
| `post-aT1.v#.md` | `dir_3.3_post-aT1.v#/` | Strategist |
| `ConsolidationOutcome.C.v#.md` | `dir_C.v00X/` | Strategist |
| `Overseer.Analyze.md` | `dir_C.v00X/` | Overseer |
| `CycleConsolidation.C.v#.md` | `dir_C.v00X/` | Overseer |
| `feedback.v#.md` | `dir_C.v00X/` | Overseer |

### 3.3 Reglas Clave

1. **No hay outcome sin debate.** ConsolidationOutcome se produce solo después de "proceder"
2. **No hay análisis sin debate.** Overseer analiza solo después de que Strategist + tú discuten
3. **Outcome vive en el directorio de la etapa** (`dir_1_cT1.v#/`, `dir_2_T1.v#/`, `dir_3_aT1.v#/`)
4. **Builder solo construye.** Sin teoría, sin análisis durante ejecución
5. **Archivos raíz del ciclo** — handback, ConsolidationOutcome.C, Overseer.Analyze, CycleConsolidation, feedback viven en `dir_C.v00X/`

---

## 4. Estructura de Directorios

```
project-root/
├── protocol/                         ← Fuente de la metodología (copiar del repo)
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
├── dir_overseer/                     ← Espacio de trabajo del Overseer (entre ciclos)
│   ├── journal.md
│   ├── patterns.md
│   ├── overseer-analysis.history.md
│   ├── pipeline-status.md
│   ├── preferences.md
│   └── creation-log.md
│
├── dir_C.v001/                       ← Espacio de trabajo del ciclo
│   ├── ENTRY_C.v001.md
│   ├── HANDOFF_C.v001.md
│   │
│   ├── dir_1_cT1.v1/                 ← Etapa 1: Teoría Artesanal
│   │   ├── cT1.v1.md
│   │   ├── debate-cT1.v1.md
│   │   ├── overseer-analysis_cT1.v1.md
│   │   ├── ConsolidationOutcome.cT1.v1.md
│   │   └── ENTRY_cT1.v1.md
│   │
│   ├── dir_2_T1.v1/                  ← Etapa 2: Teoría
│   │   ├── T1.v1.md
│   │   ├── debate-T1.v1.md
│   │   ├── overseer-analysis_T1.v1.md
│   │   ├── ConsolidationOutcome.T1.v1.md
│   │   └── ENTRY_T1.v1.md
│   │
│   ├── dir_3_aT1.v1/                 ← Etapa 3: Teoría Aplicada
│   │   ├── dir_3.1_pre-aT1.v1/       ← PRE (especificaciones)
│   │   │   ├── pre-aT1.v1.md
│   │   │   ├── debate-pre-aT1.v1.md
│   │   │   └── overseer-analysis_pre-aT1.v1.md
│   │   ├── dir_3.2_build-aT1.v1/     ← EXEC (Builder)
│   │   │   └── build-aT1.v1.md
│   │   ├── dir_3.3_post-aT1.v1/      ← POST (análisis)
│   │   │   └── post-aT1.v1.md
│   │   ├── ConsolidationOutcome.aT1.v1.md
│   │   └── ENTRY_aT1.v1.md
│   │
│   ├── handback.v1.md
│   ├── ConsolidationOutcome.C.v1.md
│   ├── Overseer.Analyze.md
│   ├── CycleConsolidation.C.v1.md
│   └── feedback.v1.md
│
├── dir_C.v002/                       ← Siguiente ciclo (el historial crece aquí)
├── dir_C.v003/
└── README.md
```

---

## 5. Roles (Single AI)

### 5.1 Tú

- Inicias cada sesión
- Decides cuándo el AI cambia de rol
- Corriges cuando un rol se sale de sus límites
- Dices "proceder" o "rechazar"

### 5.2 AI — Rol Overseer

- Analiza patrones
- Produce overseer-analysis post-debate
- Produce Overseer.Analyze.md al final del ciclo
- Mantiene `dir_overseer/journal.md`

### 5.3 AI — Rol Strategist

- Propone teoría (cT, T, aT)
- Debate contigo
- Espera "proceder"
- Prepara especificaciones para Builder

### 5.4 AI — Rol Builder

- Construye software
- Produce handback
- No produce teoría ni análisis

### 5.5 Reglas

1. **No cambies de rol sin que tú lo indiques**
2. **En rol Overseer:** solo analiza, no propongas teoría
3. **En rol Strategist:** solo propón y debate, no analices como Overseer
4. **En rol Builder:** solo construye, no teorices ni analices
5. **Espera "proceder" antes de producir ConsolidationOutcome** (siempre)
6. **Pregunta cuando no entiendas** (siempre)

---

## 6. Protocolo de Comunicación

### AI → Tú

- Reporta qué rol está usando
- Pregunta cuando no entiende
- Advierte sobre patrones que ve
- No actúa sin autorización (excepto construir en EXEC)

### Tú → AI

- Provees contexto al inicio de cada sesión
- Indicas qué rol usar
- Corriges cuando el AI se sale de su rol
- Dices "proceder" o "rechazar"
- Cierras la sesión

### AI → Futuro AI (via Archivos)

El AI no persiste entre sesiones. Pero sus archivos sí:
- `HANDOFF_C.v#.md` — contexto para la siguiente sesión
- `CycleConsolidation.C.v#.md` — análisis fusionado que viaja al siguiente ciclo
- `dir_overseer/journal.md` — diario

---

## 7. Ciclo de Vida

### 7.1 Inicio

1. Clona/obtén los archivos de protocolo
2. Abre una sesión de AI
3. Di: `"Lee los archivos de ShitCodeImproveHard. Mi proyecto es @mi_proyecto."`
4. El AI lee el protocolo, pregunta lo necesario, comienza el Paso 1

### 7.2 Ejecución del Ciclo

```
[PRE]  AI (Overseer + Strategist)
1. cT → debate → Overseer analiza → "proceder" → ConsolidationOutcome
2. T → debate → Overseer analiza → "proceder" → ConsolidationOutcome
3. aT → debate → Overseer analiza → "proceder" → ConsolidationOutcome

[EXEC] AI (Builder)
4. Build → software → handback

[POST] AI (Overseer + Strategist)
5. Suma → ConsolidationOutcome.C.md
6. Overseer.Analyze.md
7. CycleConsolidation.C.md (fusionado)
8. Retroalimentación
9. Loop → siguiente ciclo
```

### 7.3 Criterios de Salida

1. PRE completo: 3 ConsolidationOutcomes producidos
2. EXEC completo: handback producido
3. POST completo: ConsolidationOutcome.C.md producido
4. Overseer.Analyze.md producido
5. CycleConsolidation.C.md producido
6. Retroalimentación producida
7. Tú decides loop o parar

---

## 8. El Principio Wise-Street

Esto no pretende ser original. Pretende ser necesario para quienes no tienen acceso a la academia pero tienen hambre de construir.

---

*ShitCodeImproveHard — Modo Single AI — Julio 2026*
