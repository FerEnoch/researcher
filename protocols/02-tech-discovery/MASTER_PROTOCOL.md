# MASTER PROTOCOL — Product Brief to Technical Discovery

## 0. Propósito

Este protocolo transforma un Product Brief validado en un Technical Discovery auditable y adversarial para proyectos web fullstack.

No produce directamente ADRs definitivos, arquitectura final ni backlog de implementación. Su objetivo es reducir incertidumbre técnica y documentar decisiones, alternativas, riesgos y preguntas abiertas antes de entrar en una etapa de ADRs y arquitectura detallada.

## 1. Variables de ejecución

El protocolo NO asume modelos fijos.

La request debe declarar:
- `ORCHESTRATOR_MODEL`
- `ADVERSARIAL_MODEL`

Opcionalmente:
- `SPECIALIST_MODELS`
- `DOMAIN`
- `TARGET_MARKET`
- `PREFERRED_STACK`
- `FORBIDDEN_STACK`
- `INFRA_CONSTRAINTS`
- `TEAM_CONSTRAINTS`
- `BUDGET_CONSTRAINTS`
- `TIME_CONSTRAINTS`

El `ORCHESTRATOR_MODEL` dirige el proceso y lanza subagentes secuencialmente.

## 2. Regla de interacción con el usuario

Cualquier modelo o subagente puede interrumpir el protocolo y hacer preguntas al usuario antes de continuar cuando detecte una ambigüedad material que pueda cambiar una decisión técnica.

Debe preguntar solo si la incertidumbre puede alterar significativamente:
- arquitectura,
- seguridad,
- costos,
- escalabilidad,
- cumplimiento,
- UX crítica,
- integraciones,
- alcance técnico.

Si la duda no es material, debe continuar y documentar la suposición.

## 3. Entradas obligatorias

Leer y usar como fuente primaria:
1. `PRODUCT_BRIEF.md`
2. `CLAIM_LEDGER_FINAL.md`

No reinterpretar el Product Brief como especificación técnica cerrada.

Toda decisión técnica debe poder rastrearse hasta:
- una necesidad de producto,
- una restricción,
- un riesgo,
- un requisito no funcional,
- o una decisión explícita del usuario.

## 4. Principios

### 4.1 No arquitectura por moda
No elegir tecnologías por popularidad o preferencia sin justificar su adecuación.

### 4.2 Separar necesidad de solución
Distinguir:
- problema,
- requisito,
- restricción,
- alternativa,
- decisión.

### 4.3 Preferir reversibilidad
Cuando dos alternativas sean razonables, favorecer la que preserve opcionalidad y reduzca lock-in temprano.

### 4.4 Evitar sobreingeniería
No diseñar para escalas, integraciones o escenarios sin evidencia razonable.

### 4.5 Seguridad por diseño
Las decisiones de autenticación, autorización, datos sensibles, auditoría y exposición pública deben tratarse como first-class concerns.

### 4.6 Operabilidad desde el inicio
Considerar despliegue, observabilidad, backups, migraciones, recuperación, soporte y mantenimiento.

### 4.7 Evidencia y confianza
Toda inferencia técnica debe tener:
- fuente o racional,
- nivel de confianza,
- impacto si resulta incorrecta.

## 5. Proceso secuencial obligatorio

El ORCHESTRATOR_MODEL debe ejecutar las fases en orden.

### Fase 1 — Product-to-Technical Translation
Objetivo: traducir el Product Brief a requisitos técnicos neutrales.

Crear:
- `01_PRODUCT_TO_TECH_MAP.md`

Debe incluir:
- actores,
- journeys críticos,
- capacidades de producto,
- datos manipulados,
- integraciones,
- requisitos de disponibilidad,
- requisitos de privacidad,
- requisitos de auditoría,
- requisitos de performance,
- requisitos de accesibilidad,
- requisitos SEO si aplica,
- superficies: web pública, backoffice, portal, ecommerce, API, mobile/PWA, etc.

No elegir todavía stack.

### Fase 2 — Domain & Data Discovery
Crear:
- `02_DOMAIN_AND_DATA_MODEL.md`

