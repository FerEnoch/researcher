# Instalar el skill researcher

El skill enruta al kit; no lo copia ni concede acceso a otros workspaces.
Ejecutar estos comandos manualmente solo con permisos para ambas ubicaciones.
No hay clonación ni instalación automática.

## Elegir versión y modalidad

Partir de un checkout local ya autorizado. Desde su raíz:

```bash
KIT="$(pwd -P)"
SKILLS_DIR="${SKILLS_DIR:-$HOME/.agents/skills}"
# Elegir UNA opción; el destino researcher no debe existir.
mkdir -p "$SKILLS_DIR"
ln -s "$KIT/skills/researcher" "$SKILLS_DIR/researcher"  # symlink
# Alternativa al symlink:
# cp -R "$KIT/skills/researcher" "$SKILLS_DIR/researcher"
export RESEARCHER_KIT="$KIT"
```

| Modalidad | Resolución y actualizaciones |
|---|---|
| Symlink | La ruta real del SKILL.md permite localizar el kit. Sigue los cambios del checkout, no fija versión. |
| Copia | Copia solo el router y referencias; necesita `RESEARCHER_KIT` o selección del kit. No se actualiza con el checkout. |

Para reproducibilidad, usar un checkout limpio de un commit elegido y
registrar `git rev-parse HEAD` más `git status --porcelain=v1`.
Al preparar manualmente ese checkout puede usarse
`git switch --detach <commit-elegido>` solo si no hay cambios que preservar;
no se prescribe ningún commit ni remoto. Seguir una rama móvil cambia el
kit usado. Copiar solo el skill tampoco fija los protocolos del kit externo.

## Verificar sin ejecutar research

Seguir [resolución y procedencia](references/kit.md): validar protocolo,
plantilla y permisos de lectura. Confirmar que el destino de artefactos es
el proyecto consumidor, no el kit externo. Antes de **cualquier** escritura,
seguir [preflight Git de output](references/output-guard.md); la existencia
del skill o de `RESEARCHER_KIT` no autoriza cambios en otros repositorios.
