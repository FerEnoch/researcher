# Pipeline: Idea → Brief → Discovery → ADRs

Este documento conecta las dos Fases y el handoff posterior.
Es la vista de punta a punta; el detalle de cada fase vive en su protocolo.

## Mapa

```
Idea / rubro
  │  templates/run-lite.md  (express)  o  templates/run-research.md (completa)
  ▼
┌────────────────────────────────────────────────┐
│ LITE · protocols/00-lite/ (opcional)           │
│ Dominio → Benchmark → Argentina → Mini-ledger  │
│ → BRIEF 1 PÁGINA                               │
└────────────────────────────────────────────────┘
  │  LITE_BRIEF.md (+ LITE_LEDGER.md si hay claims regulatorios/MVP)
  │  ⚠️ decisión: ¿la apuesta justifica Fase 1 completa?
  ▼
┌────────────────────────────────────────────────┐
│ FASE 1 · protocols/01-benchmarking/            │
│ Intake → Domain map → Universo → Benchmark     │
│ → Argentina → Síntesis V1 + Ledger V1          │
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
qué hipótesis requieren validación real. Sin esa validación, no se avanza.

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

Si el objetivo es inspiración / benchmarking / exploración de ideas
para decidir si un proyecto vale la pena, el Lite alcanza:
deja benchmark + brief de 1 página sin pagar el costo del ciclo
adversarial ni del discovery técnico. Si el Lite muestra una apuesta
real, se escala a Fase 1 (brief completo) o directo a Fase 2 con el
Lite Brief como input provisorio (marcando lo no validado como
`UNRESOLVED`).
