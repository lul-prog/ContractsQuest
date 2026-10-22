# NPC

El **Maestro de misiones** es un NPC inmóvil e invulnerable que mira a los jugadores. Clic derecho abre su panel; **shift + clic derecho** (siendo admin) abre su editor.

## Aspecto

| Modo | Qué hace |
|---|---|
| Por defecto | La skin original del mod |
| Skin de jugador | Descarga la skin de un jugador premium por nombre (el botón *Yo* pone la tuya) |
| Skin por enlace | Un PNG de skin (64x64 o 64x32) desde un enlace **https** |
| Textura de resource pack | Una textura de skin que venga en un resource pack o mod (`modid:textures/...png`) |
| Mob / modelo de otro mod | El NPC se dibuja con el modelo real de ese mob, de **cualquier mod** instalado. El NBT elige la variante |
| Ítem / modelo 3D | Un ítem flotante. Con el NBT `{CustomModelData:N}` y un resource pack se puede mostrar **cualquier modelo 3D** en JSON |

Además puedes poner **nombre visible**, **escala** (de 0.1 a 8, también cambia la hitbox) y **brazos finos** para skins por enlace o textura.

### Ejemplos de NBT

- Aldeano bibliotecario: `{VillagerData:{profession:"minecraft:librarian",type:"minecraft:plains",level:1}}`
- Ítem con modelo personalizado: `{CustomModelData:1}`

Para elegir el mob o el ítem usa el **cuadrito** junto al campo: abre el selector (inventario o todo el registro). Desde el inventario se copia también el NBT.

!!! warning "Si algo falla"
    Si el mod de un mob no está en un cliente, o el modelo da un error, ese cliente ve la skin por defecto en vez de un fallo. El mod del mob debe estar instalado en el servidor y en los clientes.

!!! note "Privacidad"
    Las skins por enlace se descargan en el cliente y exponen su IP al dueño del enlace. Cada jugador puede desactivarlas con `npc.allowUrlSkins` en `questmod-client.toml`.

## Qué misiones ofrece

En la pestaña **Misiones** del editor del NPC:

- **Todas** (por defecto): ofrece cada misión del servidor, incluidas las que crees después.
- **Solo las elegidas:** marca misiones sueltas o **secciones enteras**. Las misiones nuevas que crees desde el panel de ese NPC se añaden solas.

Las misiones viven en un fondo común: varios NPC pueden ofrecer las mismas, y el progreso del jugador es el mismo en todos.

## Pergamino de misiones

Para copiar la lista de misiones de un NPC a otro (solo admins):

| Acción | Resultado |
|---|---|
| Clic derecho a un NPC con el pergamino **vacío** | Copia su lista |
| Clic derecho a otro NPC con el pergamino **cargado** | Pega la lista (sirve para varios NPC) |
| Shift + clic derecho a un NPC | Copia de nuevo (sobrescribe) |
| Shift + clic derecho al aire | Vacía el pergamino |

Se pegan referencias a las **mismas** misiones, no copias: si editas una, cambia en todos los NPC que la ofrecen. El pergamino copia también las secciones.

## Marcador "!"

Sobre cada NPC aparece un **!** rojo si hay misiones nuevas para ti y uno **dorado** si hay premios por reclamar. Solo cuenta las misiones de ese NPC. Se apaga con `npc.showNpcMarker`, y las texturas (`npc_marker_new.png` y `npc_marker_claim.png`) se pueden reemplazar con un resource pack.

## Eliminar un NPC

En su editor, el botón rojo **Eliminar NPC** pide una segunda pulsación para confirmar. También funciona `/kill`.
