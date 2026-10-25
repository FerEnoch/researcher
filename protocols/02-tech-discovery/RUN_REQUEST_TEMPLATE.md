# Run Request Template

Aplica el protocolo definido en `MASTER_PROTOCOL.md` al siguiente proyecto.

## MODELOS
- ORCHESTRATOR_MODEL: <modelA>
- ADVERSARIAL_MODEL: <modelB>
- SPECIALIST_MODELS: <opcional>

## INPUTS
- PRODUCT_BRIEF: <ruta>
- CLAIM_LEDGER_FINAL: <ruta>
- OTHER_RESEARCH: <rutas opcionales>

## CONTEXTO
- DOMAIN: <rubro/producto>
- TARGET_MARKET: <mercado>
- PROJECT_TYPE: <web app / ecommerce / SaaS / portal / combinación>

## RESTRICCIONES OPCIONALES
- PREFERRED_STACK: <...>
- FORBIDDEN_STACK: <...>
- INFRA_CONSTRAINTS: <...>
- TEAM_CONSTRAINTS: <...>
- BUDGET_CONSTRAINTS: <...>
- TIME_CONSTRAINTS: <...>
- COMPLIANCE_CONSTRAINTS: <...>

## INSTRUCCIÓN

Ejecuta todas las fases de manera secuencial.
Puedes lanzar subagentes especializados cuando agreguen valor.
Cualquier agente o subagente puede preguntarme antes de continuar si detecta una ambigüedad material que pueda cambiar una decisión técnica.

No generes backlog ni código de producción. No produzcas ADRs definitivos dentro de este protocolo. Al finalizar, identifica qué decisiones deberían pasar a ADR y entrega el contexto necesario para trabajarlas posteriormente con IA de forma ad hoc y especializada para este proyecto.
Finaliza con `FINAL_TECHNICAL_DISCOVERY.md` y `TECH_DECISION_LEDGER_FINAL.md`.
