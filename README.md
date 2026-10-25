# Researcher

Kit de research pre-dev para proyectos internos: antes de escribir código,
investigamos el rubro, hacemos benchmarking, definimos el producto
y preparamos el terreno técnico. Todo con evidencia, revisión adversarial
y artefactos versionados.

## El pipeline

```
┌─────────────────────────┐     ┌─────────────────────────┐     ┌──────────────────┐
│  FASE 1: Benchmarking   │     │ FASE 2: Tech Discovery  │     │ ADRs ad hoc      │
│  y Domain Research      │────▶│                         │────▶│ (por proyecto)   │
│  protocols/01-...       │brief│ protocols/02-...       │final│ fuera de este    │
│                         │     │                         │tech │ repo / en cada   │
│  Idea → Product Brief   │     │ Brief → Discovery       │disc │ proyecto         │
└─────────────────────────┘     └─────────────────────────┘     └──────────────────┘
```

- **Fase 1** (`protocols/01-benchmarking/`): entiende el dominio, compara
  referentes globales / regionales / argentinos / startups / open source,
  y termina en un **Product Brief** accionable. Con ciclo adversarial
  obligatorio (tesis → crítica → defensa → adjudicación).
- **Modo Lite** (`protocols/00-lite/`): versión express de la Fase 1 para
  exploración e inspiración rápida. Sin adversarial, ledger mínimo y brief
  de 1 página. Si el Lite justifica la apuesta, se escala a Fase 1 o Fase 2.
- **Fase 2** (`protocols/02-tech-discovery/`): convierte un Product Brief
  validado en un **Technical Discovery** auditable (drivers, opciones,
  seguridad, integraciones, operaciones, hipótesis de arquitectura).
  También con revisión adversarial. No genera backlog ni código.
- **ADRs**: deliberadamente fuera de este repo. Se diseñan ad hoc por
  proyecto, asistidos por IA, a partir del Technical Discovery final.

Detalle del flujo punta a punta: [`docs/PIPELINE.md`](docs/PIPELINE.md).

## Estructura

```text
researcher/
├── README.md                        ← este archivo
├── protocols/
│   ├── 00-lite/                     ← Modo Lite: benchmark express → brief 1 página
│   │   ├── README.md
│   │   ├── LITE_PROTOCOL.md         ← prompt principal (pegar en el agente)
│   │   └── RUN_REQUEST_TEMPLATE.md  ← plantilla de invocación
│   ├── 01-benchmarking/             ← Fase 1: dominio + benchmarking → Product Brief
│   │   ├── README.md
│   │   ├── MASTER_PROTOCOL.md       ← prompt principal (pegar en el orquestador)
│   │   ├── WORKFLOW.md              ← fases y roles
│   │   ├── EVIDENCE_POLICY.md       ← fuentes, claims, adjudicación
│   │   ├── ARTIFACT_CONTRACTS.md    ← artefactos exigidos por corrida
│   │   ├── REPO_STRUCTURE.md        ← convención original (ver nota abajo)
│   │   └── RUN_REQUEST_TEMPLATE.md  ← plantilla de invocación
│   └── 02-tech-discovery/           ← Fase 2: Brief → Technical Discovery
│       ├── README.md
│       ├── MASTER_PROTOCOL.md
│       ├── WORKFLOW.md
│       ├── DECISION_POLICY.md       ← jerarquía y tipos de decisión
│       ├── QUALITY_GATE.md          ← checklist de cierre
│       ├── ARTIFACT_CONTRACTS.md
│       ├── REPO_STRUCTURE.md
│       └── RUN_REQUEST_TEMPLATE.md
├── templates/
│   ├── run-lite.md                  ← invocación Lite (copiar/pegar)
│   ├── run-research.md              ← invocación Fase 1 (copiar/pegar)
│   ├── run-discovery.md             ← invocación Fase 2 (copiar/pegar)
│   └── run.yaml                     ← metadatos de corrida (ejemplo)
├── output/                          ← corridas LOCALES, no versionadas (ver output/README.md)
│   ├── README.md                    ← convención de carpetas por etapa
│   └── <slug>/                      ← brief/ · discovery/ · lite/ por investigación
└── docs/
    └── PIPELINE.md                  ← cómo encadenar Lite → Fase 1 → Fase 2 → ADRs
```

> Nota: los `REPO_STRUCTURE.md` dentro de cada protocolo describen la
> convención original de ese protocolo aislado. La convención vigente
> para este repo unificado es: cada investigación vive en
> `output/<slug>/` con subcarpetas por etapa (`brief/`, `discovery/`,
> `lite/`). Ver [`output/README.md`](output/README.md).

