# Idiomas

Todos los textos del mod (pantallas, mensajes del servidor, ítems, teclas) son **claves de traducción** en `assets/questmod/lang/`.

## Idiomas incluidos

Inglés (`en_us`) y español (`es_mx`, `es_es`, `es_ar`, `es_cl`, `es_uy`, `es_ve`). Cada jugador ve el mod en **su** idioma, aunque el servidor esté en otro: los mensajes del servidor viajan como claves y los traduce cada cliente. Los idiomas sin traducción caen a inglés.

## Añadir un idioma

1. Copia `en_us.json` a `assets/questmod/lang/<codigo>.json` (por ejemplo `pt_br.json` o `fr_fr.json`), dentro del mod o de un resource pack.
2. Traduce los valores. No cambies las claves.
3. Mantén los marcadores como `%s`, `%d` y `%1$s` en su lugar.

!!! warning "Porcentajes"
    En los textos con formato, un `%` literal se escribe `%%` (por ejemplo `"Progreso total: %d%%"`).

## Cambiar un texto sin tocar el mod

Pon un archivo de idioma en un resource pack con **solo las claves que quieras reescribir**. Se aplica por encima del original.

## Traducir misiones de un datapack

En el `name` o la `description` de una misión o sección, un valor que empiece con `$` es una clave de idioma. Así el modpack puede traer sus misiones traducidas:

```json
{ "name": "$mipack.quest.zombis.name", "description": "$mipack.quest.zombis.desc", "objectives": [ ... ] }
```

Y en `assets/mipack/lang/es_es.json`:

```json
{ "mipack.quest.zombis.name": "Cazador de zombis" }
```

Si la clave no existe, se muestra el texto tal cual.
