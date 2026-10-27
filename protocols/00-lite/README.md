# Modo Lite — Opciones fundamentadas para decidir qué validar

Lite sirve para inspiración/exploración, contrastar una idea o apoyar una
decisión concreta. No demuestra demanda ni entrega go/no-go o MVP validado.
Objetivo y etapa son elecciones distintas; por defecto, Lite equilibrado,
un modelo y sin ciclo adversarial. Si ese contraste es indispensable,
proponer Fase 1 en vez de ampliar el Lite.

## Camino rápido

1. Completar [run-lite](../../templates/run-lite.md) con objetivo, decisión
   y mercado elegido por el usuario. Registrar `market` en `run.yaml` sin
   país/región por defecto; si falta o hay conflicto, preguntar y esperar.
2. Resolver [kit/permisos](../../skills/researcher/references/kit.md) y pasar el
   [preflight Git](../../skills/researcher/references/output-guard.md) antes
   de cualquier artefacto, incluido `run.yaml`.
3. Seguir [LITE_PROTOCOL.md](LITE_PROTOCOL.md): comparar 2–3 enfoques
   distintos, contexto global y local independiente, fuentes inspeccionadas.
4. Cerrar con límites, decisión habilitada e incertidumbre pendiente.

## Elegir presupuesto, no llenar cuotas

Límites **propuestos**, no performance medida: exploratorio 4–6 consultas
variadas / 2–3 lecturas; equilibrado **DEFAULT** 6–8 / 4–6. Elegir topes
concretos. Para decisión, las incertidumbres críticas determinan profundidad
y pueden requerir Fase 1. No son estimaciones de tiempo ni tokens.

Geografía/startup/open source son etiquetas; contar referentes únicos sin
cuotas aditivas. Parar por cobertura suficiente, saturación de decisión o
presupuesto agotado, distinguiéndolos. Snippets descubren fuentes, no
acreditan lectura ni necesidad de producto. El piloto histórico es
**SELF-REPORTED**, no baseline medido/calibrado ni prueba de ahorro.

## Salidas en `output/<slug>/lite/`

- `LITE_BRIEF.md`: una página ejecutiva, recomendación tentativa y validación.
- `LITE_DOMAIN.md`: actores, contexto y supuestos.
- `LITE_BENCHMARK.md`: enfoques, referentes y fuentes/pasajes inspeccionados.
- `LITE_TARGET_MARKET.md`: contraste local y checks pertinentes a la decisión.
- `LITE_LEDGER.md`: solo `REGULATORIO`/`MVP`, con estados y límites.

Enlazar, no repetir. Guardar telemetría real o `null` («no medido») en
[run.yaml](../../templates/run.yaml). Un desconocido bloquea/escalaría solo
si es indispensable hoy, no por pertenecer a una categoría.

## Siguiente etapa

Fase 1 cuando hace falta un brief completo o resolver incertidumbres
indispensables. Fase 2 requiere un Product Brief validado por una persona,
incluido su mercado. Fase 2 lo hereda; cambiarlo requiere revalidación.
Un Lite sin validar no es un atajo. Ver [pipeline](../../docs/PIPELINE.md)
e [instalación](../../skills/researcher/INSTALL.md).