## Uso rápido

### 0. Modo Lite — Exploración express (recomendado para empezar)

```text
Aplica el protocolo protocols/00-lite/LITE_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>

MODELO:
- ORCHESTRATOR_MODEL: <modelo A>

MERCADO OBJETIVO INICIAL:
Argentina

CONTEXTO DEL PROYECTO:
<cliente, restricciones, ideas iniciales, etc.>
```

Plantilla lista para copiar: [`templates/run-lite.md`](templates/run-lite.md).
Sin ciclo adversarial, ledger mínimo (solo regulatorios y MVP) y brief de
1 página. Si el Lite muestra una apuesta real, se escala a Fase 1 o Fase 2.

## Uso rápido

### 1. Fase 1 — Investigar un rubro

```text
Aplica el protocolo protocols/01-benchmarking/MASTER_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>

MERCADO OBJETIVO INICIAL:
Argentina

CONTEXTO DEL PROYECTO:
<cliente, restricciones, ideas iniciales, stack preferido, etc.>
```

Plantilla lista para copiar: [`templates/run-research.md`](templates/run-research.md).
Los modelos son parámetros: el protocolo no depende de proveedores concretos.

Salida: `output/<slug>/brief/` con domain map, benchmark global, mercado
argentino, síntesis, claim ledger, ciclo adversarial, product discovery,
**`09_PRODUCT_BRIEF.md`** y **`FINAL_REPORT.md`**.

### 2. Fase 2 — Del Brief al Technical Discovery

Cuando el Product Brief esté validado por un humano:

```text
Aplica el protocolo protocols/02-tech-discovery/MASTER_PROTOCOL.md.

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>

INPUTS:
- PRODUCT_BRIEF: output/<slug>/brief/09_PRODUCT_BRIEF.md
- CLAIM_LEDGER_FINAL: output/<slug>/brief/CLAIM_LEDGER_FINAL.md
```

Plantilla lista para copiar: [`templates/run-discovery.md`](templates/run-discovery.md).

Salida: `output/<slug>/discovery/` con
**`FINAL_TECHNICAL_DISCOVERY.md`** y **`TECH_DECISION_LEDGER_FINAL.md`**.

### 3. Después: ADRs del proyecto

Con el Technical Discovery en mano, diseñar los ADRs ad hoc para ese
proyecto (prompts, especialistas y profundidad según el caso).
No hay protocolo genérico de ADRs en este repo, por decisión explícita
del diseño original.

## Reglas del juego

1. **Evidencia o `UNRESOLVED`.** Todo claim importante se rastrea a
   fuentes, se marca como inferencia, o queda `UNRESOLVED`. Sin relleno
   con prosa confiada.
2. **Adversarial obligatorio.** Tesis → crítica → defensa → adjudicación.
   Las discrepancias se resuelven por evidencia, nunca por retórica.
3. **Global primero, Argentina después.** La investigación local es
   independiente, nunca una traducción (WhatsApp, Mercado Pago, ARCA,
   regulación, logística, costos).
4. **No copiar features.** Cada feature candidata responde: ¿qué problema
   resuelve, para quién, con qué frecuencia, con qué costo operativo?
   Explícitamente: table stakes, diferenciadores y **anti-features**.
5. **Secuencial, local.** Una investigación = una carpeta en
   `output/<slug>/` (no versionada), con subcarpetas por etapa.
   Sin borrar desacuerdos: el historial adversarial se conserva en disco.
6. **Los protocolos no generan código.** Fase 1 termina en Product Brief,
   Fase 2 en Technical Discovery. Sin backlog, sin estimaciones, sin tickets.

## Convenciones

- Una corrida = `output/<slug>/` + `run.yaml` (ver
  [`templates/run.yaml`](templates/run.yaml)). Los outputs no se versionan;
  lo que se commitea son mejoras al kit (protocolos, templates, docs).
- Commits del kit en español o inglés, prefijados por etapa, ej:
  `protocol(lite): add saturation rule`,
  `templates: add run-lite request`.
- `UNRESOLVED` valiosos → backlog de preguntas de validación con usuarios,
  no se esconden.

## Para quién es esto

Equipos internos que inician un producto web fullstack y quieren una base
de decisiones trazable antes de diseñar arquitectura o estimar. Si solo
necesitás inspiración rápida, el **modo Lite** (`protocols/00-lite/`)
deja benchmark + brief de 1 página en una fracción del costo.
