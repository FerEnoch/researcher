# LITE PROTOCOL — Opciones fundamentadas para decidir qué validar

## 0. Alcance e inicio seguro

Lite compara enfoques y prepara validaciones; no prueba demanda ni entrega
un go/no-go o un MVP validado. Termina en un brief ejecutivo de una página
con soporte conciso, no en arquitectura, backlog, estimaciones ni código.

Antes de cualquier artefacto, seguir el [preflight Git de output](../../skills/researcher/references/output-guard.md),
incluso al usar este protocolo directamente. Resolver el kit y permisos
según [procedencia](../../skills/researcher/references/kit.md).
Solo después crear `output/<slug>/run.yaml` desde la
[plantilla](../../templates/run.yaml). No sobrescribir corridas existentes.

## 1. Objetivo, etapa y modelo

Registrar el objetivo por separado de la etapa Lite: **inspiración/exploración**,
**contrastar una idea** o **apoyar una decisión concreta**. Preguntar solo si
hay una decisión material abierta; en ese caso, una ronda de hasta tres
preguntas. Explicitar supuestos sin convertirlos en hechos.

El usuario debe elegir el mercado en runtime; registrar su alcance y
jurisdicciones en `market` de `run.yaml`, sin default Argentina ni LatAm.
Si falta, queda un placeholder o contradice pedido/metadata, preguntar y
esperar aclaración antes de investigar. Es una decisión material, no un
supuesto permitido. Al retomar corridas antiguas, conservar artefactos y
metadata históricos y registrar sus rutas exactas en `notes`; no renombrarlos.
Las nuevas corridas usan `scope.target_market_research`.

Un solo `ORCHESTRATOR_MODEL` por corrida Lite, elegido por usuario/runtime.
No afirmar que corrió un modelo por estar preferido o escrito en el pedido.
Seleccionar uno según disponibilidad y preferencias de la corrida, sin
inventar identificadores de API ni evidencia de ejecución. No imponer un
proveedor desde el protocolo. Dos modelos coincidentes no son fuentes
independientes. Lite no ejecuta ciclo adversarial: si la decisión necesita
ese contraste, proponer Fase 1 con alcance y presupuesto explícitos,
sin ampliar el Lite automáticamente.

## 2. Presupuestos propuestos y parada

Estos rangos son **límites propuestos de planificación**, no cuotas mínimas,
performance medida ni estimaciones de tiempo/tokens. Seleccionar un tope
concreto dentro del perfil y registrarlo; se puede terminar antes.

| Perfil | Consultas variadas | Lecturas dirigidas de fuentes |
|---|---|---|
| Exploratorio | 4–6 | 2–3 |
| Equilibrado (DEFAULT) | 6–8 | 4–6 |
| Orientado a decisión | Según incertidumbres críticas; acordar límite, puede requerir Fase 1 | Priorizar evidencia indispensable |

La distribución 30% apertura / 50% contraste y lectura / 20% síntesis es
una heurística no calibrada. Favorecer lectura de fuentes frente a más
productos redundantes, duplicar cinco archivos o sumar otro modelo.

Parar cuando los enfoques y preguntas relevantes estén suficientemente
cubiertos, cuando nuevas búsquedas dejen de cambiar la decisión, o al
agotar el presupuesto. Registrar motivo: `sufficient_coverage`,
`decision_saturation` o `budget_exhausted`; agotar presupuesto **no** prueba
saturación. No afirmar exhaustividad global tras una búsqueda superficial.

## 3. Cobertura diversa, no inventarios por cuota

Elegir referentes no redundantes por su aporte a la decisión. Global,
local, startup y open source son etiquetas, no poblaciones aditivas:
un referente con varias etiquetas cuenta una vez. Registrar nombre, URL,
segmento, etiquetas, razón de inclusión y fuente primaria inspeccionada;
si solo se descubrió, etiquetar pendiente, no como referente verificado.

Comparar **2–3 enfoques genuinamente distintos** antes de recomendar:
problema/actor, mecanismo, trade-offs, evidencia y qué validar. No fabricar
alternativas; si no se hallaron, declarar la carencia y no cerrar una
recomendación comparativa. Cuando aporte, incluir 1–2 inspiraciones de
dominios adyacentes, rotuladas **INSPIRACIÓN**, no competidores directos ni
prueba de demanda local. No inferir arquitectura oculta de una interfaz.

Mantener contexto global primero y búsqueda independiente del mercado
elegido después: no es una traducción. Los referentes regionales siguen ese
mercado, no una región implícita. Investigar actores, hábitos y restricciones
pertinentes. Pagos, canales, regulación y logística se chequean según la
jurisdicción y decisión actual; no son bloqueantes universales. Solo si el
mercado incluye Argentina y aplica, considerar ARCA o Mercado Pago.

## 4. Evidencia y ledger mínimo

`LITE_LEDGER.md` contiene **solo** categorías `REGULATORIO` y `MVP`.
Las demás observaciones van en las notas de dominio/benchmark/locales.

