# Cómo guardar investigaciones (local, no versionado)

Todo lo que genera una corrida vive bajo `output/<slug>/` y **no se
commitea**: el repo publicado es solo el kit. Cada corrida local conserva
sus artefactos sin ensuciar el historial. Este README y `.gitkeep` son
metadatos del kit, no research.

**Antes de escribir cualquier artefacto**, incluido `run.yaml`, aplicar el
[preflight Git](../skills/researcher/references/output-guard.md) en el
proyecto consumidor. Sin Git, permisos o exclusión comprobada: STOP.
Si hay research ya rastreado, reportar rutas exactas y detenerse;
`.gitignore` no desrastrea. Nunca desrastrear ni borrar automáticamente.
Añadir `/output/*` al `.gitignore` de ese proyecto solo si hace falta y está
autorizado; preservar metadatos/excepciones y revalidar todos los destinos.
No modificar exclusiones globales ni otros repositorios. Excluir de Git no
es cifrar ni autoriza guardar secretos o datos personales innecesarios.

```text
output/<slug>/
├── run.yaml                     ← metadatos (copiar de templates/run.yaml)
├── brief/                       ← salida de la Fase 1
│   ├── 01_DOMAIN_MAP.md
│   ├── 02_COMPETITOR_UNIVERSE.md
│   ├── 03_GLOBAL_BENCHMARK.md
│   ├── 04_TARGET_MARKET.md
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
    ├── LITE_TARGET_MARKET.md
    ├── LITE_LEDGER.md           ← solo claims regulatorios y de MVP
    └── LITE_BRIEF.md            ← opciones y próxima validación, 1 página
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
- `market` en [run.yaml](../templates/run.yaml) es obligatorio, elegido por
  el usuario en runtime y sin país/región por defecto. Si falta o hay
  conflicto, preguntar antes del research. Fase 2 hereda el mercado del
  brief validado; un cambio requiere revalidación humana, no override.
- Nuevas corridas usan los nombres neutrales del árbol y
  `scope.target_market_research`; `argentina_research` es solo histórico.
  No migrar ni renombrar outputs antiguos. Al retomarlos, registrar sus
  rutas exactas en `run.yaml` (`notes`) y conservar artefactos/metadata previos.
- `run.yaml` se crea **después del guard**, con objetivo, etapa y perfil
  separados. Status: `active` → `lite-done` para Lite; Fase 1/2 conservan
  `active` → `brief-ready` → `discovery-active` → `done`. Fase 2 exige
  Product Brief validado por humano: no hay salto desde Lite sin validar.
- Lite conserva los cinco nombres `LITE_`: brief ejecutivo + notas concisas
  enlazadas, sin duplicar contenido. Ledger solo `REGULATORIO`/`MVP`.
  Perfiles/presupuestos son propuestas, no cuotas ni mediciones; cerrar por
  cobertura, saturación de decisión o presupuesto, distinguiéndolos.
- Registrar consultas variadas y fuentes realmente leídas, modelo/config
  observado, tiempos y decisión habilitada en
  [run.yaml](../templates/run.yaml). Telemetría ausente = `null` / «no medido»;
  tokens/costo solo si el runtime los entrega. No inferir desde el perfil.
- Commits: los outputs no se versionan, así que no hay commits por fase
  de contenido. Lo que sí se versiona (y se commitea) son mejoras al kit:
  protocolos, templates, docs.
- No borrar los artefactos intermedios del ciclo adversarial
  (`SYNTHESIS_V1`, `CLAIM_LEDGER_V1`, `ADVERSARIAL_REVIEW`, `DEFENSE`).
  Son la auditoría del porqué.
- Los `UNRESOLVED` del ledger se enlazan como preguntas abiertas del brief;
  en Lite solo bloquean/escalan si son indispensables para la decisión actual.
- Si una investigación se reutiliza meses después: freshness check
  (pricing, features, integraciones, regulación, discontinuados).
