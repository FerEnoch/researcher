# Researcher

Kit de research pre-dev para proyectos internos: antes de escribir código,
investigamos el rubro, hacemos benchmarking, definimos el producto
y preparamos el terreno técnico. Todo con evidencia, revisión adversarial
y artefactos locales trazables (los outputs no se versionan).

## El pipeline

```
┌─────────────────────────┐     ┌─────────────────────────┐     ┌──────────────────┐
│  FASE 1: Benchmarking   │     │ FASE 2: Tech Discovery  │     │ ADRs ad hoc      │
│  y Domain Research      │────▶│                         │────▶│ (por proyecto)   │
│  protocols/01-...       │brief│ protocols/02-...       │final│ fuera de este    │
│                         │     │                         │tech │ repo / en cada   │
│  Idea → Product Brief   │     │ Brief → Discovery       │disc │ proyecto         │
└─────────────────────────┘     └─────────────────────────┘     └──────────────────┘
```

- **Fase 1** (`protocols/01-benchmarking/`): entiende el dominio, compara
  referentes globales / regionales pertinentes / del mercado objetivo /
  startups / open source,
  y termina en un **Product Brief** accionable. Con ciclo adversarial
  obligatorio (tesis → crítica → defensa → adjudicación).
- **Modo Lite** (`protocols/00-lite/`): opciones fundamentadas para decidir
  qué validar, no go/no-go ni MVP validado. Default equilibrado, un modelo,
  sin ciclo adversarial y brief ejecutivo de 1 página. Puede alimentar Fase 1;
  Fase 2 siempre exige un Product Brief genuinamente validado por un humano.
- **Fase 2** (`protocols/02-tech-discovery/`): convierte un Product Brief
  validado en un **Technical Discovery** auditable (drivers, opciones,
  seguridad, integraciones, operaciones, hipótesis de arquitectura).
  También con revisión adversarial. No genera backlog ni código.
- **ADRs**: deliberadamente fuera de este repo. Se diseñan ad hoc por
  proyecto, asistidos por IA, a partir del Technical Discovery final.

Detalle del flujo punta a punta: [`docs/PIPELINE.md`](docs/PIPELINE.md).

## Estructura

```text
researcher/
├── README.md                        ← este archivo
├── protocols/
│   ├── 00-lite/                     ← Modo Lite: benchmark express → brief 1 página
│   │   ├── README.md
│   │   ├── LITE_PROTOCOL.md         ← prompt principal (pegar en el agente)
│   │   └── RUN_REQUEST_TEMPLATE.md  ← plantilla de invocación
│   ├── 01-benchmarking/             ← Fase 1: dominio + benchmarking → Product Brief
│   │   ├── README.md
│   │   ├── MASTER_PROTOCOL.md       ← prompt principal (pegar en el orquestador)
│   │   ├── WORKFLOW.md              ← fases y roles
│   │   ├── EVIDENCE_POLICY.md       ← fuentes, claims, adjudicación
│   │   ├── ARTIFACT_CONTRACTS.md    ← artefactos exigidos por corrida
│   │   ├── REPO_STRUCTURE.md        ← convención original (ver nota abajo)
│   │   └── RUN_REQUEST_TEMPLATE.md  ← plantilla de invocación
│   └── 02-tech-discovery/           ← Fase 2: Brief → Technical Discovery
│       ├── README.md
│       ├── MASTER_PROTOCOL.md
│       ├── WORKFLOW.md
│       ├── DECISION_POLICY.md       ← jerarquía y tipos de decisión
│       ├── QUALITY_GATE.md          ← checklist de cierre
│       ├── ARTIFACT_CONTRACTS.md
│       ├── REPO_STRUCTURE.md
│       └── RUN_REQUEST_TEMPLATE.md
├── templates/
│   ├── run-lite.md                  ← invocación Lite (copiar/pegar)
│   ├── run-research.md              ← invocación Fase 1 (copiar/pegar)
│   ├── run-discovery.md             ← invocación Fase 2 (copiar/pegar)
│   └── run.yaml                     ← metadatos de corrida (ejemplo)
├── output/                          ← corridas LOCALES, no versionadas (ver output/README.md)
│   ├── README.md                    ← convención de carpetas por etapa
│   └── <slug>/                      ← brief/ · discovery/ · lite/ por investigación
├── skills/
│   └── researcher/                  ← skill para usar el kit desde cualquier proyecto
│       ├── SKILL.md                 ← instálalo con symlink (ver INSTALL.md)
│       ├── INSTALL.md
│       └── references/              ← resolución del kit y preflight Git
└── docs/
    └── PIPELINE.md                  ← cómo encadenar Lite → Fase 1 → Fase 2 → ADRs
```

