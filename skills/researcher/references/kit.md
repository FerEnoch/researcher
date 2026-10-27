# Resolver el kit sin ampliar permisos

Un locator no autoriza lecturas fuera del workspace permitido por el host.
Si el kit está fuera, pedir acceso a esa ubicación concreta o elegir un kit
ya autorizado; detenerse hasta resolverlo. No leer credenciales ni `.env`.

## Localización y validación

1. Usar `RESEARCHER_KIT` si fue declarado explícitamente para la corrida.
2. En una instalación por symlink, resolver la ruta **real** del `SKILL.md`
   activado; desde `<kit>/skills/researcher/SKILL.md`, subir tres directorios.
   No usar el directorio de trabajo ni asumir una ruta del equipo del autor.
3. Una copia aislada del skill no contiene el kit: requiere `RESEARCHER_KIT`
   o selección humana de una ubicación autorizada. Si hay candidatos
   ambiguos, pedir elección; no inventar URL, descargar ni instalar nada.

En el kit seleccionado, comprobar que se pueden leer `docs/PIPELINE.md`,
`templates/run.yaml`, el protocolo y su plantilla de la etapa elegida:

| Etapa | Protocolo | Plantilla |
|---|---|---|
| Lite | `protocols/00-lite/LITE_PROTOCOL.md` | `templates/run-lite.md` |
| Fase 1 | `protocols/01-benchmarking/MASTER_PROTOCOL.md` | `templates/run-research.md` |
| Fase 2 | `protocols/02-tech-discovery/MASTER_PROTOCOL.md` | `templates/run-discovery.md` |

Resolver también las referencias exigidas por ese protocolo. Si falta un
archivo, detenerse y reportarlo; no sustituirlo con memoria del modelo.

## Procedencia (antes de escribir; guardar luego en run.yaml)

Si el kit es la raíz Git seleccionada, consultar:

```bash
git -C "$KIT" rev-parse --show-toplevel
git -C "$KIT" rev-parse --verify HEAD
git -C "$KIT" status --porcelain=v1
```

Registrar ruta real, commit exacto y `dirty: true/false` según status.
Comprobar que la raíz reportada sea el kit, no un repositorio padre.
Una copia sin Git registra commit/dirty `null` y motivo `unavailable`;
una versión solo se registra si existe evidencia explícita, nunca inventada.
Un commit con cambios locales no reproduce por sí solo el contenido usado.
Ver [instalación](../INSTALL.md) y [guard de output](output-guard.md).
