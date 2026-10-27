---
name: researcher
description: "Trigger: investigar rubro, benchmark, research pre-dev, brief de producto, discovery técnico. Corre el kit researcher (Lite, Fase 1, Fase 2) en cualquier proyecto."
license: Apache-2.0
metadata:
  author: "ferenoch"
  version: "1.0"
---

## Activación

Usar para research pre-dev, inspiración, benchmarking, brief o discovery.
Separar **objetivo** (explorar/inspirar, contrastar una idea, apoyar una
decisión concreta) de **etapa**. Sin una decisión material abierta, no
preguntar por la etapa: usar Lite equilibrado como punto de partida.
El mercado es independiente: siempre lo elige el usuario, sin país/región
por defecto. Si falta o hay conflicto, preguntar y esperar antes del research.

## Reglas

- Sin código, backlog ni estimaciones de implementación.
- Modelos como parámetros de runtime/usuario; en Lite, uno por corrida.
  Una preferencia no prueba ejecución; dos modelos no son dos fuentes.
- `market` en `templates/run.yaml` es la configuración canónica obligatoria,
  sin default Argentina/LatAm. En Fase 2 heredar el mercado del brief validado;
  cualquier cambio exige revalidación humana antes de continuar.
- Global primero, investigación independiente del mercado elegido después;
  referentes regionales, pagos y regulación siguen sus jurisdicciones.
- Evidencia insuficiente queda visible como `UNRESOLVED`.
- No escribir artefactos sin resolver permisos, kit y exclusión Git.

## Enrutamiento

| Necesidad | Etapa / protocolo relativo al kit |
|---|---|
| Opciones fundamentadas para decidir qué validar | Lite: `protocols/00-lite/LITE_PROTOCOL.md` |
| Brief completo para una apuesta comprometida | Fase 1: `protocols/01-benchmarking/MASTER_PROTOCOL.md` |
| Product Brief validado por una persona | Fase 2: `protocols/02-tech-discovery/MASTER_PROTOCOL.md` |

## Ejecución

1. Resolver el kit y registrar su procedencia según
   [kit y permisos](references/kit.md). No clonar ni instalar automáticamente.
2. Leer el protocolo elegido y sus referencias; conservar sus contratos.
3. Ejecutar [preflight de output](references/output-guard.md) en el proyecto
   consumidor **antes de cualquier artefacto**, incluso `run.yaml`.
4. Solo tras pasar el guard, usar `templates/run.yaml` y escribir bajo
   `<proyecto>/output/<slug>/{lite,brief,discovery}/`, nunca en el kit externo.
5. Usar `LITE_TARGET_MARKET.md` / `04_TARGET_MARKET.md` y
   `scope.target_market_research` en nuevas corridas. No migrar ni renombrar
   outputs antiguos; al retomarlos registrar sus rutas exactas en `run.yaml`
   (`notes`) y preservar artefactos/metadata. `argentina_research` es histórico.
6. Registrar evidencia de ejecución, incertidumbre y decisión habilitada.
   Lite no habilita Fase 2 con un brief sin validar.

## Entrega

Informar objetivo, mercado/jurisdicciones, etapa, perfil/presupuesto,
kit/versión/dirty, modelo observado (o no medido), rutas, límites y
`UNRESOLVED`. En Lite, ledger
solo `REGULATORIO`/`MVP`, sin ciclo adversarial; declarar su ausencia
y recomendar siguiente validación o Fase 1 solo cuando corresponda.
