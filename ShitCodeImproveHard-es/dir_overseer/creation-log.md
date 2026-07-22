# Registro de Creación

*El Overseer registra cuándo se crea cada directorio y archivo clave. Las marcas de tiempo son aproximadas.*

---

## {fecha}

| Ruta | Tipo |
|------|------|
| `dir_C.v{ciclo}/` | dir de ciclo |
| `dir_C.v{ciclo}/dir_1_cT1.v{versión}/` | dir de etapa |
| `dir_C.v{ciclo}/dir_2_T1.v{versión}/` | dir de etapa |
| `dir_C.v{ciclo}/dir_3_aT1.v{versión}/` | dir de etapa |
| `dir_C.v{ciclo}/dir_3_aT1.v{versión}/dir_3.1_pre-aT1.v{versión}/` | sub-etapa |
| `dir_C.v{ciclo}/dir_3_aT1.v{versión}/dir_3.2_build-aT1.v{versión}/` | sub-etapa |
| `dir_C.v{ciclo}/dir_3_aT1.v{versión}/dir_3.3_post-aT1.v{versión}/` | sub-etapa |
| `dir_C.v{ciclo}/ENTRY_C.v{versión}.md` | entrada de ciclo |
| `dir_C.v{ciclo}/HANDOFF_C.v{versión}.md` | handoff de ciclo |
| `dir_C.v{ciclo}/dir_1_cT1.v{versión}/cT{número}.v{versión}.md` | teoría artesanal |
| `dir_C.v{ciclo}/dir_1_cT1.v{versión}/debate-cT{número}.v{versión}.md` | debate |
| `dir_C.v{ciclo}/dir_1_cT1.v{versión}/overseer-analysis_cT{número}.v{versión}.md` | análisis |
| `dir_C.v{ciclo}/dir_1_cT1.v{versión}/ConsolidationOutcome.cT{número}.v{versión}.md` | outcome |
| `dir_C.v{ciclo}/handback.v{versión}.md` | handback |
| `dir_C.v{ciclo}/ConsolidationOutcome.C.v{versión}.md` | outcome de ciclo |
| `dir_C.v{ciclo}/Overseer.Analyze.md` | análisis de ciclo |
| `dir_C.v{ciclo}/CycleConsolidation.C.v{versión}.md` | consolidación de ciclo |
| `dir_C.v{ciclo}/feedback.v{versión}.md` | retroalimentación |

---

## Línea de Tiempo

```
{fecha} — C.v{ciclo} iniciado
{fecha} — cT{versión} creado
{fecha} — debate completado
{fecha} — ConsolidationOutcome.cT producido
...continuar por ciclo...
```
