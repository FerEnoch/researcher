# Artifact Contracts

Cada ejecución debe producir, como mínimo:

## `01_DOMAIN_MAP.md`

Debe contener:

- definición del rubro;
- actores;
- procesos;
- vocabulario;
- workflows;
- entidades conceptuales;
- pains conocidos;
- restricciones;
- preguntas abiertas.

## `02_COMPETITOR_UNIVERSE.md`

Separar en:

- Global Leaders
- Regional (pertinente al mercado elegido)
- Target Market (elegido por el usuario)
- Innovative Startups
- Relevant Open Source

Para cada producto: URL, mercado, segmento, razón de inclusión y evidencia básica.

## `03_GLOBAL_BENCHMARK.md`

Comparativa profunda, con matrices cuando sea útil y análisis cualitativo obligatorio.

## `04_TARGET_MARKET.md`

Debe explicitar el mercado/jurisdicciones elegidos en `market` de `run.yaml`
y diferenciar:

- hechos locales;
- particularidades operativas;
- diferencias frente al benchmark global;
- oportunidades locales;
- riesgos/regulación.

## `05_SYNTHESIS_V1.md`

Primera tesis del orquestador antes de la crítica adversarial.

## `CLAIM_LEDGER_V1.md`

Tabla mínima:

| Claim ID | Claim | Type | Sources | Evidence Strength | Geography | Confidence | Status |
|---|---|---|---|---|---|---|---|

## `06_ADVERSARIAL_REVIEW.md`

Cada objeción debe referenciar claims o secciones concretas y proponer qué evidencia faltaría.

## `07_DEFENSE.md`

Responder objeciones una por una.

## `CLAIM_LEDGER_FINAL.md`

Debe incorporar adjudicación final y consecuencia práctica para producto.

Campos recomendados:

| Claim ID | Final Claim | Evidence | Counterevidence | Geography | Confidence | Status | Product Implication |
|---|---|---|---|---|---|---|---|

## `08_PRODUCT_DISCOVERY.md`

Debe contener:

- actores/personas;
- JTBD;
- workflows;
- pains;
- oportunidades;
- table stakes;
- diferenciadores;
- anti-features;
- feature map;
- integraciones;
- entidades del dominio;
- hipótesis;
- incertidumbres.

## `09_PRODUCT_BRIEF.md`

Debe poder ser entregado a un equipo de producto/desarrollo sin releer todo el research.
Debe declarar mercado y jurisdicciones: se validan humanamente junto con el
brief y Fase 2 los hereda; un cambio exige revalidación humana previa.

## `FINAL_REPORT.md`

Estructura recomendada:

1. Executive Summary
2. Domain Overview
3. Global Market Findings
4. Target Market Findings
5. Competitive Patterns
6. Evidence-backed Opportunities
7. Product Strategy
8. MVP Recommendation
9. Technical Observations
10. Risks and Constraints
11. Open Questions
12. Unresolved Claims
13. Recommended Next Research
14. Source Index

## Regla de trazabilidad

Toda recomendación importante del Product Brief o Final Report debería poder rastrearse a uno o más `CLAIM_ID` del ledger final.
