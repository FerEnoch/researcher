# Run Request — Lite: opciones fundamentadas para decidir qué validar

Completar y pegar; [protocolo](../protocols/00-lite/LITE_PROTOCOL.md).
La etapa es Lite; elegir el objetivo por separado. No preguntar salvo que
una decisión material siga abierta. Mercado faltante o contradictorio
siempre requiere preguntar y esperar antes de investigar.

```text
Aplica el protocolo protocols/00-lite/LITE_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>
OBJETIVO:
<inspiración/exploración | contrastar una idea | apoyar una decisión concreta>
DECISIÓN ACTUAL Y PREGUNTAS:
<qué queremos decidir y qué queda fuera>
MODELO (uno por Lite):
- ORCHESTRATOR_MODEL: <modelo seleccionado del runtime/usuario>
MERCADO OBJETIVO (obligatorio; se registra en market de run.yaml):
<país, región o conjunto de mercados; precisar jurisdicciones, sin default>
CONTEXTO DEL PROYECTO:
<ideas, actores, restricciones conocidas>
PERFIL Y TOPES PROPUESTOS:
Equilibrado DEFAULT: elegir tope de 6–8 consultas variadas y 4–6 lecturas.
Alternativa exploratoria: 4–6 y 2–3. Orientado a decisión: acordar topes
según incertidumbres críticas; puede requerir Fase 1. No llenar cuotas.
ADVERSARIAL:
No se ejecuta en Lite. Si es indispensable, proponer Fase 1 por separado.

INSTRUCCIONES:
Resolver kit/permisos y preflight Git antes de cualquier artefacto.
Comparar 2–3 enfoques reales, global primero y mercado elegido independiente
después. Referentes regionales según ese mercado, no LatAm por defecto.
Fuentes primarias leídas; snippets son pistas, no prueba de necesidad.
Mantener desconocidos visibles; bloquear/escalar solo si son indispensables
para esta decisión. Citar en cada decisión/recomendación sus fuentes
primarias inspeccionadas con links (`[nombre](URL) — fecha — pasaje/sección`);
sin fuente, marcar `UNRESOLVED` y no recomendar. No expandir a otra fase unilateralmente.
Registrar motivo de parada (cobertura, saturación de decisión o presupuesto),
telemetría real o null/no medido, y la decisión que habilitó el run.
```

Seguir [guard de output](../skills/researcher/references/output-guard.md);
solo tras aprobarlo crear `output/<slug>/run.yaml` desde
[run.yaml](run.yaml) y los cinco `LITE_*.md` en `output/<slug>/lite/`.
La preferencia de modelos no acredita ejecución: registrar evidencia real.
Fase 2 exige Product Brief validado por una persona; Lite no lo sustituye.
