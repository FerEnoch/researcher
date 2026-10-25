# Run Request — Fase 2: Product Brief → Technical Discovery

Copiar, completar y pegar en el agente orquestador.
Protocolo completo: `protocols/02-tech-discovery/MASTER_PROTOCOL.md`.
Ejecutar solo con un Product Brief ya validado por un humano.

```text
Aplica el protocolo definido en protocols/02-tech-discovery/MASTER_PROTOCOL.md
al siguiente proyecto.

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>
- SPECIALIST_MODELS: <opcional>

INPUTS:
- PRODUCT_BRIEF: output/<slug>/brief/09_PRODUCT_BRIEF.md
- CLAIM_LEDGER_FINAL: output/<slug>/brief/CLAIM_LEDGER_FINAL.md
- OTHER_RESEARCH: <rutas opcionales>

CONTEXTO:
- DOMAIN: <rubro/producto>
- TARGET_MARKET: <mercado>
- PROJECT_TYPE: <web app / ecommerce / SaaS / portal / combinación>

RESTRICCIONES OPCIONALES:
- PREFERRED_STACK: <...>
- FORBIDDEN_STACK: <...>
- INFRA_CONSTRAINTS: <...>
- TEAM_CONSTRAINTS: <...>
- BUDGET_CONSTRAINTS: <...>
- TIME_CONSTRAINTS: <...>
- COMPLIANCE_CONSTRAINTS: <...>

INSTRUCCIÓN:
Ejecuta todas las fases de manera secuencial. Puedes lanzar subagentes
especializados cuando agreguen valor. Cualquier agente o subagente puede
preguntarme antes de continuar si detecta una ambigüedad material que pueda
cambiar una decisión técnica.

No generes backlog ni código de producción. No produzcas ADRs definitivos.
Al finalizar, identifica qué decisiones deberían pasar a ADR y entrega el
contexto necesario para trabajarlas con IA de forma ad hoc y especializada.
Finaliza con FINAL_TECHNICAL_DISCOVERY.md y TECH_DECISION_LEDGER_FINAL.md
en output/<slug>/discovery/.
```