Debe identificar:
- entidades de dominio,
- relaciones,
- ownership,
- lifecycle,
- invariantes,
- estados,
- eventos importantes,
- datos derivados,
- datos sensibles,
- retención,
- necesidades de búsqueda,
- volumen y crecimiento estimados.

Separar claramente:
- modelo conceptual,
- hipótesis,
- decisiones pendientes.

### Fase 3 — Architecture Drivers
Crear:
- `03_ARCHITECTURE_DRIVERS.md`

Derivar drivers reales:
- escala,
- concurrencia,
- disponibilidad,
- latencia,
- consistencia,
- seguridad,
- cumplimiento,
- extensibilidad,
- multitenancy,
- internacionalización,
- offline/PWA,
- integraciones,
- costos,
- capacidad del equipo,
- time-to-market.

Para cada driver indicar:
- evidencia,
- severidad,
- probabilidad,
- impacto arquitectónico.

### Fase 4 — Technical Options Exploration
Crear:
- `04_TECHNICAL_OPTIONS.md`

Evaluar alternativas para:
- frontend,
- backend,
- base de datos,
- storage,
- autenticación,
- autorización,
- búsqueda,
- colas/eventos,
- cache,
- realtime,
- integraciones,
- emails/notificaciones,
- pagos si aplica,
- observabilidad,
- despliegue,
- CI/CD,
- testing,
- analytics,
- CMS si aplica.

No asumir que todos los componentes son necesarios.

Para cada categoría:
- necesidad,
- opción A/B/C,
- ventajas,
- desventajas,
- complejidad,
- lock-in,
- costo,
- madurez,
- fit con el proyecto,
- recomendación provisional.

### Fase 5 — Security, Privacy & Compliance Discovery
Crear:
- `05_SECURITY_PRIVACY_COMPLIANCE.md`

Analizar según corresponda:
- autenticación,
- autorización,
- RBAC/ABAC,
- aislamiento tenant,
- secretos,
- cifrado,
- sesiones,
- rate limiting,
- validación,
- uploads,
- SSRF/XSS/CSRF/SQLi,
- auditoría,
- PII,
- backup,
- recovery,
- logging seguro,
- dependencias,
- supply chain,
- regulación aplicable.

Si el mercado incluye Argentina, contemplar requisitos locales cuando correspondan.

### Fase 6 — Integration Discovery
Crear:
- `06_INTEGRATIONS.md`

Clasificar:
- esenciales,
- probables,
- opcionales,
- futuras.

Para cada integración:
- propósito,
- proveedor candidato,
- API disponible,
- autenticación,
- límites,
- webhooks,
- retry/idempotencia,
- riesgos,
- fallback,
- costo,
- dependencia crítica.

### Fase 7 — Delivery & Operations Discovery
Crear:
- `07_DELIVERY_AND_OPERATIONS.md`

Cubrir:
- ambientes,
- infraestructura,
- IaC si corresponde,
- CI/CD,
- migraciones,
- feature flags,
- observabilidad,
- alertas,
- backups,
- restore tests,
- rollback,
- logs,
- métricas,
- trazas,
- runbooks,
- costos operativos.

### Fase 8 — Preliminary Architecture Hypotheses
Crear:
- `08_ARCHITECTURE_HYPOTHESES.md`

Proponer 2-3 arquitecturas plausibles como hipótesis, por ejemplo:
- monolito modular,
- monolito + workers,
- servicios separados,
- serverless/event-driven,
según el caso.

Para cada una:
- diagrama textual,
- límites,
- fortalezas,
- debilidades,
- riesgos,
- trigger para evolucionar.

No declarar una arquitectura definitiva todavía.

### Fase 9 — Technical Synthesis V1
Crear:
- `09_TECHNICAL_SYNTHESIS_V1.md`
- `TECH_DECISION_LEDGER_V1.md`

El ledger debe registrar cada decisión candidata con:
- ID,
- decisión,
- alternativas,
- evidencia,
- racional,
- nivel de confianza,
- reversibilidad,
- costo de error,
- dependencias,
- estado.

Estados sugeridos:
- ACCEPT
- ACCEPT_WITH_CAVEAT
- DEFER
- REJECT
- UNRESOLVED

