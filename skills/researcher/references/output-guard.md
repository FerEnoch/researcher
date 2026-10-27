# Preflight obligatorio antes de cualquier artefacto

Aplica a Lite, Fase 1 y Fase 2, incluso si se invocan sin el skill.
`PROJECT` es la raíz Git del proyecto consumidor elegida y autorizada;
`SLUG` es un nombre nuevo en minúsculas, números y guiones, sin `/` ni `..`.
No escribir todavía directorios de corrida, fuentes, notas ni `run.yaml`.

## 1. Verificar destino y contenido ya rastreado

```bash
git -C "$PROJECT" rev-parse --show-toplevel
git -C "$PROJECT" rev-parse --is-inside-work-tree
git -C "$PROJECT" ls-files -- output/
```

Si falla un comando, no hay worktree Git, o la raíz real no coincide con
`PROJECT`, **STOP sin artefactos**. Resolver permisos antes de continuar.
Inspeccionar la lista completa (usar `ls-files -z` si hay nombres inusuales).
Solo se exceptúan exactamente `output/README.md` y `output/.gitkeep` si
son metadatos conocidos del kit, sin contenido de corrida. El nombre por
sí solo no basta: research dentro de un README también se reporta.
Cualquier otra ruta rastreada bajo `output/` exige
**STOP y reporte de sus rutas exactas**, aunque ya exista una regla ignore.
Nunca ejecutar `git rm`, desrastrear ni borrar contenido automáticamente.

## 2. Comprobar cada destino planificado

Ejemplo de probes sin crear archivos; completar con **todos** los destinos
reales previstos, incluidas capturas/fuentes de cada etapa. Nuevas corridas
usan `LITE_TARGET_MARKET.md` y `04_TARGET_MARKET.md`. Al retomar corridas
históricas, no renombrar archivos: registrar y comprobar sus rutas exactas
conservadas (también en `run.yaml`, `notes`), no solo estos probes neutrales:

```bash
for path in \
  "output/$SLUG/run.yaml" \
  "output/$SLUG/lite/LITE_DOMAIN.md" \
  "output/$SLUG/lite/LITE_BENCHMARK.md" \
  "output/$SLUG/lite/LITE_TARGET_MARKET.md" \
  "output/$SLUG/lite/LITE_LEDGER.md" \
  "output/$SLUG/lite/LITE_BRIEF.md" \
  "output/$SLUG/brief/04_TARGET_MARKET.md" \
  "output/$SLUG/brief/09_PRODUCT_BRIEF.md" \
  "output/$SLUG/discovery/FINAL_TECHNICAL_DISCOVERY.md" \
  "output/$SLUG/sources/probe.txt" \
  "output/$SLUG/lite/sources/probe.txt" \
  "output/$SLUG/brief/sources/probe.txt" \
  "output/$SLUG/discovery/sources/probe.txt"
do
  git -C "$PROJECT" check-ignore -q -- "$path" || {
    printf 'STOP: destino no excluido o error Git: %s\n' "$path"
    exit 1
  }
done
```

Ejecutar el bloque en un shell acotado; `exit 1` detiene el preflight, no
es permiso para seguir con la corrida. Para diagnóstico, usar
`git -C "$PROJECT" check-ignore -v -- "output/$SLUG/run.yaml"`.
Un único `check-ignore` con múltiples rutas no basta: su éxito puede
significar que solo una quedó excluida. La comprobación no escribe probes.

## 3. Corregir solo con autorización y volver a verificar

Si falta exclusión y está autorizada la edición del `.gitignore` de ese
proyecto, añadir **solo si hace falta** la regla anclada `/output/*`.
Conservar reglas ajenas y las excepciones de metadatos del kit:
`!/output/README.md` y `!/output/.gitkeep`, cuando correspondan.
No editar `.git/info/exclude`, configuración global ni otros repositorios.
Si no hay permiso, pedirlo y detenerse. No sobrescribir un output existente.

Repetir los pasos 1 y 2 **antes de crear `run.yaml`**. Si una negación u
otra regla impide excluir los destinos, STOP y reportar; no forzar escrituras.
Repetir para destinos nuevos o al retomar una corrida. Un ignore no vuelve
privados los datos ni evita un `git add -f`: no guardar secretos ni datos
personales innecesarios. Los outputs siguen siendo archivos locales.
