# Misiones

## Objetivos

Una misión tiene de **1 a 6 objetivos** y se completa cuando se cumplen **todos**.

| Tipo | Se cumple cuando el jugador... |
|---|---|
| `kill` (Mata) | mata una entidad |
| `break` (Rompe) | rompe un bloque |
| `eat` (Consume) | come o **bebe** un ítem (comida, pociones, leche, bebidas de mods) |
| `craft` (Craftea) | craftea un ítem |
| `smelt` (Funde) | saca un ítem de un horno |
| `deliver` (Entrega) | entrega ítems al NPC o al libro con el botón **Entregar** (se quitan del inventario) |

### IDs y tags

El objetivo es un **ID** (`minecraft:zombie`, `create:andesite_alloy`) o un **tag** con `#` (`#minecraft:logs`, `#forge:ores`). Con un tag, una misión de "romper 20 troncos" cuenta los troncos de **cualquier mod** que los meta en ese tag.

En el editor no hace falta escribir nada: el **selector** a la derecha tiene tres pestañas, *Inventario* (tus ítems), *Todos* (todo el registro, con buscador, mods incluidos) y *Tags*.

## Premios

- Hasta **6 ítems** de recompensa, cada uno con su cantidad y su **NBT** (encantamientos, pociones, datos de mods). Si la cantidad pasa de un stack, se reparte; lo que no quepa en el inventario cae al suelo.
- **Experiencia** opcional.
- Puedes ocultar el premio (el jugador ve `???` hasta reclamar).

### Hitos (premios por porcentaje)

Una misión puede dar premios intermedios al llegar a ciertos porcentajes. El premio final es el 100%.

- Hasta **6 hitos**, con porcentaje de 1 a 99, ítems y experiencia propios.
- El **porcentaje** es el promedio del avance de cada objetivo, así todos pesan igual. En una comunitaria cuenta el avance global.
- Se reclaman con **¡Reclamar hito!**, sin esperar a completar la misión. Al reclamar el premio final se entregan los hitos que faltaran.
- En el editor: página *Premios*, el botón de arriba cambia entre el premio final y cada hito (`+` crea uno, `✕` lo borra).

## Requisitos (cadenas)

Una misión puede exigir que otras estén **reclamadas**. Mientras tanto aparece como *Bloqueada* y se ve qué falta. No se permiten ciclos.

## Desde dónde se ofrece

Cada misión elige su **acceso**:

| Acceso | Significado |
|---|---|
| Solo NPC | Se acepta, entrega y reclama con un NPC que la ofrezca |
| Solo libro | Solo desde el libro de misiones (tecla **K** o ítem), sin NPC |
| NPC y libro | Desde cualquiera de los dos |

## Automatismos

- **Aceptar sola:** se acepta en cuanto está desbloqueada, sin NPC ni libro. Ideal para tutoriales o progresiones tipo logros.
- **Reclamar sola:** al completarse, los premios van directo al inventario.

## Secciones

Las **secciones** agrupan misiones, por ejemplo una por mod. En el panel aparecen como una tira de íconos a la izquierda, con un punto verde si hay premios por reclamar y uno dorado si hay misiones nuevas.

- **Crear (admins):** el botón **+** de la tira. **Clic derecho** sobre una sección para editarla o borrarla (sus misiones quedan sin sección).
- **Asignar:** en el editor de misión, página General.
- **NPC por sección:** en la pestaña *Misiones* del NPC puedes marcar secciones enteras. Ese NPC ofrece todas sus misiones, también las que crees después.

## Misiones comunitarias

Un contador **global del servidor**, y cada jugador decide si participa.

- **Unirse:** la misión aparece en *Disponibles* con el avance global y el botón **Unirse**. Solo cuenta lo que hagas **después de unirte**. Quien no se une no aporta ni gasta ítems en entregas.
- **Unirse sola (opcional):** si prefieres un evento donde todos entren por defecto, actívalo en la misión.
- **Reclamar:** al completarse se avisa por chat solo a quienes se unieron, y reclaman los que aportaron al menos el **aporte mínimo** de la misión. Quien no se unió, o no llegó al mínimo, la ve como cerrada. Nadie puede unirse después de completada.
- **Entregas:** los objetivos de entrega también valen: lo que entrega cada jugador suma al total y a su aporte.
- **Limitaciones:** no tienen requisitos ni reclamo automático.
- **Repetir un evento:** `/questmod community reset <misión>`.

!!! info "Rendimiento"
    El avance de las comunitarias se envía a los jugadores en bloque, como máximo una vez por segundo, así cientos de kills no saturan la red.

## Editar y borrar

Los admins ven **Editar** y **Borrar** (con confirmación) en el panel. Las misiones que vienen de un datapack son de **solo lectura** en el juego.
