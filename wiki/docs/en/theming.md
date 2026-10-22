# Theming

The whole look of the screens and the HUD comes from a normal resource, `assets/questmod/theme.json`. **Any resource pack** (including the server's) can override it, and you only need to put **the keys you want to change**: packs stack and anything missing uses the default theme. It reloads with **F3 + T**.

!!! tip "Example pack"
    In the repository, `docs/ejemplo_tema/` is a complete resource pack (wood and gold) with textures ready to copy and modify.

## Colors and sizes

`colors` uses `RRGGBB` (opaque) or `AARRGGBB`. `layout` holds sizes in pixels (`panel_width`, `list_width`, `hud_max_width`...). The keys and their defaults are in the [Reference](reference.md#theme).

```json
{
  "colors": { "title": "55FFFF", "btn_accept": "AA00AA", "panel": "F00A0A2A" },
  "layout": { "panel_width": 420 }
}
```

## Textures (skins)

Each element can have an **optional texture**. If it has none, it is drawn with its usual color.

```json
"skins": {
  "button": {
    "texture": "mypack:textures/gui/button.png",
    "width": 24, "height": 20,
    "border": 3,
    "hover":    { "v": 20 },
    "disabled": { "v": 40 }
  }
}
```

| Field | Description |
|---|---|
| `texture` | The image. The only required field (its size is detected automatically) |
| `u`, `v`, `width`, `height` | Which part of the image to use (default, all of it). Lets you put several states in one sheet |
| `border` | Border thickness for **9-slice**: corners aren't distorted and the rest stretches, so one small PNG works at any size |
| `hover`, `disabled`, `selected` | State variants. They inherit the skin and only change what you specify (almost always `v`) |

Setting `"key": null` removes the texture set by an earlier pack.

### Elements

| Element | Where it is used | States |
|---|---|---|
| `panel` | Screen backgrounds | normal |
| `picker` | Item picker background | normal |
| `button` | All buttons | normal, hover, disabled |
| `button_accept`, `button_claim`, `button_edit`, `button_delete`, `button_confirm`, `button_neutral` | Buttons by role (falls back to `button`) | normal, hover |
| `entry` | Rows of the quest list and the picker | normal, hover, selected |
| `section` | Cells of the section strip | normal, hover, selected |
| `tab` | Available / In progress / Done tabs (with a texture the underline is hidden) | normal, hover, selected |
| `slot` | Item boxes and picker cells | normal, selected (active) |
| `checkbox` | List checkboxes | normal, selected (checked) |
| `list_bg` | Background of lists with checkboxes | normal |
| `bar_bg`, `bar_fill`, `bar_done` | Progress bars | normal |
| `scroll` | Scrollbars | normal |
| `hud_box`, `hud_step` | HUD boxes (quest and step) | normal |

!!! info "Tips"
    - Keep textures small and use `border` so they scale well.
    - A sheet with the three states stacked (normal, hover, disabled) is declared with `"hover": {"v": 20}`, `"disabled": {"v": 40}`.
    - The status color stripe of the rows is adjusted with `layout.entry_stripe` (0 hides it).
    - A broken skin (missing image, bad JSON) breaks nothing: it is reported in the log and the color is used.

## Section icons as images

A section's icon can be an image instead of an item: type the PNG path (`mypack:textures/gui/section/create.png`) in the icon field. It is scaled to 16×16.

## Other textures

- **NPC marker:** `textures/gui/npc_marker_new.png` and `npc_marker_claim.png`.
- **Items and NPC:** `textures/item/quest_scroll.png`, `quest_book.png` and `textures/entity/quest_npc.png`.

## Compatibility

The old `panel_texture` format (one stretched full image) still works.
