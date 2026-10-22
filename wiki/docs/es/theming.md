# Personalización

Todo el aspecto de las pantallas y del HUD sale de un recurso normal, `assets/questmod/theme.json`. **Cualquier resource pack** (incluido el del servidor) puede sobrescribirlo, y basta con poner **solo las claves que quieras cambiar**: los packs se apilan y lo que falte usa el tema por defecto. Se recarga con **F3 + T**.

!!! tip "Pack de ejemplo"
    En el repositorio, `docs/ejemplo_tema/` es un resource pack completo (madera y dorado) con texturas listas para copiar y modificar.

## Colores y medidas

`colors` usa `RRGGBB` (opaco) o `AARRGGBB`. `layout` son medidas en píxeles (`panel_width`, `list_width`, `hud_max_width`...). Las claves y sus valores por defecto están en la [Referencia](reference.md#tema).

```json
{
  "colors": { "title": "55FFFF", "btn_accept": "AA00AA", "panel": "F00A0A2A" },
  "layout": { "panel_width": 420 }
}
```

## Texturas (skins)

Cada elemento puede tener una **textura opcional**. Si no la tiene, se dibuja con su color de siempre.

```json
"skins": {
  "button": {
    "texture": "mipack:textures/gui/boton.png",
    "width": 24, "height": 20,
    "border": 3,
    "hover":    { "v": 20 },
    "disabled": { "v": 40 }
  }
}
```

| Campo | Descripción |
|---|---|
| `texture` | La imagen. Es lo único obligatorio (el tamaño se detecta solo) |
| `u`, `v`, `width`, `height` | Qué parte de la imagen usar (por defecto, toda). Permite varios estados en una hoja |
| `border` | Grosor del borde para **9-slice**: las esquinas no se deforman y el resto se estira, así un PNG pequeño sirve para cualquier tamaño |
| `hover`, `disabled`, `selected` | Variantes por estado. Heredan lo del skin y solo cambian lo que indiques (casi siempre `v`) |

Poner `"clave": null` quita la textura que haya puesto un pack anterior.

### Elementos

| Elemento | Dónde se usa | Estados |
|---|---|---|
| `panel` | Fondo de las pantallas | normal |
| `picker` | Fondo del selector de ítems | normal |
| `button` | Todos los botones | normal, hover, disabled |
| `button_accept`, `button_claim`, `button_edit`, `button_delete`, `button_confirm`, `button_neutral` | Botones por rol (si falta, usa `button`) | normal, hover |
| `entry` | Filas de la lista de misiones y del selector | normal, hover, selected |
| `section` | Celdas de la tira de secciones | normal, hover, selected |
| `tab` | Pestañas Disponibles / En curso / Hechas (con textura se oculta el subrayado) | normal, hover, selected |
| `slot` | Cuadritos de ítem y celdas del selector | normal, selected (activo) |
| `checkbox` | Casillas de las listas | normal, selected (marcada) |
| `list_bg` | Fondo de las listas con casillas | normal |
| `bar_bg`, `bar_fill`, `bar_done` | Barras de progreso | normal |
| `scroll` | Barras de desplazamiento | normal |
| `hud_box`, `hud_step` | Recuadros del HUD (misión y paso) | normal |

!!! info "Consejos"
    - Haz las texturas pequeñas y usa `border` para que escalen bien.
    - Una hoja con los tres estados apilados (normal, hover, disabled) se indica con `"hover": {"v": 20}`, `"disabled": {"v": 40}`.
    - La franja de color de estado de las filas se ajusta con `layout.entry_stripe` (0 la oculta).
    - Los errores de un skin (imagen que no existe, JSON mal) no rompen nada: se avisa en el log y se usa el color.

## Íconos de sección como imagen

El ícono de una sección puede ser una imagen en vez de un ítem: escribe la ruta del PNG (`mipack:textures/gui/seccion/create.png`) en el campo del ícono. Se escala a 16×16.

## Otras texturas

- **Marcador de los NPC:** `textures/gui/npc_marker_new.png` y `npc_marker_claim.png`.
- **Ítems y NPC:** `textures/item/quest_scroll.png`, `quest_book.png` y `textures/entity/quest_npc.png`.

## Compatibilidad

El formato antiguo `panel_texture` (una imagen completa estirada) sigue funcionando.
