# Run Request — Fase 1: Benchmarking & Domain Research

Copiar, completar y pegar en el agente orquestador.
Protocolo completo: `protocols/01-benchmarking/MASTER_PROTOCOL.md`.

```text
Aplica el protocolo definido en protocols/01-benchmarking/MASTER_PROTOCOL.md
al siguiente caso.

RUBRO / DOMINIO:
<describir rubro>

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>

MERCADO OBJETIVO (obligatorio; se registra en market de run.yaml):
<país, región o conjunto de mercados; precisar jurisdicciones, sin default>

ALCANCE DEL PRODUCTO:
Combinación potencial de sitio institucional, aplicaciones internas/backoffice,
portal de clientes, ecommerce, marketplace, SaaS u otras superficies digitales
que la investigación determine como relevantes.

CONTEXTO DEL PROYECTO:
<cliente, restricciones, ideas iniciales, legacy, presupuesto, stack preferido, etc.>

RESTRICCIONES / EXCLUSIONES:
<opcional>

PREGUNTAS QUE QUIERO RESPONDER:
<opcional>

INSTRUCCIÓN ESPECIAL:
Cualquier agente o subagente puede hacerme preguntas antes de continuar si
detecta ambigüedades materiales. Agrupa las preguntas y explica brevemente
por qué cada una puede cambiar el resultado. Si falta el mercado o hay
conflicto, pregunta y espera antes de investigar; no asumas Argentina/LatAm.
Investiga global primero y el mercado elegido de forma independiente después.
```

Al iniciar, crear `output/<slug>/run.yaml` (ver `templates/run.yaml`).
