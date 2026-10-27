# Benchmarking & Domain Research Protocol

Protocolo reutilizable para investigación de rubros, benchmarking competitivo, discovery de producto y preparación de un brief de producto previo al desarrollo web fullstack.

Está pensado para ejecutarse desde agentes de coding/research como OpenCode o Gentle Shell, usando un **modelo orquestador** y uno o más **modelos revisores/adversariales**. Los modelos son parámetros dinámicos: el protocolo no depende de proveedores ni nombres concretos.

## Uso rápido

Ejemplo de invocación:

```text
Aplica este protocolo al rubro: inmobiliario,
utilizando los siguientes modelos:
- ORCHESTRATOR_MODEL: Muse Spark 1.3 Contributor
- ADVERSARIAL_MODEL: DeepSeek V4 Pro

Contexto adicional del proyecto:
- Mercado objetivo: <elegido por el usuario; precisar jurisdicciones>
- Tipo de producto esperado: combinación de sitio institucional, portal de clientes y backoffice
- Restricciones conocidas: ninguna por ahora
```

También puede usarse con otros modelos en el futuro:

```text
Aplica este protocolo al rubro: veterinaria con agenda de turnos,
utilizando los siguientes modelos:
- ORCHESTRATOR_MODEL: <modelA>
- ADVERSARIAL_MODEL: <modelB>
- MERCADO OBJETIVO: <país, región o conjunto de mercados; sin default>
```

## Objetivo

El protocolo busca producir dos resultados principales:

1. **Research de dominio/rubro**: comprender actores, operaciones, procesos, reglas, terminología, necesidades, dolores, tendencias y particularidades locales.
2. **Discovery de producto**: convertir los hallazgos en oportunidades, workflows, feature map, decisiones de producto y un brief accionable para desarrollo.

El benchmarking competitivo es un medio para esos fines, no el fin único.

## Principios

- `market` en [run.yaml](../../templates/run.yaml) es obligatorio y elegido
  en runtime, sin default Argentina/LatAm; si falta o hay conflicto,
  preguntar y esperar antes del research.
- Investigación global primero; investigación independiente del mercado elegido después.
- Separar líderes globales, referentes regionales pertinentes al mercado,
  actores de ese mercado, startups innovadoras y open source relevante.
- No incluir competidores indirectos o sustitutos salvo que el usuario lo solicite expresamente.
- Toda afirmación relevante debe distinguir entre evidencia, inferencia y opinión.
- Las discrepancias entre modelos se resuelven por evidencia, no por autoridad ni retórica.
- Cuando no exista evidencia suficiente, la conclusión debe quedar marcada como `UNRESOLVED`.
- Cualquier agente o subagente puede hacer preguntas al usuario antes de continuar si una ambigüedad material puede alterar significativamente el resultado.
- Las preguntas deben agruparse y priorizarse; no deben interrumpir por detalles menores que puedan resolverse con supuestos explícitos.

## Archivos del protocolo

- `MASTER_PROTOCOL.md`: prompt principal para pegar en el agente orquestador.
- `WORKFLOW.md`: fases, roles y secuencia adversarial.
- `EVIDENCE_POLICY.md`: reglas de investigación, fuentes y adjudicación.
- `ARTIFACT_CONTRACTS.md`: documentos que debe producir la ejecución.
- `REPO_STRUCTURE.md`: estructura recomendada para el repositorio de research.
- `RUN_REQUEST_TEMPLATE.md`: plantilla corta para iniciar un nuevo rubro.

## Recomendación operativa

En este kit unificado, usar `output/<slug>/brief/` tras el
[guard Git](../../skills/researcher/references/output-guard.md): outputs locales
no versionados. Conservar finales e intermedios adversariales para auditoría.
Nuevas corridas usan `04_TARGET_MARKET.md` y `scope.target_market_research`;
las antiguas quedan sin migrar ni renombrar, registrando sus rutas exactas
en `run.yaml` (`notes`) al retomarlas. Ver [convención vigente](../../output/README.md).
