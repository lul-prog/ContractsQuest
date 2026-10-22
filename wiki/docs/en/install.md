# Installation

## Requirements

- Minecraft **1.20.1** with **Forge 47.2.0** or newer.
- Java 17.
- The mod must be installed on the **server and on every client**. If the versions don't match, the client can't join (the mod checks a network protocol version).

## Steps

1. Download the `.jar` from CurseForge.
2. Copy it into the `mods/` folder of the client and the server.
3. Start the game. The configuration files are created.

## Configuration files

| File | Where | What for |
|---|---|---|
| `config/questmod-client.toml` | Client | HUD, skin downloads and the NPC `!` marker |
| `serverconfig/questmod-server.toml` | Each world | Who is an admin, the quest book and the welcome book |
| `defaultconfigs/questmod-server.toml` | Server or modpack | Default server config values for new worlds |

The options are described in the [Reference](reference.md).

## Keys

| Key | Action |
|---|---|
| **K** | Opens the quest book (no NPC needed) |
| **G** | Shows or hides each quest's steps in the HUD |

They can be changed in *Options → Controls → QuestMod*.

## Updating from an earlier version

Quests and progress from earlier versions are read without problems: progress is migrated automatically the first time a player joins. Because the network protocol changes between versions, **update the mod on the server and on the clients at the same time**.
