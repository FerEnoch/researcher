# Instalar el skill researcher

El skill es un acceso directo al kit: vive en este repo para viajar con
él a GitHub, pero el agente lo descubre desde tu carpeta global de skills.

```bash
# Opción A — symlink (recomendada: sigue las actualizaciones del repo)
ln -s /home/ferenoch/code/active/researcher/skills/researcher ~/.agents/skills/researcher

# Opción B — copiar (fija una versión)
cp -r /home/ferenoch/code/active/researcher/skills/researcher ~/.agents/skills/researcher
```

Luego, opcional:

```bash
# Fija dónde vive el kit para no declararlo en cada corrida
export RESEARCHER_KIT=/home/ferenoch/code/active/researcher
```

Verificación: pedí "investigá el rubro X en modo Lite" en cualquier
proyecto; el agente debe activar el skill y escribir en
`<ese-proyecto>/output/<slug>/`, nunca dentro del kit.
