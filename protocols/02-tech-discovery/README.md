# Product Brief to Technical Discovery Protocol

Protocolo reutilizable para transformar un Product Brief validado y su evidencia asociada en un Technical Discovery auditable, adversarial y orientado a decisiones de arquitectura.

## Objetivo

Convertir decisiones de producto en una base técnica suficientemente sólida para iniciar la etapa de ADRs (Architecture Decision Records) y arquitectura detallada, evitando:
- arquitectura prematura,
- sobreingeniería,
- inferencias no respaldadas,
- decisiones de stack por preferencia personal,
- tickets de desarrollo antes de cerrar riesgos técnicos relevantes.

## Entrada mínima

- `PRODUCT_BRIEF.md`
- `CLAIM_LEDGER_FINAL.md`

Opcionales:
- research previo,
- restricciones de negocio,
- restricciones de infraestructura,
- stack preferido o prohibido,
- equipo disponible,
- presupuesto,
- horizonte temporal,
- requisitos regulatorios,
- prototipos UX/UI.

## Salida principal

- `FINAL_TECHNICAL_DISCOVERY.md`
- `TECH_DECISION_LEDGER.md`

## Uso recomendado

Ejecutar este protocolo después de validar el Product Brief y antes de producir ADRs concretos, arquitectura definitiva, backlog técnico o estimaciones de implementación.

## Siguiente etapa: ADRs asistidos por IA, sin protocolo genérico

El siguiente paso recomendado después de `FINAL_TECHNICAL_DISCOVERY.md` es elaborar los **ADRs (Architecture Decision Records)** necesarios para el proyecto.

Esa etapa también puede y debería estar **fuertemente asistida por IA**, incluyendo investigación, contraste de alternativas, crítica adversarial y redacción. Sin embargo, deliberadamente **no forma parte de este protocolo ni debe convertirse en un protocolo universal fijo**.

Los ADRs dependen demasiado del contexto concreto: arquitectura seleccionada, restricciones reales, stack, equipo, infraestructura, integración, seguridad, escala, presupuesto, deuda técnica y decisiones aún abiertas. Por eso, para cada proyecto se deben diseñar prompts, especialistas, preguntas, criterios de decisión y profundidad de análisis **ad hoc**.

Principio de transición:

`FINAL_TECHNICAL_DISCOVERY` → `ADRs asistidos por IA y especializados para ese proyecto` → `arquitectura detallada / planificación de implementación`

No crear un `ADR_PROTOCOL.md` genérico como continuación automática de este repositorio.

Ver `RUN_REQUEST_TEMPLATE.md`.
