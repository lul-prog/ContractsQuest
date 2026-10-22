# Compatibilidad

## Con otros mods

- **IDs de cualquier mod.** Los objetivos aceptan mobs, bloques e ítems de cualquier mod instalado. El editor los lista (pestaña *Todos* del selector) y avisa en el chat si el objetivo no existe en el servidor.
- **Tags.** Un tag como `#forge:ores` cuenta lo que cualquier mod meta en él, sin configurar nada.
- **Mobs y modelos de otros mods en los NPC.** El NPC se dibuja con el renderer real del mob, así que funcionan también los mods con modelos propios (por ejemplo GeckoLib). Si falla, ese cliente ve la skin por defecto.
- **Ítems con modelos 3D.** Con `CustomModelData` y un resource pack.

## Qué cuenta y qué no

| Tipo | Cuenta | No cuenta |
|---|---|---|
| `kill` | Matar con armas, proyectiles y flechas del jugador | Matar jugadores. Lo que hacen `FakePlayer` (turrets, deployers) |
| `break` | Romper bloques como jugador | Lo que rompen máquinas de otros mods; romper bloques que un mod de protección impide |
| `eat` | Comida y también bebidas (pociones, leche, bebidas de mods) | Lo que consume otro ser |
| `craft` | Craftear en mesa o menús de crafteo | Máquinas que no usan el crafteo normal |
| `smelt` | Sacar el resultado de un horno | Lo que mueven los hoppers u otras automatizaciones |
| `deliver` | Entregar con el botón del panel | Soltar ítems al suelo |

Las acciones de **jugadores falsos** (`FakePlayer`: deployers, turrets, quarries) no suman progreso. Los eventos de matar y romper se cuentan con prioridad baja: si un mod de protección (claims) cancela la acción, **no cuenta**.

## Cliente y servidor

El mod debe estar en **ambos lados** y con la misma versión. Los mods de mobs, bloques o ítems que uses en una misión deben estar en ambos lados también (si no, el servidor o el cliente no reconocerán el ID).

## Mundos existentes

Al actualizar, las misiones y el progreso anteriores se migran solos. Las misiones antiguas quedan con acceso *Solo NPC*, y los NPC existentes siguen ofreciendo todas las misiones.