> Nota: los `REPO_STRUCTURE.md` dentro de cada protocolo describen la
> convención original de ese protocolo aislado. La convención vigente
> para este repo unificado es: cada investigación vive en
> `output/<slug>/` con subcarpetas por etapa (`brief/`, `discovery/`,
> `lite/`). Ver [`output/README.md`](output/README.md).

## Uso rápido

Antes de **cualquier** artefacto, incluso `run.yaml`, ejecutar el
[preflight Git de output](skills/researcher/references/output-guard.md).
Sin Git, permisos o exclusión verificada, detenerse. Research ya rastreado
se reporta con rutas exactas: `.gitignore` no lo desrastrea.

### 0. Modo Lite — Opciones para decidir qué validar (default equilibrado)

```text
Aplica el protocolo protocols/00-lite/LITE_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>

OBJETIVO (separado de la etapa Lite):
<inspiración/exploración | contrastar una idea | apoyar una decisión concreta>
DECISIÓN ACTUAL:
<qué queremos decidir>

MODELO:
- ORCHESTRATOR_MODEL: <modelo A>

MERCADO OBJETIVO (obligatorio, elegido por el usuario):
<país, región o conjunto de mercados; precisar jurisdicciones>

CONTEXTO DEL PROYECTO:
<cliente, restricciones, ideas iniciales, etc.>
```

Plantilla lista para copiar: [`templates/run-lite.md`](templates/run-lite.md).
Ledger solo `REGULATORIO`/`MVP`; brief de 1 página y cuatro notas concisas
que se enlazan, no se duplican. Comparar 2–3 enfoques realmente distintos;
cuando aporte, 1–2 inspiraciones adyacentes rotuladas como tales.

Límites **propuestos**, no cuotas ni performance medida: exploratorio
4–6 consultas variadas / 2–3 lecturas; equilibrado **DEFAULT** 6–8 / 4–6.
Para decisión, la profundidad depende de incertidumbres críticas y puede
requerir Fase 1. Parar por cobertura, saturación de decisión o presupuesto,
sin confundir agotamiento con saturación. No hay ahorro de tokens calibrado.
Registrar telemetría observada o `null` («no medido»), nunca inferirla del perfil.
Preguntar solo si queda una decisión material abierta; un mercado ausente
o contradictorio siempre requiere aclaración antes de investigar.

### 1. Fase 1 — Investigar un rubro

```text
Aplica el protocolo protocols/01-benchmarking/MASTER_PROTOCOL.md al siguiente caso.

RUBRO / DOMINIO:
<rubro>

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>

MERCADO OBJETIVO (obligatorio, elegido por el usuario):
<país, región o conjunto de mercados; precisar jurisdicciones>

CONTEXTO DEL PROYECTO:
<cliente, restricciones, ideas iniciales, stack preferido, etc.>
```

Plantilla lista para copiar: [`templates/run-research.md`](templates/run-research.md).
Los modelos son parámetros: el protocolo no depende de proveedores concretos.

Salida: `output/<slug>/brief/` con domain map, benchmark global, mercado
objetivo (`04_TARGET_MARKET.md`), síntesis, claim ledger, ciclo adversarial,
product discovery, **`09_PRODUCT_BRIEF.md`** y **`FINAL_REPORT.md`**.

### 2. Fase 2 — Del Brief al Technical Discovery

Cuando el Product Brief esté validado por un humano, incluido su mercado:
Fase 2 lo hereda; cualquier cambio requiere revalidación humana previa.

```text
Aplica el protocolo protocols/02-tech-discovery/MASTER_PROTOCOL.md.

MODELOS:
- ORCHESTRATOR_MODEL: <modelo A>
- ADVERSARIAL_MODEL: <modelo B>

INPUTS:
- PRODUCT_BRIEF: output/<slug>/brief/09_PRODUCT_BRIEF.md
- CLAIM_LEDGER_FINAL: output/<slug>/brief/CLAIM_LEDGER_FINAL.md
```

Plantilla lista para copiar: [`templates/run-discovery.md`](templates/run-discovery.md).

Salida: `output/<slug>/discovery/` con
**`FINAL_TECHNICAL_DISCOVERY.md`** y **`TECH_DECISION_LEDGER_FINAL.md`**.

### 3. Después: ADRs del proyecto

Con el Technical Discovery en mano, diseñar los ADRs ad hoc para ese
proyecto (prompts, especialistas y profundidad según el caso).
No hay protocolo genérico de ADRs en este repo, por decisión explícita
del diseño original.

