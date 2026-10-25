# Recommended Repository Structure

```text
technical-discovery/
├── protocol/
│   ├── MASTER_PROTOCOL.md
│   ├── WORKFLOW.md
│   ├── DECISION_POLICY.md
│   ├── ARTIFACT_CONTRACTS.md
│   └── RUN_REQUEST_TEMPLATE.md
│
├── projects/
│   └── <project>/
│       ├── inputs/
│       │   ├── PRODUCT_BRIEF.md
│       │   └── CLAIM_LEDGER_FINAL.md
│       ├── discovery/
│       │   ├── 01_PRODUCT_TO_TECH_MAP.md
│       │   ├── 02_DOMAIN_AND_DATA_MODEL.md
│       │   ├── 03_ARCHITECTURE_DRIVERS.md
│       │   ├── 04_TECHNICAL_OPTIONS.md
│       │   ├── 05_SECURITY_PRIVACY_COMPLIANCE.md
│       │   ├── 06_INTEGRATIONS.md
│       │   ├── 07_DELIVERY_AND_OPERATIONS.md
│       │   ├── 08_ARCHITECTURE_HYPOTHESES.md
│       │   ├── 09_TECHNICAL_SYNTHESIS_V1.md
│       │   ├── TECH_DECISION_LEDGER_V1.md
│       │   ├── 10_ADVERSARIAL_REVIEW.md
│       │   ├── 11_DEFENSE_AND_REVISION.md
│       │   ├── TECH_DECISION_LEDGER_FINAL.md
│       │   └── FINAL_TECHNICAL_DISCOVERY.md
│       └── run.yaml
└── README.md
```

## Recomendación Git

Commits por fase:
- `discovery: map product requirements to technical needs`
- `discovery: add domain and data model`
- `discovery: evaluate technical options`
- `review: adversarial technical review`
- `decision: finalize technical decision ledger`
- `discovery: finalize technical discovery`


## Después de este repositorio/protocolo

Los ADRs no se consideran una fase protocolizada adicional de este paquete. Para cada proyecto, pueden guardarse en el repo correspondiente (por ejemplo, `docs/adr/`), pero su investigación, debate y redacción se diseñarán con asistencia de IA específicamente para las decisiones reales de ese caso.
