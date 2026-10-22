# NPCs

The **Quest Master** is a motionless, invulnerable NPC that looks at players. Right-click opens its panel; **shift + right-click** (as an admin) opens its editor.

## Appearance

| Mode | What it does |
|---|---|
| Default | The mod's original skin |
| Player skin | Downloads a premium player's skin by name (the *Me* button uses yours) |
| Skin from link | A skin PNG (64x64 or 64x32) from an **https** link |
| Resource pack texture | A skin texture shipped in a resource pack or mod (`modid:textures/...png`) |
| Mob / model from another mod | The NPC is drawn with that mob's real model, from **any** installed mod. The NBT picks the variant |
| Item / 3D model | A floating item. With the NBT `{CustomModelData:N}` and a resource pack you can show **any 3D model** in JSON |

You can also set a **visible name**, a **scale** (0.1 to 8, which also changes the hitbox) and **slim arms** for link or texture skins.

### NBT examples

- Librarian villager: `{VillagerData:{profession:"minecraft:librarian",type:"minecraft:plains",level:1}}`
- Item with a custom model: `{CustomModelData:1}`

To pick the mob or item, use the **little box** next to the field: it opens the picker (inventory or the whole registry). From the inventory the NBT is copied too.

!!! warning "If something fails"
    If a mob's mod isn't on a client, or the model throws an error, that client sees the default skin instead of a crash. The mob's mod must be installed on the server and on the clients.

!!! note "Privacy"
    Link skins are downloaded on the client and expose its IP to the link's owner. Each player can disable them with `npc.allowUrlSkins` in `questmod-client.toml`.

## Which quests it offers

In the **Quests** tab of the NPC editor:

- **All** (default): offers every quest on the server, including ones you create later.
- **Only the chosen ones:** tick single quests or **whole sections**. New quests you create from that NPC's panel are added automatically.

Quests live in a common pool: several NPCs can offer the same ones, and a player's progress is the same on all of them.

## Quest scroll

To copy one NPC's quest list to another (admins only):

| Action | Result |
|---|---|
| Right-click an NPC with an **empty** scroll | Copies its list |
| Right-click another NPC with a **loaded** scroll | Pastes the list (works for several NPCs) |
| Shift + right-click an NPC | Copies again (overwrites) |
| Shift + right-click in the air | Empties the scroll |

What is pasted are references to the **same** quests, not copies: if you edit one, it changes on every NPC that offers it. The scroll copies sections too.

## "!" marker

Above each NPC a red **!** appears if there are new quests for you and a **gold** one if there are rewards to claim. It only counts that NPC's quests. It can be turned off with `npc.showNpcMarker`, and the textures (`npc_marker_new.png` and `npc_marker_claim.png`) can be replaced with a resource pack.

## Deleting an NPC

In its editor, the red **Delete NPC** button asks for a second press to confirm. `/kill` works too.