## Reglas del juego

1. **Evidencia o `UNRESOLVED`.** Todo claim importante se rastrea a
   fuentes, se marca como inferencia, o queda `UNRESOLVED`. Sin relleno
   con prosa confiada.
2. **Adversarial en Fases 1/2, no en Lite.** Tesis → crítica → defensa →
   adjudicación según protocolo. Resolver discrepancias
   por evidencia, nunca retórica; dos modelos no son fuentes independientes.
3. **Contexto global y local independiente**, nunca una traducción.
   El mercado local y los referentes regionales dependen de `market`, no de
   un país o región por defecto. En Lite, pagos, regulación o logística
   dependen de la jurisdicción y decisión actual: no son bloqueantes universales.
4. **No copiar features.** Cada feature candidata responde: ¿qué problema
   resuelve, para quién, con qué frecuencia, con qué costo operativo?
   Explícitamente: table stakes, diferenciadores y **anti-features**.
5. **Secuencial, local.** Una investigación = una carpeta en
   `output/<slug>/` (no versionada), con subcarpetas por etapa.
   Sin borrar desacuerdos: el historial adversarial se conserva en disco.
6. **Los protocolos no generan código.** Fase 1 termina en Product Brief,
   Fase 2 en Technical Discovery. Sin backlog, sin estimaciones, sin tickets.

## Convenciones

- `market` en [`templates/run.yaml`](templates/run.yaml) es la configuración
  canónica: obligatorio, elegido por el usuario en runtime y sin default
  Argentina/LatAm. Si falta o contradice el pedido/brief, preguntar y detener
  el research hasta resolverlo; un placeholder no es un mercado definido.
- Nuevas corridas usan `LITE_TARGET_MARKET.md`, `04_TARGET_MARKET.md` y
  `scope.target_market_research`. Corridas antiguas quedan sin cambios ni
  renombres; al retomarlas registrar sus rutas exactas en `run.yaml` (`notes`).
  `argentina_research` es solo metadata histórica, no una opción nueva.
- Una corrida = `output/<slug>/` + `run.yaml`. Los outputs no se versionan;
  lo que se commitea son mejoras al kit (protocolos, templates, docs).
- Commits del kit en español o inglés, prefijados por etapa, ej:
  `protocol(lite): add saturation rule`,
  `templates: add run-lite request`.
- `UNRESOLVED` valiosos → preguntas visibles de validación. En Lite bloquean
  o escalan solo si son indispensables para la decisión actual.
- Snippets son pistas, no lectura ni prueba de demanda. Una página oficial
  leída prueba lo anunciado, no un MVP. Claims materiales citan pasajes
  inspeccionados con URL, fecha, alcance/jurisdicción y límites.

## Skill: usar el kit desde otros proyectos

[`researcher`](skills/researcher/SKILL.md) es el router: el agente lee los
protocolos del kit y guarda la investigación en **el proyecto donde estás
trabajando**, no en el kit externo. El camino habitual es instalarlo una vez,
abrir el proyecto consumidor y pedir una investigación con mercado explícito.

### 1. Instalar desde un checkout local autorizado

Necesitás un checkout del kit ya disponible y permisos para leerlo y para
escribir en el directorio de skills. Desde la raíz de ese checkout, ejecutá
manualmente lo siguiente **solo si el destino `researcher` no existe**:

```bash
KIT="$(pwd -P)"
SKILLS_DIR="${SKILLS_DIR:-$HOME/.agents/skills}"
mkdir -p "$SKILLS_DIR"
ln -s "$KIT/skills/researcher" "$SKILLS_DIR/researcher"
```

`$HOME/.agents/skills` es la ubicación del ejemplo, no una convención
universal: elegí `SKILLS_DIR` según la documentación de tu agente. El symlink
permite localizar el kit por la ruta real de `SKILL.md` y sigue los cambios
del checkout; no fija una versión. No se clona ni instala automáticamente.

Si preferís **copiar** el skill, seguí la alternativa de
[INSTALL.md](skills/researcher/INSTALL.md), no ambas modalidades. La copia
incluye el router y sus referencias, no los protocolos. Para localizar el kit,
podés declarar en el entorno desde el que iniciás el agente:

```bash
export RESEARCHER_KIT="/ruta/absoluta/al/checkout/autorizado/researcher"
```

Reemplazá esa ruta por la real. `RESEARCHER_KIT` explícito tiene prioridad;
sin él, una copia requiere selección humana de un kit autorizado. Copiar el
skill no lo actualiza con el checkout ni fija la versión de los protocolos.
Para reproducibilidad y elección de versión, consultá la
[instalación portable](skills/researcher/INSTALL.md).

