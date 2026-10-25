# Cómo guardar investigaciones

Cada corrida de la Fase 1 vive en su propia carpeta:

```text
research/<slug-del-rubro>/
├── run.yaml                     ← metadatos (copiar de templates/run.yaml)
├── 01_DOMAIN_MAP.md
├── 02_COMPETITOR_UNIVERSE.md
├── 03_GLOBAL_BENCHMARK.md
├── 04_ARGENTINA_MARKET.md
├── 05_SYNTHESIS_V1.md
├── CLAIM_LEDGER_V1.md
├── 06_ADVERSARIAL_REVIEW.md
├── 07_DEFENSE.md
├── CLAIM_LEDGER_FINAL.md
├── 08_PRODUCT_DISCOVERY.md
├── 09_PRODUCT_BRIEF.md
├── FINAL_REPORT.md
├── sources/                     ← capturas, PDFs, notas de campo (opcional)
└── discovery/                   ← salida de la Fase 2 (si se ejecuta)
    ├── 01_PRODUCT_TO_TECH_MAP.md
    ├── 02_DOMAIN_AND_DATA_MODEL.md
    ├── 03_ARCHITECTURE_DRIVERS.md
    ├── 04_TECHNICAL_OPTIONS.md
    ├── 05_SECURITY_PRIVACY_COMPLIANCE.md
    ├── 06_INTEGRATIONS.md
    ├── 07_DELIVERY_AND_OPERATIONS.md
    ├── 08_ARCHITECTURE_HYPOTHESES.md
    ├── 09_TECHNICAL_SYNTHESIS_V1.md
    ├── TECH_DECISION_LEDGER_V1.md
    ├── 10_ADVERSARIAL_REVIEW.md
    ├── 11_DEFENSE_AND_REVISION.md
    ├── TECH_DECISION_LEDGER_FINAL.md
    └── FINAL_TECHNICAL_DISCOVERY.md
```

## Reglas

- Un slug por rubro/proyecto: `inmobiliario/`, `veterinaria-turnos/`,
  `compraventa-autos/`. Sin espacios, en minúsculas, con guiones.
- `run.yaml` se crea al iniciar y se actualiza el `status`
  (`active` → `brief-ready` → `discovery-active` → `done`).
- Commits por fase, no un commit gigante al final.
- No borrar los artefactos intermedios del ciclo adversarial
  (`SYNTHESIS_V1`, `CLAIM_LEDGER_V1`, `ADVERSARIAL_REVIEW`, `DEFENSE`).
  Son la auditoría del porqué.
- Los `UNRESOLVED` del ledger final se listan también como preguntas
  abiertas del brief: son el backlog de validación con usuarios.
- Si una investigación se reutiliza meses después: freshness check
  (pricing, features, integraciones, regulación, discontinuados).
