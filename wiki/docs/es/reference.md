# Referencia

## Controles

| Tecla | Acción |
|---|---|
| **K** | Abre el libro de misiones |
| **G** | Muestra u oculta los pasos de cada misión en el HUD |

## Configuración del cliente

Archivo `config/questmod-client.toml`.

| Opción | Por defecto | Descripción |
|---|---|---|
| `hud.enabled` | `true` | Muestra el progreso de las misiones activas en pantalla |
| `hud.side` | `LEFT` | Lado del HUD: `LEFT` o `RIGHT` |
| `hud.maxQuests` | `5` | Máximo de misiones visibles en el HUD (1 a 10) |
| `hud.expanded` | `false` | Muestra los pasos de cada misión por separado (lo alterna la tecla **G**) |
| `npc.allowUrlSkins` | `true` | Permite descargar skins desde enlaces https que el servidor ponga en los NPC |
| `npc.showNpcMarker` | `true` | Muestra el `!` sobre los NPC |

## Configuración del servidor

Archivo `serverconfig/questmod-server.toml` de cada mundo (o `defaultconfigs/questmod-server.toml` para fijar valores en un modpack).

| Opción | Por defecto | Descripción |
|---|---|---|
| `general.adminPermissionLevel` | `2` | Nivel de op necesario para administrar misiones y NPC (0 a 4) |
| `general.singleplayerOwnerIsAdmin` | `true` | En un mundo en solitario, el dueño es admin aunque no tenga cheats |
| `general.bookEnabled` | `true` | Activa el libro de misiones (tecla e ítem) |
| `general.giveBook` | `FIRST_JOIN` | Cuándo se entrega el libro: `NEVER`, `FIRST_JOIN` (una vez por jugador) o `IF_MISSING` (en cada entrada, si no lo lleva) |

## Comandos

Para admins (nivel configurado, 2 por defecto; la consola y los command blocks usan ese mismo nivel).

| Comando | Qué hace |
|---|---|
| `/questmod export <namespace>` | Exporta las misiones y secciones del mundo como datapack en `questmod_export/<namespace>/` |
| `/questmod reset <jugadores> [misión]` | Reinicia el progreso de todo, o de una misión |
| `/questmod complete <jugadores> <misión>` | Marca una misión como completada |
| `/questmod community reset <misión>` | Reinicia una misión comunitaria para todos (contador, aportes y premios reclamados) |

Para recargar las misiones de datapack se usa el `/reload` de siempre.

## Ítems y entidades

| ID | Qué es |
|---|---|
| `questmod:quest_npc` | El Maestro de misiones (`/summon questmod:quest_npc`) |
| `questmod:quest_npc_spawn_egg` | Su huevo generador |
| `questmod:quest_scroll` | Pergamino de misiones (copia y pega listas entre NPC) |
| `questmod:quest_book` | Libro de misiones (abre el panel sin NPC) |

## Rutas de datapack

| Ruta | Contenido |
|---|---|
| `data/<ns>/questmod/quests/*.json` | Misiones |
| `data/<ns>/questmod/sections/*.json` | Secciones |

Los formatos están en [Modpacks y datapacks](modpacks.md) y hay esquemas JSON para validarlos.

## Tema

Todo esto se cambia con `assets/questmod/theme.json` (ver [Personalización](theming.md)). Esta tabla se generó leyendo el código del mod.

### Colores

| Clave | Por defecto | Uso |
|---|---|---|
| `panel` | `E0141418` | Fondo de los paneles |
| `title` | `E8C34A` | Títulos |
| `accent` | `E8C34A` | Acentos (pestaña elegida, objetivos) |
| `text` | `FFFFFF` | Texto principal |
| `text_dim` | `9A9AA5` | Texto secundario |
| `text_muted` | `888888` | Texto apagado (ayudas) |
| `tab_hover_line` | `666666` | Subrayado de pestañas |
| `error` | `FF5555` | Mensajes de error |
| `entry` | `1B1B24` | Fondo de las filas |
| `entry_hover` | `23232E` | Fila bajo el mouse |
| `entry_selected` | `2D2D44` | Fila seleccionada |
| `claimed` | `7DEB7D` | Texto de "hecho" / reclamado |
| `bar_bg` | `33333D` | Fondo de las barras |
| `bar_fill` | `5B8DD9` | Relleno de la barra de progreso |
| `bar_done` | `4CAF50` | Barra completada |
| `btn_accept` | `2E7D32` | Botón aceptar |
| `btn_claim` | `8A6D1B` | Botón reclamar |
| `btn_edit` | `2A4B6B` | Botón editar |
| `btn_delete` | `6B2A2A` | Botón borrar |
| `btn_confirm` | `8A1B1B` | Botón de confirmación |
| `btn_disabled` | `3A3A3A` | Botón desactivado |
| `btn_neutral` | `3F3F48` | Botón neutro |
| `btn_text_disabled` | `777777` | Texto de botón desactivado |
| `btn_text_confirm` | `FF8888` | Texto del botón de confirmación |
| `hud_bg` | `B0141418` | Fondo de los recuadros del HUD |

### Medidas

| Clave | Por defecto | Uso |
|---|---|---|
| `panel_width` | `460` | Ancho máximo del panel de misiones |
| `list_width` | `170` | Ancho de la lista de misiones |
| `entry_height` | `72` | Alto de una fila de misión |
| `entry_height_compact` | `60` | Alto de una fila en modo compacto |
| `hud_width` | `152` | Ancho mínimo del HUD |
| `hud_max_width` | `240` | Ancho máximo del HUD |
| `entry_stripe` | `3` | Grosor de la franja de estado de las filas (0 la oculta) |
