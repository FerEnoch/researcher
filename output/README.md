# Cómo guardar investigaciones (local, no versionado)

Todo lo que genera una corrida vive bajo `output/<slug>/` y **no se
commitea**: el repo publicado es solo el kit. Cada corrida local conserva
sus artefactos sin ensuciar el historial.

```text
output/<slug>/
├── run.yaml                     ← metadatos (copiar de templates/run.yaml)
├── brief/                       ← salida de la Fase 1 (y del modo Lite)
│   ├── 01_DOMAIN_MAP.md
│   ├── 02_COMPETITOR_UNIVERSE.md
│   ├── 03_GLOBAL_BENCHMARK.md
│   ├── 04_ARGENTINA_MARKET.md
│   ├── 05_SYNTHESIS_V1.md
│   ├── CLAIM_LEDGER_V1.md
│   ├── 06_ADVERSARIAL_REVIEW.md
│   ├── 07_DEFENSE.md
│   ├── CLAIM_LEDGER_FINAL.md
│   ├── 08_PRODUCT_DISCOVERY.md
│   ├── 09_PRODUCT_BRIEF.md
│   ├── FINAL_REPORT.md
│   └── sources/                 ← capturas, PDFs, notas de campo (opcional)
├── discovery/                   ← salida de la Fase 2 (si se ejecuta)
│   ├── 01_PRODUCT_TO_TECH_MAP.md
│   ├── 02_DOMAIN_AND_DATA_MODEL.md
│   ├── 03_ARCHITECTURE_DRIVERS.md
│   ├── 04_TECHNICAL_OPTIONS.md
│   ├── 05_SECURITY_PRIVACY_COMPLIANCE.md
│   ├── 06_INTEGRATIONS.md
│   ├── 07_DELIVERY_AND_OPERATIONS.md
│   ├── 08_ARCHITECTURE_HYPOTHESES.md
│   ├── 09_TECHNICAL_SYNTHESIS_V1.md
│   ├── TECH_DECISION_LEDGER_V1.md
│   ├── 10_ADVERSARIAL_REVIEW.md
│   ├── 11_DEFENSE_AND_REVISION.md
│   ├── TECH_DECISION_LEDGER_FINAL.md
│   └── FINAL_TECHNICAL_DISCOVERY.md
└── lite/                        ← salida del modo Lite (si se usa)
    ├── LITE_DOMAIN.md
    ├── LITE_BENCHMARK.md
    ├── LITE_ARGENTINA.md
    ├── LITE_LEDGER.md           ← solo claims regulatorios y de MVP
    └── LITE_BRIEF.md            ← brief de 1 página
```

## Por qué subcarpetas por etapa

Los protocolos completo de Fase 1 y Fase 2 usan nombres de artefacto
casi idénticos (`06_ADVERSARIAL_REVIEW.md`, `WORKFLOW.md`, etc.).
Las subcarpetas `brief/` / `discovery/` / `lite/` eliminan la colisión:
el mismo nombre en distinta carpeta es de distinta etapa. Nunca mezclar
artefactos de dos etapas en la misma carpeta.

## Reglas

- Un slug por rubro/proyecto: `inmobiliario/`, `veterinaria-turnos/`,
  `estudio-agrimensura/`. Sin espacios, en minúsculas, con guiones.
- `run.yaml` se crea al iniciar y se actualiza el `status`
  (`active` → `brief-ready` → `discovery-active` → `done`;
  en Lite: `active` → `lite-done`, o `lite-done` → `discovery-active`
  si después se escala a Fase 2).
- Commits: los outputs no se versionan, así que no hay commits por fase
  de contenido. Lo que sí se versiona (y se commitea) son mejoras al kit:
  protocolos, templates, docs.
- No borrar los artefactos intermedios del ciclo adversarial
  (`SYNTHESIS_V1`, `CLAIM_LEDGER_V1`, `ADVERSARIAL_REVIEW`, `DEFENSE`).
  Son la auditoría del porqué.
- Los `UNRESOLVED` del ledger final se listan también como preguntas
  abiertas del brief: son el backlog de validación con usuarios.
- Si una investigación se reutiliza meses después: freshness check
  (pricing, features, integraciones, regulación, discontinuados).
