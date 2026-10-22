# Modpacks and datapacks

QuestMod doesn't depend on an admin placing an NPC. A modpack can ship its quests ready-made and players can use them from the quest book.

## Quest book

- **K key** (rebindable) or the `questmod:quest_book` item (right-click). It opens the same panel **without an NPC** and shows quests with *book* or *NPC and book* access.
- **Welcome book:** given on join according to `giveBook` in the server config (`FIRST_JOIN`, `IF_MISSING` or `NEVER`).
- **Turning it off:** `bookEnabled = false` in the server config.
- **Making it craftable:** the mod ships no recipe. Add one with a datapack, for example `data/mypack/recipes/quest_book.json`:

```json
{
  "type": "minecraft:crafting_shapeless",
  "ingredients": [ { "item": "minecraft:book" }, { "item": "minecraft:feather" } ],
  "result": { "item": "questmod:quest_book" }
}
```

## Quests in JSON

Files `data/<namespace>/questmod/quests/<name>.json`. They load on their own when the world starts and with `/reload`, and are **read-only** in game. The quest ID is `namespace:name` and other quests can use it in `requires`.

```json
{
  "name": "Zombie hunter",
  "description": "Kill zombies and eat something to recover.",
  "icon": "minecraft:iron_sword",
  "access": "both",
  "section": "mypack:combat",
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

### Fields

| Field | Type | Description |
|---|---|---|
| `name` | text | Name. If it starts with `$`, the rest is a language key |
| `description` | text | Description (also accepts `$key`) |
| `icon` | item ID | List icon |
| `access` | `npc` · `book` · `both` | Where it is offered from (default `npc`) |
| `section` | ID | Section it belongs to |
| `scope` | `individual` · `community` | Individual progress or a global counter |
| `min_contribution` | integer | Community only: minimum contribution to claim |
| `auto_accept` | boolean | Accepted automatically. In community quests it means "auto-join" |
| `auto_claim` | boolean | Claimed automatically (doesn't apply to community quests) |
| `requires` | list of IDs | Quests that must be claimed first (doesn't apply to community quests) |
| `objectives` | list (1 to 6) | Each with `type`, `target` and `count` |
| `rewards` | list (up to 6) | Each with `item`, `count` and optional `nbt` (SNBT) |
| `milestones` | list (up to 6) | Each with `percent` (1 to 99), `rewards` and `xp` |
| `xp` | integer | Experience of the final reward |
| `show_reward` | boolean | If `false`, the player sees `???` |

Objective types: `kill`, `break`, `eat`, `craft`, `smelt`, `deliver`. The `target` is an ID or a `#tag` from any mod.

!!! tip "Autocomplete in VS Code"
    The wiki ships JSON schemas ([quest](../schemas/quest.schema.json) and [section](../schemas/section.schema.json)). Associate them with `data/*/questmod/quests/*.json` and `data/*/questmod/sections/*.json` to get autocomplete and validation.

Invalid files don't break anything: they are skipped and the reason is written to the log.

## Sections in JSON

Files `data/<namespace>/questmod/sections/<name>.json`:

```json
{ "name": "Create", "icon": "create:cogwheel", "order": 10 }
```

`icon` can be an item or an image (`mypack:textures/gui/section/create.png`). Quests use the section's ID in their `section` field.

## Create in game, ship as a datapack

Build the quests with the in-game editor and run:

```
/questmod export <namespace>
```

This generates `questmod_export/<namespace>/` (with `pack.mcmeta`) with the quests and sections ready to drop into the modpack's datapacks. Afterwards, **delete the quests from the world** so you don't have them duplicated.

## Server configuration

In each world's `serverconfig/questmod-server.toml`. To set values in a modpack, put them in `defaultconfigs/questmod-server.toml`.

| Option | Default | What it does |
|---|---|---|
| `adminPermissionLevel` | 2 | Op level needed to manage |
| `singleplayerOwnerIsAdmin` | `true` | In singleplayer, the owner is an admin even without cheats |
| `bookEnabled` | `true` | Enables the quest book |
| `giveBook` | `FIRST_JOIN` | When the book is given on join: `NEVER`, `FIRST_JOIN`, `IF_MISSING` |

## Commands

For admins. See [Reference](reference.md#commands).
