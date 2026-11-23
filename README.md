# Dropper

Aplicación de Windows que publica los mensajes reenviados a un bot de Telegram en el muro de la modelo asignada mediante AgencyKey y envía un comprobante en video. La publicación, la grabación y los registros se ejecutan en la PC donde se abre la app.

## Requisitos y descarga

- Windows de 64 bits, Google Chrome instalado e internet.
- Una API de AgencyKey y un bot de Telegram.
- [Descargar Dropper para Windows](https://github.com/Hers-NSB/Dropper/releases/latest). Funciona sin instalar Python.

En HERS, descarga `HERS-Dropper.exe` desde **Administración → Dropper**. En ese panel también puedes consultar el historial y conectar la sesión de Chrome. Gestiona los bots y sus verificaciones en **Administración → Conectores → Bots**. El ejecutable conserva el acceso de las apps, los ajustes locales y el mismo servicio Dropper.

## Primeros pasos

1. En el [panel web](https://dropper.datosenviados07.workers.dev/admin), guarda la clave global de AgencyKey y la contraseña de las apps en **Ajustes**. En **Bots**, configura el token de Telegram, la modelo y los `@usuarios` autorizados para cada bot.
2. Abre el EXE, pulsa **Actualizar** e introduce la contraseña de las apps cuando se solicite.
3. Con la app abierta, pulsa **Conectar AgencyKey** en la web e inicia sesión en la ventana de Chrome.
4. Pulsa **Verificar Mi perfil** desde la web. No hace falta iniciar el bot para comprobar la modelo.
5. En la app, selecciona el bot y pulsa **Iniciar bot**. En Telegram pulsa **Iniciar**, reenvía los mensajes y elige **Publicar normal** o **Publicar lento**.

Se admiten mensajes de texto y fotos individuales con texto. El lote se publica del último mensaje reenviado al primero. Si el Drop contiene publicaciones confirmadas, el bot envía el video y la confirmación al mismo chat.

La app debe permanecer abierta para verificar, publicar y grabar. Las verificaciones reutilizan Chrome al cambiar de modelo y reintentan las cargas incompletas o los cortes de conexión; puedes detenerlas con **Cancelar verificación**. Si recargas la web, se retoma la comprobación pendiente. La búsqueda de posts comienza al grabar, después de confirmar la identidad de la modelo. **Actualizar** descarga configuraciones. Instala el último `Dropper.exe` para conectar la aplicación al dominio `dropper.datosenviados07.workers.dev`.

## Acceso y recuperación

1. En el panel, edita el bot y añade los `@usuarios` de Telegram autorizados. Una lista vacía bloquea la publicación. Al reconocer un usuario en una PC, la app lo vincula a su ID de Telegram para evitar que otra cuenta reutilice ese nombre.
2. Configura una sola clave de AgencyKey en **Ajustes**. La app descarga la clave y el token del bot usando su contraseña general. Compártela únicamente con quienes puedan usar las configuraciones de todos los bots.
3. Si falla un post, el bot muestra **Enviar enlace** y **Omitir post** debajo del teclado. Usa **Enviar enlace** y pega el enlace de OnlyFans si lo publicaste manualmente. Usa **Omitir post** si no lo publicaste. El bot continúa y graba los posts automáticos y manuales confirmados del Drop. La app conserva el avance del lote tras reiniciar.
4. El comprobante graba los posts del Drop en el orden del muro, del más reciente al más antiguo. Chrome permanece oculto y las publicaciones ajenas al Drop se excluyen del video y de la espera de fotos.
5. Tras 120 segundos sin cargar una foto del Drop, Telegram avisa qué post está pendiente. Chrome sigue en ese punto y la grabación continúa automáticamente cuando aparece la foto. **Reintentar** vuelve a comprobarla y, si Chrome ya se cerró, inicia otra grabación del mismo Drop. **Cancelar grabación** detiene solo el comprobante.
6. Si Chrome muestra un aviso de DRM en un post del Drop, el comprobante incluye el post tal como aparece e indica que su foto quedó sin verificar.

Para conservar un número limitado de días de videos y diagnósticos locales, configura `AGENCYKEY_RECORDER_RETENTION_DAYS` en Windows antes de iniciar la app. La limpieza omite comprobantes que aún están asociados a un trabajo. Si no se configura, se conservan los archivos.

## Resumen diario de Drops

En el panel web, abre **Drops**. El botón **Hoy** muestra las confirmaciones del día en hora de Caracas. El selector de fecha permite consultar días anteriores.

Cada modelo tiene su propio resumen, con una fila por Drop y los recuentos de publicaciones automáticas y manuales. Un post manual cuenta cuando el bot recibe su enlace. Los posts omitidos quedan fuera del resumen y del comprobante. Si omites todos los posts, el bot cierra el Drop sin generar un video.

El historial comienza con la versión de Dropper que sincroniza las confirmaciones con el panel. Consulta [STATUS.md](STATUS.md#producción) para comprobar la disponibilidad del panel y del ejecutable.

## Errores y reportes

| Dónde ocurre | Dónde consultar y descargar el reporte |
| --- | --- |
| Verificación manual desde la web | En la fila de la modelo: **Ver detalle** o **Descargar reporte**. |
| Publicación o grabación en la app | **Ver registro → Guardar registro** en la app. |

**Reintentar** en Telegram vuelve a grabar el comprobante si el intento anterior terminó.

## Estado del proyecto

Para habilitar la integración, configura `HERS_SUPABASE_PUBLISHABLE_KEY` en el Worker de Dropper con la clave publicable de Supabase de Hers-prueba. Publica el Worker de Dropper y luego el de HERS con su binding a `dropper`. Las vistas integradas comparten D1 con el panel independiente. El Worker exige una sesión administrativa de Hers-prueba para consultar o modificar datos desde HERS.

Consulta [STATUS.md](STATUS.md) para conocer la versión publicada, las comprobaciones realizadas y la siguiente tarea pendiente.
