# Instalación

## Requisitos

- Minecraft **1.20.1** con **Forge 47.2.0** o superior.
- Java 17.
- El mod debe estar instalado **en el servidor y en todos los clientes**. Si las versiones no coinciden, el cliente no podrá entrar (el mod comprueba una versión de protocolo de red).

## Pasos

1. Descarga el `.jar` desde CurseForge.
2. Cópialo a la carpeta `mods/` del cliente y del servidor.
3. Inicia el juego. Se crean los archivos de configuración.

## Archivos de configuración

| Archivo | Dónde | Para qué |
|---|---|---|
| `config/questmod-client.toml` | Cliente | HUD, descarga de skins y marcador `!` de los NPC |
| `serverconfig/questmod-server.toml` | Cada mundo | Quién es admin, libro de misiones y libro de bienvenida |
| `defaultconfigs/questmod-server.toml` | Servidor o modpack | Valores por defecto de la config del servidor para mundos nuevos |

Las opciones están descritas en la [Referencia](reference.md).

## Teclas

| Tecla | Acción |
|---|---|
| **K** | Abre el libro de misiones (sin NPC) |
| **G** | Muestra u oculta los pasos de cada misión en el HUD |

Se pueden cambiar en *Opciones → Controles → QuestMod*.

## Actualizar desde una versión anterior

Las misiones y el progreso de versiones anteriores se leen sin problema: el progreso se migra solo la primera vez que un jugador entra. Como el protocolo de red cambia entre versiones, **actualiza el mod a la vez en el servidor y en los clientes**.
