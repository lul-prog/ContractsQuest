# Compatibility

## With other mods

- **IDs from any mod.** Objectives accept mobs, blocks and items from any installed mod. The editor lists them (the picker's *All* tab) and warns in chat if the target doesn't exist on the server.
- **Tags.** A tag like `#forge:ores` counts whatever any mod puts in it, with no setup.
- **Mobs and models from other mods on NPCs.** The NPC is drawn with the mob's real renderer, so mods with their own models (for example GeckoLib) work too. If it fails, that client sees the default skin.
- **Items with 3D models.** With `CustomModelData` and a resource pack.

## What counts and what doesn't

| Type | Counts | Doesn't count |
|---|---|---|
| `kill` | Kills with weapons and projectiles/arrows fired by the player | Killing players. What a `FakePlayer` does (turrets, deployers) |
| `break` | Breaking blocks as a player | What machines from other mods break; breaking blocks a protection mod prevents |
| `eat` | Food and also drinks (potions, milk, mod drinks) | What another creature consumes |
| `craft` | Crafting at a table or crafting menus | Machines that don't use normal crafting |
| `smelt` | Taking the result out of a furnace | What hoppers or other automation move |
| `deliver` | Delivering with the panel button | Dropping items on the ground |

Actions by **fake players** (`FakePlayer`: deployers, turrets, quarries) don't add progress. Kill and break events are counted with low priority: if a protection (claims) mod cancels the action, it **doesn't count**.

## Client and server

The mod must be on **both sides** with the same version. Mods for the mobs, blocks or items you use in a quest must also be on both sides (otherwise the server or client won't recognize the ID).

## Existing worlds

When updating, earlier quests and progress are migrated automatically. Old quests keep *NPC only* access, and existing NPCs keep offering all quests.
