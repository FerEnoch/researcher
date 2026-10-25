# LITE PROTOCOL — Benchmark express → brief de 1 página

## 0. Propósito

Producir en poco tiempo una base suficiente para decidir si una idea
merece una Fase 1 completa: mapa de dominio compacto, benchmark con
topes, flash Argentina, mini-ledger y brief de 1 página.

No produce un Product Brief validable para arquitectura. Todo lo que
afirma y no pudo verificar queda marcado `UNRESOLVED` en el brief.

## 1. Variables de ejecución

El protocolo usa un único modelo:

- `ORCHESTRATOR_MODEL`

No hay `ADVERSARIAL_MODEL`. La ausencia de revisión adversarial es una
limitación declarada, no un detalle: el brief final incluye la sección
"Qué NO valida este Lite".

## 2. Regla de saturación (cuándo parar de buscar)

Topes duros por categoría de referente:

- Global Leaders: 2–4.
- LatAm / Regional: 2–3.
- Argentina: 2–4.
- Startups innovadoras: 1–3.
- Open source relevante: 0–2 (si no hay, se declara, no se rellena).

Regla de parada: si dos rondas de búsqueda consecutivas no agregan
patrones nuevos (features, modelos de negocio, integraciones, pricing),
se cierra el universo aunque no se haya llegado al tope. Llegar al tope
sin saturar también cierra: el Lite no persigue exhaustividad.

Cada referente se registra con: nombre, URL, mercado, segmento, razón de
inclusión y al menos una fuente primaria (sitio oficial, docs, pricing,
app store, organismo público). Sin fuente primaria, el referente no entra.

## 3. Ledger mínimo (qué va al ledger y qué no)

Al `LITE_LEDGER.md` van **únicamente** dos tipos de claim:

1. **Regulatorios**: colegiaturas, habilitaciones, facturación/ARCA,
   protección de datos, normativa sectorial. Si un regulatorio no se pudo
   verificar, queda `UNRESOLVED` y pasa al brief como pregunta bloqueante.
2. **De MVP**: afirmaciones que sostienen el corte del MVP propuesto
   (table stakes, diferenciador, anti-feature). Cada item del MVP
   referencia al menos un claim del ledger o queda marcado `UNRESOLVED`.

Todo lo demás (curiosidades de mercado, features de nicho, tecnicismos
observados) vive como notas en `LITE_BENCHMARK.md`, sin ledger.

## 3b. Regla de lectura (qué cuenta como fuente)

Un snippet del buscador **no** es haber leído la fuente: solo prueba que
la fuente existe y de qué dominio viene. Por eso:

- Un claim `REGULATORIO` solo llega a `SUPPORTED` si se leyó la fuente
  primaria (fetch a norma, organismo o colegio). Con solo snippet,
  el techo es `PARTIALLY_SUPPORTED`.
- Un claim de `MVP` puede ser `SUPPORTED` con snippet **únicamente** si
  la fuente es el sitio oficial del producto y lo afirmado es oferta
  pública (features, pricing). Todo lo demás, techo `PARTIALLY`.
- Cada fetch suma costo: reservarlos para regulatorios y el corte del
  MVP. El resto se cierra con snippets + `UNRESOLVED` donde corresponda.

## 4. Fases

### L0 — Intake (máximo 1 ronda de preguntas)

Interpretar rubro, mercado y contexto. Si hay ambigüedades materiales
(usuarios, modelo de negocio, alcance), hacer **una sola ronda de hasta
3 preguntas**. Lo no preguntado se resuelve con supuestos explícitos
anotados en `LITE_DOMAIN.md`.

### L1 — Dominio compacto

Actores, vocabulario mínimo, 3–5 workflows típicos, entidades
conceptuales, pains visibles, restricciones obvias. Una página como
máximo. Salida: `LITE_DOMAIN.md`.

### L2 — Benchmark con topes

Armar el universo respetando la regla de saturación (§2). Para cada
referente seleccionado: propuesta de valor, segmento, workflows
principales observables, 3–5 features troncales, monetización visible,
integraciones nombradas, señales UX/mobile. Sin inferir arquitectura
oculta: lo no observable se marca como tal. Salida: `LITE_BENCHMARK.md`.

### L3 — Argentina flash

Investigación local independiente y contraste con lo global: actores
locales, WhatsApp y canales, Mercado Pago y pagos, facturación/ARCA,
regulación sectorial, logística, costos y expectativas comerciales.
Lista de diferencias concretas, no traducción. Salida: `LITE_ARGENTINA.md`.

### L4 — Mini-ledger + Brief 1 página

Consolidar `LITE_LEDGER.md` según §3 (tabla: Claim ID, claim, tipo
`REGULATORIO`/`MVP`, fuentes, confianza, estado, implicancia).
Después escribir `LITE_BRIEF.md` con estas secciones fijas, una página:

1. Problema y contexto (2–3 líneas).
2. Usuarios (quién paga, quién usa, quién opera).
3. Propuesta de valor (1–2 líneas).
4. Superficies tentativas (web, backoffice, portal, app…).
5. Table stakes (máx 5) y diferenciadores (máx 3).
6. Anti-features (máx 3): qué vimos afuera y no haríamos.
7. Corte de MVP (qué entra y por qué, con referencia al ledger).
8. No-construir todavía.
9. Integraciones clave.
10. Riesgos top 3.
11. Qué NO valida este Lite + preguntas abiertas (`UNRESOLVED`).

## 5. Prohibido en Lite

- Ciclo adversarial (crítica, defensa, adjudicación).
- Claim ledger completo.
- Technical discovery, backlog, estimaciones, código.
- Completar huecos de evidencia con prosa confiada.

## 6. Handoff / escala

El Lite escala a Fase 1 cuando: hay decisión tentativa de construir, un
`UNRESOLVED` bloquea el corte del MVP, o el riesgo regulatorio exige
adjudicación. Lo producido se reutiliza tal cual: `LITE_DOMAIN.md`,
`LITE_BENCHMARK.md` y `LITE_ARGENTINA.md` alimentan las Fases 1–4 de la
Fase 1, y `LITE_LEDGER.md` se expande al formato completo.

Medir cada corrida Lite en `run.yaml` (`lite_measured`: búsquedas,
tiempo aproximado, artefactos): es el dato que calibra el costo del modo
express a lo largo de los proyectos.