### 2. Activarlo en el proyecto y confirmar los permisos

Abrí el proyecto consumidor con tu agente y comprobá, mediante su mecanismo
de descubrimiento, que `researcher` está disponible. Pedí «Usá el skill
researcher…» como en los ejemplos de abajo. No hay un comando slash universal:
si tu agente no descubre ese directorio, configurá su ubicación según su propia
documentación o indicá explícitamente el `SKILL.md` autorizado para que lo lea.

Antes de investigar, confirmá con el agente:

- **Kit y acceso:** autorizá la lectura de la ruta concreta del kit si está
  fuera del workspace. Un symlink o `RESEARCHER_KIT` localiza archivos, pero
  no concede permisos. Sin acceso, detenerse o elegir un kit ya autorizado.
- **Procedencia:** verificar los archivos y referencias de la etapa según
  [resolución/permisos](skills/researcher/references/kit.md). Registrar ruta
  real, commit y `dirty`; si no se pueden observar, `null` y motivo
  `unavailable`. Un commit con cambios locales no reproduce todo lo usado.
- **Destino:** elegir la raíz Git autorizada del proyecto y un slug nuevo
  (minúsculas, números y guiones, sin `/` ni `..`). No escribir en el kit
  externo ni sobrescribir una corrida existente.

El [preflight de output](skills/researcher/references/output-guard.md) es
obligatorio **antes de cualquier artefacto, incluso `run.yaml`**: verificar
raíz Git, revisar todo lo rastreado bajo `output/` y comprobar por separado
la exclusión de cada destino previsto, incluidas fuentes y capturas.
Sin Git, permisos o exclusión verificada, detenerse. Si hay research ya
rastreado, reportar sus rutas exactas; `.gitignore` no lo desrastrea.
Las únicas excepciones posibles son los metadatos conocidos del kit indicados
en el guard, no cualquier archivo llamado README. Si falta exclusión, pedir
autorización para corregir el `.gitignore` del proyecto y repetir el preflight;
no borrar, desrastrear ni cambiar configuración global automáticamente.

### 3. Elegir la etapa y copiar un pedido

| Lo que necesitás ahora | Etapa |
|---|---|
| Explorar opciones y decidir qué validar | Lite equilibrado, punto de partida habitual |
| Investigar una apuesta y construir un Product Brief completo | Fase 1 |
| Convertir un Product Brief validado por una persona en discovery técnico | Fase 2 |

El **objetivo** no es la etapa: podés explorar, contrastar una idea o apoyar
una decisión concreta. Si no queda una decisión material abierta, el agente
puede empezar por Lite equilibrado sin preguntar por la etapa. El **mercado
siempre lo elegís vos**; si falta o contradice el pedido, debe preguntar y
esperar antes de investigar. Chile es solo el mercado de los ejemplos,
no un default: reemplazalo junto con el rubro, slug y contexto por tu caso.

En estos pedidos, autorizá solo ubicaciones a las que realmente puedas dar
acceso. Los modelos son parámetros del runtime/usuario: completá las
selecciones pendientes antes de ejecutar Fases 1/2. Una preferencia declarada
no prueba ejecución; registrar el modelo observado o «no medido», nunca
simular que se ejecutó otro modelo.

**Lite — explorar antes de comprometer una apuesta:**

```text
Usá el skill researcher en este proyecto consumidor.
Etapa: Lite equilibrado. Rubro: gestión de turnos para talleres de bicicletas.
Objetivo: explorar opciones. Decisión actual: qué problema validar primero
con talleres independientes; no decidir todavía un MVP ni un stack.
Mercado elegido por mí: Chile, con foco inicial en Santiago.
Slug nuevo: turnos-talleres-chile.
Modelo: el configurado en este runtime; uno solo, sin adversarial.
Acordemos un tope dentro de 6–8 consultas variadas y 4–6 lecturas, sin cuotas.
Autorizo leer el checkout del kit y escribir outputs locales en este proyecto
solo después de verificar rutas, permisos y el preflight Git de output.
Si falta algún permiso concreto, pedímelo y esperá antes de investigar/escribir.
Seguí el protocolo Lite y templates/run-lite.md del kit resuelto.
Entregá opciones, incertidumbres y siguiente validación; no escales de etapa
sin acordarlo conmigo. Registrá telemetría observada o null/no medido.
```

Lite deja cinco `LITE_*.md` en `output/<slug>/lite/`, incluido el brief de una
página. **No valida un MVP ni habilita automáticamente Fase 2.** Detalles y
presupuestos: [plantilla Lite](templates/run-lite.md).

