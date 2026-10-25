# Pipeline: Idea → Brief → Discovery → ADRs

Este documento conecta las dos Fases y el handoff posterior.
Es la vista de punta a punta; el detalle de cada fase vive en su protocolo.

## Mapa

```
Idea / rubro
  │  templates/run-research.md
  ▼
┌────────────────────────────────────────────────┐
│ FASE 1 · protocols/01-benchmarking/            │
│ Intake → Domain map → Universo → Benchmark     │
│ → Argentina → Síntesis V1 + Ledger V1          │
│ → Adversarial → Defensa → Adjudicación         │
│ → Discovery → PRODUCT BRIEF → FINAL REPORT     │
└────────────────────────────────────────────────┘
  │  09_PRODUCT_BRIEF.md + CLAIM_LEDGER_FINAL.md
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
  │  FINAL_TECHNICAL_DISCOVERY.md + TECH_DECISION_LEDGER_FINAL.md
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

## Cuándo usar solo la Fase 1

Si el objetivo es inspiración / benchmarking / exploración de ideas
para decidir si un proyecto vale la pena, la Fase 1 sola alcanza:
deja benchmark + brief + preguntas abiertas sin pagar el costo
de un discovery técnico completo.
