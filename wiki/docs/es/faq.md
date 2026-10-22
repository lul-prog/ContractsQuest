# Preguntas frecuentes

??? question "No puedo editar nada en mi mundo en solitario"
    En un mundo en solitario el dueño es admin **si** `singleplayerOwnerIsAdmin` está en `true` (por defecto). Un modpack puede haberlo puesto en `false` en `defaultconfigs/questmod-server.toml`. Cámbialo en `serverconfig/questmod-server.toml` de tu mundo, o activa los cheats.

??? question "No veo el libro de misiones / la tecla K no hace nada"
    Comprueba `bookEnabled` y `giveBook` en la config del servidor. Además, el libro solo muestra misiones con acceso *Solo libro* o *NPC y libro*: una misión *Solo NPC* no aparece.

??? question "Mi misión no avanza"
    - Si el objetivo no existe en el servidor (falta el mod o el ID/tag está mal escrito), al guardar recibiste un aviso en el chat y ese objetivo **no avanza**.
    - Debes haber **aceptado** la misión (en las comunitarias, **unirte**).
    - Las acciones de `FakePlayer` y lo que cancele un mod de protección no cuentan. Ver [Compatibilidad](compatibility.md).

??? question "El botón Aceptar o Reclamar no hace nada"
    Con un NPC debes estar a **menos de 10 bloques** y ese NPC debe ofrecer la misión (revisa su pestaña *Misiones*). Una misión *Bloqueada* pide completar antes sus requisitos.

??? question "Una misión comunitaria no suma"
    Solo cuenta lo que haces **después de unirte**. Pulsa **Unirse** en el panel.

??? question "Un NPC se ve con la skin por defecto"
    Puede ser que el mod del mob no esté en tu cliente, que el modelo haya fallado, o que las skins por enlace estén desactivadas (`npc.allowUrlSkins`). Una skin de jugador tarda un instante en descargarse.

??? question "Mi misión de datapack no aparece"
    Revisa el log: los archivos inválidos se omiten y se indica el motivo. Ejecuta `/reload` tras cambiar los archivos y comprueba la ruta `data/<ns>/questmod/quests/`. Las misiones de datapack son de solo lectura en el juego.

??? question "Mis texturas del tema no se aplican"
    Recarga con **F3 + T**, comprueba que el resource pack está activo y que `theme.json` está en `assets/questmod/`. Si una imagen no existe o el JSON está mal, el log lo indica y se usa el color de siempre.

??? question "¿Cómo reinicio el progreso de un jugador?"
    `/questmod reset <jugador>` para todo, o `/questmod reset <jugador> <misión>` para una sola. Para repetir una comunitaria para todos: `/questmod community reset <misión>`.

??? question "¿Qué pasa con mis misiones al actualizar?"
    Se migran solas. Las misiones antiguas quedan como *Solo NPC*, y los NPC existentes siguen ofreciendo todo. Actualiza cliente y servidor a la vez.