**Fase 1 — construir el Product Brief:**

```text
Usá el skill researcher en este proyecto consumidor. Etapa: Fase 1.
Rubro: gestión de turnos para talleres de bicicletas independientes.
Mercado elegido por mí: Chile, con foco inicial en Santiago.
Objetivo: contrastar la apuesta de reducir ausencias y trabajo administrativo.
Contexto: no hay stack decidido; dejá fuera cadenas con sistemas propios.
Slug nuevo: turnos-talleres-brief-chile.
ORCHESTRATOR_MODEL: <modelo elegido del runtime/usuario>
ADVERSARIAL_MODEL: <modelo elegido del runtime/usuario>
Seguí templates/run-research.md y el protocolo de Fase 1 del kit resuelto,
incluido el ciclo adversarial. Si no podés ejecutar un modelo, informalo.
Autorizo leer el kit y escribir outputs locales en este proyecto solo tras
resolver los permisos concretos y pasar el preflight Git de output.
Si hay ambigüedad material o conflicto de mercado, preguntá y esperá.
Entregá el Product Brief, ledger final y reporte en output/<slug>/brief/.
No inicies Fase 2: primero voy a revisar y validar el brief y su mercado.
```

Consultá la [plantilla de Fase 1](templates/run-research.md) para ampliar
alcance, restricciones y preguntas. La salida esperada incluye
`09_PRODUCT_BRIEF.md`, `CLAIM_LEDGER_FINAL.md` y `FINAL_REPORT.md`.

**Fase 2 — solo después de la validación humana:**

El siguiente pedido presupone que revisaste y validaste realmente el brief.
No lo copies como declaración de validación si esa revisión no ocurrió.

```text
Usá el skill researcher en este proyecto consumidor. Etapa: Fase 2.
Validé como responsable humano el Product Brief y su mercado: Chile,
con foco inicial en Santiago. Registrá el alcance de esta validación.
PRODUCT_BRIEF: output/turnos-talleres-brief-chile/brief/09_PRODUCT_BRIEF.md
CLAIM_LEDGER_FINAL: output/turnos-talleres-brief-chile/brief/CLAIM_LEDGER_FINAL.md
ORCHESTRATOR_MODEL: <modelo elegido del runtime/usuario>
ADVERSARIAL_MODEL: <modelo elegido del runtime/usuario>
Seguí templates/run-discovery.md y el protocolo de Fase 2 del kit resuelto.
Heredá el mercado del brief en market de run.yaml. Si falta, hay conflicto
o propongo cambiarlo, detenete hasta la revalidación humana del brief.
Autorizo leer el kit y estos inputs locales. Antes de cualquier escritura,
resolvé permisos y repetí el preflight para todos los destinos nuevos.
Conservá los artefactos previos y no sobrescribas outputs existentes.
Entregá FINAL_TECHNICAL_DISCOVERY.md y TECH_DECISION_LEDGER_FINAL.md en
output/turnos-talleres-brief-chile/discovery/.
No generes código, backlog ni ADRs definitivos; no simules modelos ejecutados.
```

Más restricciones e inputs opcionales en la
[plantilla de Fase 2](templates/run-discovery.md).

### 4. Revisar la entrega y decidir el siguiente paso

Después del guard, la corrida guarda `run.yaml` y sus artefactos en
`<proyecto-consumidor>/output/<slug>/`, con subcarpetas `lite/`, `brief/` o
`discovery/`. Son outputs locales, no contenido para publicar en Git; la
exclusión no los vuelve privados: no guardar secretos ni datos personales
innecesarios. Al retomar una corrida, conservar sus rutas históricas y
registrarlas en `run.yaml` (`notes`), sin renombrarlas.

Pedile al agente objetivo, mercado/jurisdicciones, etapa, perfil/presupuesto,
procedencia del kit, modelos observados, rutas y límites/`UNRESOLVED`.
Usá Lite para elegir la siguiente validación o acordar Fase 1 si corresponde;
solo un Product Brief genuinamente validado por una persona permite Fase 2.
El recorrido completo está en [PIPELINE.md](docs/PIPELINE.md); la convención
de carpetas, en [output/README.md](output/README.md).

## Para quién es esto

Equipos internos que inician un producto web fullstack y quieren una base
de decisiones trazable antes de diseñar arquitectura o estimar. Si solo
necesitás inspiración rápida, el **modo Lite** (`protocols/00-lite/`)
deja opciones y un brief de 1 página con presupuesto acotado propuesto,
sin prometer ahorros medidos.
