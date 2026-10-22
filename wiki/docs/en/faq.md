# FAQ

??? question "I can't edit anything in my singleplayer world"
    In a singleplayer world the owner is an admin **if** `singleplayerOwnerIsAdmin` is `true` (the default). A modpack may have set it to `false` in `defaultconfigs/questmod-server.toml`. Change it in your world's `serverconfig/questmod-server.toml`, or enable cheats.

??? question "I can't see the quest book / the K key does nothing"
    Check `bookEnabled` and `giveBook` in the server config. Also, the book only shows quests with *Book only* or *NPC and book* access: an *NPC only* quest doesn't appear.

??? question "My quest doesn't advance"
    - If the target doesn't exist on the server (a mod is missing or the ID/tag is misspelled), you got a warning in chat when saving and that objective **won't advance**.
    - You must have **accepted** the quest (in community quests, **joined**).
    - Actions by `FakePlayer`s and anything a protection mod cancels don't count. See [Compatibility](compatibility.md).

??? question "The Accept or Claim button does nothing"
    With an NPC you must be **within 10 blocks** and that NPC must offer the quest (check its *Quests* tab). A *Locked* quest asks you to complete its requirements first.

??? question "A community quest doesn't add up"
    Only what you do **after joining** counts. Press **Join** in the panel.

??? question "An NPC shows the default skin"
    The mob's mod may not be on your client, the model may have failed, or link skins may be disabled (`npc.allowUrlSkins`). A player skin takes a moment to download.

??? question "My datapack quest doesn't show up"
    Check the log: invalid files are skipped and the reason is given. Run `/reload` after changing files and check the path `data/<ns>/questmod/quests/`. Datapack quests are read-only in game.

??? question "My theme textures aren't applied"
    Reload with **F3 + T**, check that the resource pack is active and that `theme.json` is in `assets/questmod/`. If an image is missing or the JSON is wrong, the log says so and the usual color is used.

??? question "How do I reset a player's progress?"
    `/questmod reset <player>` for everything, or `/questmod reset <player> <quest>` for one. To repeat a community quest for everyone: `/questmod community reset <quest>`.

??? question "What happens to my quests when updating?"
    They are migrated automatically. Old quests stay as *NPC only*, and existing NPCs keep offering everything. Update client and server at the same time.
