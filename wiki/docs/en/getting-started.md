# Getting started

## For players

- **Opening quests:** right-click a Quest Master, or use the **K** key / the *Quest Book* item if the server allows it.
- **The panel:** the quest list is on the left and the details on the right. Tabs separate *Available*, *In progress* and *Done*. If there are sections, they appear as icons on the left.
- **Accept, deliver and claim:** press **Accept** on an available quest. When you meet its objectives, **Claim!** appears and you get the rewards. Some quests ask you to **Deliver** items to the NPC. To accept, deliver or claim with an NPC you must be within 10 blocks of it.
- **HUD:** accepted quests are shown on a side of the screen. Press **G** to expand each step separately.
- **Marker:** above an NPC, a red **!** means new quests and a **gold** one means rewards to claim.

!!! tip "Community quests"
    A community quest has a counter shared by the whole server. Press **Join** to take part: only what you do after joining counts.

## For admins

### 1. Get an NPC
Use the *Quest Master* egg (creative Tools tab) or `/summon questmod:quest_npc`.

### 2. Configure it
**Shift + right-click** the NPC (as an admin) opens its editor, with two tabs:

- **Appearance:** name, skin, model of another mob or item, scale. See [NPCs](npcs.md).
- **Quests:** which quests it offers (all of them, or only the ones you pick).

### 3. Create a quest
Right-click the NPC and press **+ New quest**. The editor has four pages:

1. **General:** name, description, icon, section, where it is offered from, and type.
2. **Objectives:** up to 6. Press the little box, pick a mob, block or item in the panel on the right, and set the amount.
3. **Requirements:** quests that must be claimed first.
4. **Rewards:** items, experience and milestones.

Press **Save**. If a mob or item doesn't exist on the server (for example a mod is missing), the quest is still saved but you get a warning in chat.

### Who is an admin?
An operator with the configured level (2 by default) and, in a singleplayer world, also the world owner even without cheats. It can be changed in the [server configuration](reference.md).
