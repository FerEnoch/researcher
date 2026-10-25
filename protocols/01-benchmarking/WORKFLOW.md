# Workflow

## Roles

### ORCHESTRATOR_MODEL

Responsable de:

- interpretar la solicitud;
- preguntar al usuario cuando existan ambigüedades materiales;
- dividir la investigación en subproblemas;
- lanzar subagentes secuencialmente;
- mantener el registro de claims;
- asegurar cobertura global y argentina;
- integrar resultados;
- actuar como adjudicador final salvo que el protocolo asigne esa fase al modelo adversarial.

### ADVERSARIAL_MODEL

Responsable de:

- buscar fallos, omisiones y sesgos;
- verificar claims;
- encontrar contraejemplos;
- detectar extrapolaciones inválidas;
- exigir respaldo;
- cuestionar prioridades de producto;
- defender contra-propuestas con evidencia.

Ambos modelos pueden asumir roles secundarios en fases distintas. El objetivo no es que uno “gane”, sino mejorar la calidad del resultado.

## Secuencia obligatoria

### Fase 0 — Intake y preguntas

El orquestador:

1. interpreta rubro, mercado y contexto;
2. identifica ambigüedades que puedan alterar el research;
3. si las hay, formula preguntas agrupadas al usuario;
4. si no son críticas, continúa dejando supuestos explícitos.

### Fase 1 — Domain Mapping

Construir un mapa inicial del dominio:

- actores;
- procesos;
- vocabulario;
- workflows;
- objetos/entidades;
- restricciones;
- pains;
- regulaciones;
- ciclos de negocio;
- posibles superficies digitales.

Salida: `01_DOMAIN_MAP.md`.

### Fase 2 — Global Benchmark Discovery

Buscar y clasificar referentes en:

1. líderes globales;
2. referentes regionales/LatAm;
3. startups/innovadores;
4. open source relevante.

No incluir sustitutos indirectos salvo petición expresa.

Salida: `02_COMPETITOR_UNIVERSE.md`.

### Fase 3 — Deep Benchmark

Seleccionar un conjunto representativo y analizar, cuando sea observable:

- propuesta de valor;
- target;
- información/arquitectura del producto;
- onboarding;
- workflows principales;
- features;
- UX/UI patterns;
- monetización;
- retención;
- upselling;
- modelo SaaS cuando corresponda;
- integraciones;
- arquitectura observable;
- stack observable/inferible;
- APIs;
- SEO;
- performance;
- accesibilidad;
- seguridad observable;
- modelo de datos inferible;
- multitenancy;
- mobile/PWA;
- analytics;
- automatización/IA;
- fortalezas;
- debilidades;
- patrones repetidos.

Salida: `03_GLOBAL_BENCHMARK.md`.

### Fase 4 — Argentina Research

Realizar una investigación argentina independiente y luego contrastarla con la global.

Salida: `04_ARGENTINA_MARKET.md`.

### Fase 5 — First Synthesis

El orquestador produce:

- patrones;
- table stakes;
- diferenciadores;
- oportunidades;
- riesgos;
- claims importantes;
- primeras hipótesis de producto.

Salidas:

- `05_SYNTHESIS_V1.md`
- `CLAIM_LEDGER_V1.md`

### Fase 6 — Adversarial Review

El modelo adversarial debe intentar refutar o degradar los hallazgos.

Debe buscar:

- claims sin respaldo;
- fuentes débiles;
- sesgo de selección;
- survivorship bias;
- generalización global→Argentina;
- features copiadas sin justificar;
- conclusiones basadas en popularidad;
- sobreinterpretación de tecnología observable;
- contradicciones entre competidores;
- omisiones del dominio;
- problemas regulatorios;
- prioridades de MVP discutibles.

Salida: `06_ADVERSARIAL_REVIEW.md`.

### Fase 7 — Defense / Rebuttal

El orquestador u otro subagente debe responder cada objeción con una de cuatro acciones:

- `DEFEND`
- `CONCEDE`
- `REFINE`
- `UNRESOLVED`

Debe aportar evidencia nueva cuando corresponda.

Salida: `07_DEFENSE.md`.

### Fase 8 — Adjudication

Revisar claim por claim aplicando `EVIDENCE_POLICY.md`.

Actualizar:

- estado;
- confianza;
- evidencia aceptada;
- evidencia rechazada;
- consecuencia para producto.

Salida: `CLAIM_LEDGER_FINAL.md`.

### Fase 9 — Product Discovery

Convertir evidencia adjudicada en:

- actores/personas operativas;
- jobs-to-be-done;
- journeys/workflows;
- necesidades;
- pains;
- oportunidades;
- feature map;
- table stakes;
- diferenciadores;
- anti-features;
- integraciones;
- entidades conceptuales del dominio;
- riesgos;
- hipótesis a validar;
- decisiones que no deben tomarse aún.

Salida: `08_PRODUCT_DISCOVERY.md`.

### Fase 10 — Product Brief

Construir un brief accionable para desarrollo:

- problema;
- contexto;
- usuarios;
- propuesta de valor;
- alcance;
- superficies de producto;
- workflows críticos;
- MVP;
- post-MVP;
- do-not-build-yet;
- integraciones;
- arquitectura funcional de alto nivel;
- modelo conceptual de datos;
- consideraciones no funcionales;
- riesgos;
- preguntas abiertas;
- experimentos/validaciones recomendadas;
- criterios para comenzar diseño técnico.

Salida: `09_PRODUCT_BRIEF.md`.

### Fase 11 — Final Report

Crear un documento ejecutivo y navegable que sintetice todo sin ocultar desacuerdos relevantes.

Salida: `FINAL_REPORT.md`.