- Snippets son pistas de descubrimiento, no lectura ni prueba de necesidad.
  Un fetch por sí solo tampoco acredita lectura o aplicabilidad jurídica.
- Una página oficial leída acredita lo que el proveedor **anuncia**, no
  demanda ni validez de un MVP. Una recomendación de MVP conecta por
  separado evidencia con problema, actor y contexto local; cita claims o
  queda `UNRESOLVED`. Table stakes/diferenciadores/anti-features son hipótesis.
- Claims materiales citan pasajes primarios realmente inspeccionados:
  URL, fecha de consulta, pasaje/sección, alcance/jurisdicción y límites.
  Evidencia parcial solo sostiene la porción efectivamente respaldada.
- **Obligación de cita por decisión: ninguna decisión, recomendación,
  table stake, diferenciador, anti-feature, corte MVP, integración ni
  riesgo se sostiene sin cita.** Cada una cita en el mismo artefacto sus
  fuentes primarias realmente inspeccionadas con formato mínimo
  `[nombre](URL) — fecha de consulta — pasaje/sección`. Sin fuente
  inspeccionada, la decisión queda `UNRESOLVED` y no se recomienda;
  se registra qué falta para resolverla. Un Lite sin estas citas con
  links está incompleto, aunque enlace IDs del ledger.
- Separar naturaleza `FACT` / `INFERENCE` / `IDEA` de confianza y estado.
  Estados estables: `SUPPORTED`, `PARTIALLY_SUPPORTED`, `UNRESOLVED`,
  `CONTRADICTED`. Un snippet solo no habilita apoyo material.
- Columnas: ID, claim, categoría, naturaleza, fuente/pasaje y fecha,
  alcance/jurisdicción, limitaciones, confianza, estado, implicancia para
  la decisión e indispensabilidad actual. El estado no es una puntuación.

Un desconocido regulatorio o de MVP bloquea/escalaría **solo si es
indispensable para la decisión actual**. Explicar por qué y pedir la
validación humana/especializada o Fase 1 pertinente; no ampliar alcance
unilateralmente. Los demás se conservan visibles sin escalado automático.

## 5. Cinco artefactos compatibles, sin duplicación

Guardar bajo `output/<slug>/lite/`. Limitar presentación, no honestidad:
las limitaciones sustanciales no se omiten para caber en una página.

| Archivo | Contenido conciso |
|---|---|
| `LITE_DOMAIN.md` | Objetivo, mercado/jurisdicciones, decisión, actores, vocabulario/workflows útiles y supuestos. |
| `LITE_BENCHMARK.md` | Comparación de enfoques, referentes únicos, fuentes/pasajes, inspiraciones y registro de consultas/lecturas. |
| `LITE_TARGET_MARKET.md` | Mercado elegido, contraste local independiente, evidencia y checks pertinentes o no pertinentes con motivo. |
| `LITE_LEDGER.md` | Solo REGULATORIO/MVP; IDs estables, soporte y desconocidos. Si no hay claims, declararlo. |
| `LITE_BRIEF.md` | Una página ejecutiva: problema/actores, enfoques y trade-offs, recomendación tentativa con cita con links por decisión y próxima validación. |

El brief enlaza notas e IDs, no repite inventarios, y **cita en cada
decisión/recomendación sus fuentes con links clicables** según la
obligación de §4 (formato `[nombre](URL) — fecha — pasaje/sección`;
si no hay fuente inspeccionada, marca `UNRESOLVED`). Incluir propuesta de
valor/superficies tentativas, table stakes (máx. 5), diferenciadores (máx. 3),
anti-features (máx. 3), hipótesis de corte MVP con ledger, no-construir aún,
integraciones pertinentes y riesgos top 3, compactados o referenciados.
Cerrar con **Qué NO valida este Lite**, preguntas pendientes y la decisión
que efectivamente habilitó (también puede ser posponer la recomendación).

## 6. Medición y handoff

Completar `run.yaml` con perfil, presupuesto, consultas variadas reales y
fuentes realmente leídas (no llamadas fetch), modelo/config con evidencia,
inicio/fin y duración transcurrida observada. Tokens in/out y costo solo si
el runtime los proporciona. Ausente = `null` / «no medido», nunca cero ni
estimación disfrazada; registrar 0 solo si se observó realmente. Registrar
incertidumbre remanente, motivo de parada y decisión habilitada. Los rangos
del perfil no predicen tiempo, tokens ni ahorro.

No usar el piloto histórico como baseline: sus cifras son SELF-REPORTED,
no medidas ni calibradas. No hay umbral de costo calibrado ni ahorro demostrado.

Reutilizar las notas e IDs en Fase 1 si el alcance o una incertidumbre
indispensable lo requiere. No hay salto silencioso a Fase 2: exige un
Product Brief genuinamente validado por una persona y el ledger requerido
por esa fase. Fase 2 hereda el mercado validado del brief; un cambio exige
revalidación humana. Un Lite sin validar no lo sustituye ni etiquetándolo provisorio.
