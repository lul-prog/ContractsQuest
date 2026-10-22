# Languages

All of the mod's texts (screens, server messages, items, keys) are **translation keys** in `assets/questmod/lang/`.

## Included languages

English (`en_us`) and Spanish (`es_mx`, `es_es`, `es_ar`, `es_cl`, `es_uy`, `es_ve`). Each player sees the mod in **their** language even if the server is in another: server messages travel as keys and each client translates them. Languages without a translation fall back to English.

## Adding a language

1. Copy `en_us.json` to `assets/questmod/lang/<code>.json` (for example `pt_br.json` or `fr_fr.json`), inside the mod or a resource pack.
2. Translate the values. Don't change the keys.
3. Keep placeholders such as `%s`, `%d` and `%1$s` in place.

!!! warning "Percent signs"
    In texts with formatting, a literal `%` is written `%%` (for example `"Total progress: %d%%"`).

## Changing a text without touching the mod

Put a language file in a resource pack with **only the keys you want to rewrite**. It applies on top of the original.

## Translating datapack quests

In the `name` or `description` of a quest or section, a value starting with `$` is a language key. This way the modpack can ship its quests translated:

```json
{ "name": "$mypack.quest.zombies.name", "description": "$mypack.quest.zombies.desc", "objectives": [ ... ] }
```

And in `assets/mypack/lang/en_us.json`:

```json
{ "mypack.quest.zombies.name": "Zombie hunter" }
```

If the key doesn't exist, the text is shown as is.
