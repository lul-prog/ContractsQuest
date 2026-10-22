# Quests

## Objectives

A quest has **1 to 6 objectives** and is completed when **all** are met.

| Type | Met when the player... |
|---|---|
| `kill` | kills an entity |
| `break` | breaks a block |
| `eat` | eats or **drinks** an item (food, potions, milk, mod drinks) |
| `craft` | crafts an item |
| `smelt` | takes an item out of a furnace |
| `deliver` | hands items to the NPC or book with the **Deliver** button (they are removed from the inventory) |

### IDs and tags

The target is an **ID** (`minecraft:zombie`, `create:andesite_alloy`) or a **tag** with `#` (`#minecraft:logs`, `#forge:ores`). With a tag, a "break 20 logs" quest counts the logs from **any mod** that puts them in that tag.

You don't have to type anything in the editor: the **picker** on the right has three tabs, *Inventory* (your items), *All* (the whole registry, searchable, mods included) and *Tags*.

## Rewards

- Up to **6 reward items**, each with its amount and **NBT** (enchantments, potions, mod data). If the amount exceeds a stack, it is split up; whatever doesn't fit in the inventory drops on the ground.
- Optional **experience**.
- You can hide the reward (the player sees `???` until claiming).

### Milestones (percentage rewards)

A quest can give intermediate rewards when it reaches certain percentages. The final reward is 100%.

- Up to **6 milestones**, with a percentage from 1 to 99, and their own items and experience.
- The **percentage** is the average progress of each objective, so all of them weigh the same. In a community quest it uses the global progress.
- They are claimed with **Claim milestone!**, without waiting for the quest to be completed. Claiming the final reward also hands out any milestones left.
- In the editor: *Rewards* page, the top button switches between the final reward and each milestone (`+` creates one, `✕` deletes it).

## Requirements (chains)

A quest can require that others are **claimed**. Until then it shows as *Locked* and you can see what is missing. Cycles are not allowed.

## Where it is offered from

Each quest chooses its **access**:

| Access | Meaning |
|---|---|
| NPC only | Accepted, delivered and claimed with an NPC that offers it |
| Book only | Only from the quest book (**K** key or item), no NPC |
| NPC and book | From either |

## Automation

- **Auto-accept:** accepted as soon as it is unlocked, with no NPC or book. Great for tutorials or advancement-style progressions.
- **Auto-claim:** when completed, the rewards go straight to the inventory.

## Sections

**Sections** group quests, for example one per mod. In the panel they appear as a strip of icons on the left, with a green dot if there are rewards to claim and a gold one if there are new quests.

- **Create (admins):** the **+** button of the strip. **Right-click** a section to edit or delete it (its quests are left without a section).
- **Assign:** in the quest editor, General page.
- **NPC by section:** in the NPC's *Quests* tab you can tick whole sections. That NPC offers all their quests, including ones you create later.

## Community quests

A **server-wide** counter, and each player decides whether to take part.

- **Joining:** the quest appears in *Available* with the global progress and a **Join** button. Only what you do **after joining** counts. Whoever doesn't join neither contributes nor spends items on deliveries.
- **Auto-join (optional):** if you prefer an event where everyone is in by default, turn it on in the quest.
- **Claiming:** when completed, only those who joined are notified in chat, and those who contributed at least the quest's **minimum contribution** can claim. Whoever didn't join, or didn't reach the minimum, sees it as closed. Nobody can join after it is completed.
- **Deliveries:** delivery objectives work too: what each player hands in adds to the total and to their contribution.
- **Limitations:** no requirements and no auto-claim.
- **Repeating an event:** `/questmod community reset <quest>`.

!!! info "Performance"
    Community progress is sent to players in batches, at most once per second, so hundreds of kills don't flood the network.

## Editing and deleting

Admins see **Edit** and **Delete** (with confirmation) in the panel. Quests that come from a datapack are **read-only** in game.