### Fase 10 — Adversarial Review
El ADVERSARIAL_MODEL recibe toda la evidencia previa y produce:
- `10_ADVERSARIAL_REVIEW.md`

Debe intentar falsar:
- supuestos,
- decisiones,
- sizing,
- arquitectura,
- stack,
- seguridad,
- costos,
- escalabilidad,
- integraciones,
- dependencias,
- modelo de datos.

Debe buscar especialmente:
- overengineering,
- underengineering,
- vendor lock-in,
- single points of failure,
- riesgos de seguridad,
- costos ocultos,
- incompatibilidades,
- contradicciones con Product Brief.

No se aceptan críticas genéricas.
Cada crítica debe indicar:
- claim/decision atacada,
- evidencia o argumento,
- severidad,
- cambio recomendado.

### Fase 11 — Defense & Revision
El ORCHESTRATOR_MODEL debe responder con:
- `11_DEFENSE_AND_REVISION.md`

Para cada crítica:
- aceptar,
- aceptar parcialmente,
- rechazar,
- dejar unresolved.

Debe modificar decisiones cuando la crítica sea superior.
No defender por consistencia narrativa.

### Fase 12 — Final Adjudication
El ADVERSARIAL_MODEL o un subagente árbitro designado debe producir:
- `TECH_DECISION_LEDGER_FINAL.md`

Resolver por:
1. evidencia,
2. fit con producto,
3. simplicidad,
4. reversibilidad,
5. costo,
6. riesgo,
7. operabilidad.

No resolver por autoridad retórica del modelo.

### Fase 13 — Final Technical Discovery
El ORCHESTRATOR_MODEL produce:
- `FINAL_TECHNICAL_DISCOVERY.md`

Debe contener:
1. Executive summary
2. Product-to-tech translation
3. Domain model summary
4. Architecture drivers
5. Recommended technical direction
6. Recommended stack with rationale
7. Security model
8. Integration strategy
9. Data strategy
10. Deployment & operations strategy
11. Testing strategy
12. Observability strategy
13. Cost considerations
14. Scalability assumptions
15. Architecture hypothesis selected
16. Deferred decisions
17. Explicit non-goals
18. Technical risks
19. Unknowns / questions
20. Triggers for re-architecture
21. Readiness assessment

## 6. Salida prohibida

No generar como salida final:
- backlog detallado,
- user stories,
- story points,
- sprint planning,
- estimaciones de horas,
- tickets de implementación,
- código de producción.

Puede señalar futuros workstreams, pero sin convertirlos en plan de ejecución.

### Frontera explícita del protocolo

La salida de este protocolo debe quedar preparada para el **siguiente paso: creación de ADRs (Architecture Decision Records)**. Esa etapa será asistida por IA, pero **no debe ejecutarse mediante un protocolo genérico fijo**.

Para cada proyecto concreto, los ADRs deben trabajarse con una estrategia ad hoc: prompts específicos, modelos o subagentes apropiados, investigación focalizada, comparación de opciones, revisión adversarial y criterios de decisión ajustados al contexto técnico real.

No asumir que existe ni generar automáticamente un `ADR_PROTOCOL.md` universal. El orquestador debe detenerse al completar el Technical Discovery y entregar los unresolved, decisiones candidatas y riesgos que servirán como insumo para ese trabajo especializado.

## 7. Regla de trazabilidad

Toda recomendación final debe poder rastrearse así:

Product Need / Constraint
→ Technical Requirement
→ Architecture Driver
→ Evaluated Alternatives
→ Decision Ledger
→ Final Recommendation

## 8. Criterio de finalización

El Technical Discovery está listo cuando:
- no existen contradicciones críticas no documentadas,
- las decisiones irreversibles tienen evidencia suficiente,
- los riesgos altos tienen mitigación o trigger,
- los unresolved están explícitos,
- el Product Brief sigue siendo satisfecho,
- la arquitectura recomendada es suficientemente concreta para iniciar la elaboración especializada de ADRs asistidos por IA;
- están identificadas las decisiones que merecen ADR y los unresolved que deben resolverse durante esa etapa;
- no se intentó imponer un protocolo genérico de ADRs ni producir ADRs definitivos prematuramente.
