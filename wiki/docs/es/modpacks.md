# Modpacks y datapacks

QuestMod no depende de que un admin ponga un NPC. Un modpack puede traer sus misiones ya hechas y los jugadores usarlas desde el libro de misiones.

## Libro de misiones

- **Tecla K** (cambiable) o el ítem `questmod:quest_book` (clic derecho). Abre el mismo panel **sin NPC** y muestra las misiones con acceso *libro* o *NPC y libro*.
- **Libro de bienvenida:** se entrega al entrar según `giveBook` en la config del servidor (`FIRST_JOIN`, `IF_MISSING` o `NEVER`).
- **Apagarlo:** `bookEnabled = false` en la config del servidor.
- **Hacerlo crafteable:** el mod no trae receta. Añade una con un datapack, por ejemplo `data/mipack/recipes/quest_book.json`:

```json
{
  "type": "minecraft:crafting_shapeless",
  "ingredients": [ { "item": "minecraft:book" }, { "item": "minecraft:feather" } ],
  "result": { "item": "questmod:quest_book" }
}
```

## Misiones en JSON

Archivos `data/<namespace>/questmod/quests/<nombre>.json`. Se cargan solos al iniciar el mundo y con `/reload`, y en el juego son de **solo lectura**. El ID de la misión es `namespace:nombre` y otras misiones pueden usarlo en `requires`.

```json
{
  "name": "Cazador de zombis",
  "description": "Elimina zombis y come algo para recuperar fuerzas.",
  "icon": "minecraft:iron_sword",
  "access": "both",
  "section": "mipack:combate",
  "objectives": [
    { "type": "kill", "target": "minecraft:zombie", "count": 20 },
    { "type": "eat", "target": "#minecraft:foods", "count": 5 }
  ],
  "milestones": [
    { "percent": 50, "rewards": [ { "item": "minecraft:bread", "count": 8 } ], "xp": 20 }
  ],
  "rewards": [
    { "item": "minecraft:diamond", "count": 3 },
    { "item": "minecraft:golden_apple", "count": 2 }
  ],
  "xp": 50,
  "show_reward": true
}
```

### Campos

| Campo | Tipo | Descripción |
|---|---|---|
| `name` | texto | Nombre. Si empieza con `$`, el resto es una clave de idioma |
| `description` | texto | Descripción (también acepta `$clave`) |
| `icon` | ID de ítem | Ícono de la lista |
| `access` | `npc` · `book` · `both` | Desde dónde se ofrece (por defecto `npc`) |
| `section` | ID | Sección a la que pertenece |
| `scope` | `individual` · `community` | Progreso individual o contador global |
| `min_contribution` | entero | Solo comunitarias: aporte mínimo para reclamar |
| `auto_accept` | booleano | Se acepta sola. En comunitarias significa "unirse sola" |
| `auto_claim` | booleano | Se reclama sola (no aplica a comunitarias) |
| `requires` | lista de IDs | Misiones que deben estar reclamadas (no aplica a comunitarias) |
| `objectives` | lista (1 a 6) | Cada uno con `type`, `target` y `count` |
| `rewards` | lista (hasta 6) | Cada uno con `item`, `count` y `nbt` opcional (SNBT) |
| `milestones` | lista (hasta 6) | Cada uno con `percent` (1 a 99), `rewards` y `xp` |
| `xp` | entero | Experiencia del premio final |
| `show_reward` | booleano | Si es `false`, el jugador ve `???` |

Tipos de objetivo: `kill`, `break`, `eat`, `craft`, `smelt`, `deliver`. El `target` es un ID o un `#tag` de cualquier mod.

!!! tip "Autocompletado en VS Code"
    En la wiki hay esquemas JSON ([misión](../schemas/quest.schema.json) y [sección](../schemas/section.schema.json)). Asócialos a `data/*/questmod/quests/*.json` y `data/*/questmod/sections/*.json` para tener autocompletado y validación.

Los archivos inválidos no rompen nada: se omiten y el motivo queda en el log.

## Secciones en JSON

Archivos `data/<namespace>/questmod/sections/<nombre>.json`:

```json
{ "name": "Create", "icon": "create:cogwheel", "order": 10 }
```

`icon` puede ser un ítem o una imagen (`mipack:textures/gui/seccion/create.png`). Las misiones usan el ID de la sección en su campo `section`.

## Crear en el juego y repartir como datapack

Arma las misiones con el editor del juego y ejecuta:

```
/questmod export <namespace>
```

Se genera `questmod_export/<namespace>/` (con `pack.mcmeta`) con las misiones y secciones listas para meter en los datapacks del modpack. Después **borra las misiones del mundo** para no tenerlas duplicadas.

## Configuración del servidor

En `serverconfig/questmod-server.toml` de cada mundo. Para fijar valores en un modpack, ponlos en `defaultconfigs/questmod-server.toml`.

| Opción | Por defecto | Qué hace |
|---|---|---|
| `adminPermissionLevel` | 2 | Nivel de op necesario para administrar |
| `singleplayerOwnerIsAdmin` | `true` | En solitario, el dueño es admin aunque no tenga cheats |
| `bookEnabled` | `true` | Activa el libro de misiones |
| `giveBook` | `FIRST_JOIN` | Cuándo se entrega el libro al entrar: `NEVER`, `FIRST_JOIN`, `IF_MISSING` |

## Comandos

Para admins. Ver [Referencia](reference.md#comandos).
