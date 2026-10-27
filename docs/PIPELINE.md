# Pipeline: Idea → Brief → Discovery → ADRs

Este documento conecta las dos Fases y el handoff posterior.
Es la vista de punta a punta; el detalle de cada fase vive en su protocolo.
Objetivo (explorar/inspirar, contrastar idea, apoyar decisión) y etapa se
eligen por separado; sin una decisión material abierta, default Lite
equilibrado. El mercado siempre lo elige el usuario en runtime: `market`
en [run.yaml](../templates/run.yaml) es obligatorio y no tiene país/región
por defecto. Si falta o hay conflicto, preguntar antes de investigar.
Antes de cualquier artefacto aplicar el
[guard Git](../skills/researcher/references/output-guard.md) y resolver
[kit/permisos](../skills/researcher/references/kit.md).

## Mapa

```
Idea / rubro
  │  templates/run-lite.md  (express)  o  templates/run-research.md (completa)
  ▼
┌────────────────────────────────────────────────┐
│ LITE · protocols/00-lite/ (opcional)           │
│ Dominio → Benchmark → Mercado objetivo → Ledger │
│ → BRIEF 1 PÁGINA                               │
└────────────────────────────────────────────────┘
  │  LITE_BRIEF.md + cuatro notas (incluido ledger REGULATORIO/MVP)
  │  ⚠️ opciones para decidir qué validar; no MVP validado
  ▼
┌────────────────────────────────────────────────┐
│ FASE 1 · protocols/01-benchmarking/            │
│ Intake → Domain map → Universo → Benchmark     │
│ → Mercado objetivo → Síntesis V1 + Ledger V1    │
│ → Adversarial → Defensa → Adjudicación         │
│ → Discovery → PRODUCT BRIEF → FINAL REPORT     │
└────────────────────────────────────────────────┘
  │  09_PRODUCT_BRIEF.md + CLAIM_LEDGER_FINAL.md  (en output/<slug>/brief/)
  │  ⚠️ pausa humana: validar el brief antes de seguir
  ▼
┌────────────────────────────────────────────────┐
│ FASE 2 · protocols/02-tech-discovery/          │
│ Tech map → Dominio/datos → Drivers → Opciones  │
│ → Seguridad → Integraciones → Operaciones      │
│ → Hipótesis → Síntesis V1 + Ledger V1          │
│ → Adversarial → Defensa → Adjudicación         │
│ → FINAL TECHNICAL DISCOVERY                    │
└────────────────────────────────────────────────┘
  │  FINAL_TECHNICAL_DISCOVERY.md + TECH_DECISION_LEDGER_FINAL.md  (en output/<slug>/discovery/)
  │  + decisiones candidatas a ADR + unresolved + riesgos
  ▼
ADRs ad hoc del proyecto (fuera de este repo)
  → arquitectura detallada → planificación
```

## Handoffs

### Fase 1 → Humano

La Fase 1 termina en Product Brief, **no** en backlog. Antes de la Fase 2,
una persona valida: qué problema, para quién, workflows prioritarios,
qué hipótesis requieren validación real y el mercado/jurisdicciones.
Fase 2 hereda ese mercado en `market`; si falta o contradice un nuevo pedido,
consultar y exigir revalidación humana del brief antes de continuar, sin
override silencioso. Sin esa validación, no se avanza.

Global primero, investigación independiente del mercado elegido después;
los referentes regionales siguen ese alcance, no LatAm por defecto.
Nuevas notas locales: `LITE_TARGET_MARKET.md` y `04_TARGET_MARKET.md`.
Corridas antiguas no se migran ni renombran: al retomar, registrar las rutas
exactas conservadas en `run.yaml` (`notes`), sin modificar sus artefactos.

### Fase 2 → ADRs

La Fase 2 termina en Technical Discovery, **no** en ADRs ni en código.
El handoff a la etapa de ADRs incluye:

- decisiones candidatas a ADR,
- alternativas que aún merecen contraste,
- drivers y restricciones,
- unresolved relevantes,
- riesgos y triggers de re-arquitectura,
- evidencia disponible.

Los ADRs se trabajan con IA de forma especializada por proyecto
(prompts, especialistas y profundidad ad hoc). No existe
`ADR_PROTOCOL.md` genérico, por decisión de diseño.

## Qué NO sale de este pipeline

- Backlog detallado, user stories, story points, sprints.
- Estimaciones de horas ni tickets de implementación.
- Código de producción.
- ADRs definitivos.

## Cuándo usar el modo Lite

Lite entrega **opciones fundamentadas para decidir qué validar**, no un
go/no-go ni demanda demostrada. Compara 2–3 enfoques distintos con contexto
global y local independiente; inspiraciones adyacentes no son competidores
ni prueba local. No hay cuotas aditivas por geografía/startup/open source.

[Perfiles propuestos](../protocols/00-lite/LITE_PROTOCOL.md): exploratorio
4–6 consultas variadas / 2–3 lecturas; equilibrado DEFAULT 6–8 / 4–6;
orientado a decisión según incertidumbres críticas, quizá Fase 1. No son
estimaciones de tiempo/tokens. Un modelo por Lite, sin ciclo adversarial.
Priorizar lectura frente a inventarios redundantes. Parar por cobertura,
saturación de decisión o presupuesto agotado, registrando la diferencia.

Brief de una página + notas concisas y enlazadas. Snippets no son lectura;
la oferta anunciada no demuestra necesidad. Desconocidos regulatorios/MVP
solo bloquean/escalan si son indispensables para la decisión actual.
Registrar medición real o `null` / «no medido» en
[run.yaml](../templates/run.yaml); el piloto SELF-REPORTED no es baseline.

Escalar a Fase 1 si se necesita más profundidad. **Nunca pasar a Fase 2
con un Lite sin validar**: exige un Product Brief genuinamente validado por
una persona y los inputs de su protocolo, no un brief provisorio con
`UNRESOLVED` como sustituto de esa validación.
