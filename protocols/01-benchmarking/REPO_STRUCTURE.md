# Recommended Repository Structure

```text
benchmarking-research/
├── README.md
├── protocol/
│   ├── MASTER_PROTOCOL.md
│   ├── WORKFLOW.md
│   ├── EVIDENCE_POLICY.md
│   ├── ARTIFACT_CONTRACTS.md
│   └── RUN_REQUEST_TEMPLATE.md
├── research/
│   ├── inmobiliario/
│   │   ├── run.yaml
│   │   ├── 01_DOMAIN_MAP.md
│   │   ├── 02_COMPETITOR_UNIVERSE.md
│   │   ├── 03_GLOBAL_BENCHMARK.md
│   │   ├── 04_ARGENTINA_MARKET.md
│   │   ├── 05_SYNTHESIS_V1.md
│   │   ├── CLAIM_LEDGER_V1.md
│   │   ├── 06_ADVERSARIAL_REVIEW.md
│   │   ├── 07_DEFENSE.md
│   │   ├── CLAIM_LEDGER_FINAL.md
│   │   ├── 08_PRODUCT_DISCOVERY.md
│   │   ├── 09_PRODUCT_BRIEF.md
│   │   ├── FINAL_REPORT.md
│   │   └── sources/
│   └── veterinaria/
│       └── ...
└── templates/
    └── run.yaml
```

## `run.yaml` recomendado

```yaml
research_id: inmobiliario-argentina-001
rubric: inmobiliario
market: Argentina
orchestrator_model: <modelA>
adversarial_model: <modelB>
started_at: YYYY-MM-DD
status: active
scope:
  indirect_substitutes: false
  global_research: true
  argentina_research: true
  technical_observation: true
notes: ""
```

## Recomendaciones adicionales

### 1. Git como log de investigación

Hacer commits por fase, por ejemplo:

```text
research(inmobiliario): complete domain map
research(inmobiliario): add global benchmark
review(inmobiliario): adversarial challenge round 1
research(inmobiliario): adjudicate claim ledger
product(inmobiliario): produce product brief
```

Así se puede comparar cómo cambió una conclusión.

### 2. No borrar desacuerdos

La versión final no debe reemplazar silenciosamente los artefactos anteriores. Conservar crítica, defensa y ledgers previos.

### 3. Separar investigación de decisiones

Un dato del mercado no equivale automáticamente a una decisión de producto. Registrar el puente lógico mediante `Product Implication`.

### 4. Crear un backlog de incertidumbres

Los `UNRESOLVED` valiosos deben convertirse en preguntas de research o validación con usuarios, no esconderse.

### 5. Evitar benchmarking por feature-count

No concluir que una funcionalidad debe construirse porque muchos competidores la tengan. Evaluar:

- qué problema resuelve;
- para qué segmento;
- frecuencia de uso;
- costo operativo;
- dependencia regulatoria;
- relevancia argentina;
- impacto sobre la propuesta de valor.

### 6. Tratar UX observable y arquitectura inferida de forma distinta

La UI puede observarse directamente. El backend, modelo de datos y arquitectura generalmente no. Mantener niveles de confianza separados.

### 7. Hacer freshness checks

Para investigaciones reutilizadas meses después, revisar al menos:

- pricing;
- planes;
- features;
- integraciones;
- regulación;
- productos discontinuados;
- adquisiciones/cambios de marca;
- fuentes que ya no existen.

### 8. Añadir una fase humana entre research y implementación

El protocolo termina en un Product Brief, no en un backlog definitivo. Antes de diseñar arquitectura o empezar coding, el desarrollador debería aprobar:

- qué problema quiere resolver;
- para quién;
- cuáles son los workflows prioritarios;
- qué hipótesis requieren validación real.
