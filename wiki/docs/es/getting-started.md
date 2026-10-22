# Primeros pasos

## Para jugadores

- **Abrir las misiones:** clic derecho a un Maestro de misiones, o la tecla **K** / el ítem *Libro de misiones* si el servidor lo permite.
- **El panel:** la lista de misiones está a la izquierda y el detalle a la derecha. Las pestañas separan *Disponibles*, *En curso* y *Hechas*. Si hay secciones, aparecen como íconos a la izquierda.
- **Aceptar, entregar y reclamar:** pulsa **Aceptar** en una misión disponible. Cuando cumplas sus objetivos aparece **¡Reclamar!** y recibes los premios. Algunas misiones piden **Entregar** ítems al NPC. Para aceptar, entregar o reclamar con un NPC debes estar a menos de 10 bloques de él.
- **HUD:** las misiones aceptadas se muestran en un lateral de la pantalla. Con **G** se despliega cada paso por separado.
- **Marcador:** sobre un NPC, un **!** rojo indica misiones nuevas y uno **dorado**, premios por reclamar.

!!! tip "Misiones comunitarias"
    Una misión comunitaria tiene un contador compartido por todo el servidor. Pulsa **Unirse** para participar: solo cuenta lo que hagas después de unirte.

## Para administradores

### 1. Consigue un NPC
Usa el huevo *Maestro de misiones* (pestaña de herramientas del creativo) o `/summon questmod:quest_npc`.

### 2. Configúralo
**Shift + clic derecho** al NPC (siendo admin) abre su editor, con dos pestañas:

- **Aspecto:** nombre, skin, modelo de otro mob o ítem, escala. Ver [NPC](npcs.md).
- **Misiones:** qué misiones ofrece (todas, o solo las que elijas).

### 3. Crea una misión
Clic derecho al NPC y pulsa **+ Nueva misión**. El editor tiene cuatro páginas:

1. **General:** nombre, descripción, ícono, sección, desde dónde se ofrece y tipo.
2. **Objetivos:** hasta 6. Pulsa el cuadrito, elige un mob, bloque o ítem en el panel de la derecha y pon la cantidad.
3. **Requisitos:** misiones que deben estar reclamadas antes.
4. **Premios:** ítems, experiencia y hitos.

Pulsa **Guardar**. Si un mob o ítem no existe en el servidor (por ejemplo, falta el mod), la misión se guarda igual pero recibes un aviso en el chat.

### ¿Quién es admin?
Un operador con el nivel configurado (2 por defecto) y, en un mundo en solitario, también el dueño del mundo aunque no tenga cheats. Se puede cambiar en la [configuración del servidor](reference.md).
