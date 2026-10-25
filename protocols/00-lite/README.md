# Modo Lite — Benchmark express → brief de 1 página

Versión liviana de la Fase 1 para decidir **si una idea vale la pena**
antes de pagar el costo del protocolo completo. Sin ciclo adversarial,
con ledger mínimo y tope de esfuerzo explícito.

## Cuándo usarlo

- Explorar un rubro nuevo, buscar inspiración, comparar ideas.
- Armar el caso para (o contra) un proyecto interno.
- Preparar una conversación con un cliente con algo más que opiniones.

## Cuándo NO usarlo (escalar a Fase 1)

- Ya hay decisión de construir y el brief va a alimentar arquitectura.
- Hay riesgo regulatorio alto que exige adjudicación adversarial.
- El dominio es desconocido y los claims de MVP no se pueden sostener
  con un ledger mínimo. El propio Lite te lo dice en `UNRESOLVED`.

## Cómo se usa

```text
Aplica el protocolo protocols/00-lite/LITE_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>

MODELO:
- ORCHESTRATOR_MODEL: <modelo A>

MERCADO OBJETIVO INICIAL:
Argentina

CONTEXTO DEL PROYECTO:
<ideas iniciales, restricciones conocidas>
```

Plantilla: [`templates/run-lite.md`](../../templates/run-lite.md).
Protocolo: [`LITE_PROTOCOL.md`](LITE_PROTOCOL.md).

## Salidas (en `output/<slug>/lite/`)

- `LITE_DOMAIN.md` — mapa de dominio compacto.
- `LITE_BENCHMARK.md` — referentes por categoría (con tope y fuentes).
- `LITE_ARGENTINA.md` — particularidades locales flash.
- `LITE_LEDGER.md` — **solo** claims regulatorios y de MVP.
- `LITE_BRIEF.md` — brief de 1 página.

## Costo de referencia

Piloto `estudio-agrimensura` (local, no versionado): 6 búsquedas, 0 fetches,
~30 min, 5 artefactos. Detalle en `output/estudio-agrimensura/run.yaml`
(campos `lite_measured`).
Si un Lite supera ~2× ese costo, algo se salió del modo express:
cortar y escalar a Fase 1.
