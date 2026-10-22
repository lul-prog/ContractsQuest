# Wiki de QuestMod / QuestMod wiki

Documentación en Markdown, bilingüe (`docs/es` y `docs/en`), publicada con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Verla en local

```bash
pip install mkdocs-material "mkdocs-static-i18n>=1.0"
cd wiki
mkdocs serve
```

Abre http://127.0.0.1:8000. (El plugin `mkdocs-static-i18n` debe ser la versión 1.0 o superior, que usa la lista `languages:` de `mkdocs.yml`.)

## Publicarla (GitHub Pages)

El workflow `.github/workflows/docs.yml` publica la wiki en cada cambio de la rama `main`. En GitHub: *Settings → Pages → Source: Deploy from a branch → rama `gh-pages`*. Después pon la dirección en `site_url` y `repo_url` de `mkdocs.yml`, y enlázala en la página del mod en CurseForge.

## Mantenerla

- Cada página existe en `docs/es/` y `docs/en/` con **el mismo nombre de archivo**. Si cambias una, cambia la otra.
- La sección *Referencia → Tema* se generó leyendo `QuestTheme.java`: si añades colores o medidas, vuelve a generarla (o edítala a mano).
- `docs/schemas/*.json` son esquemas JSON de los datapacks. En VS Code, asócialos a `data/*/questmod/quests/*.json` y `.../sections/*.json` para tener autocompletado y validación.
