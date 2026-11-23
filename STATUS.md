# Estado actual · 2026-11-20

Dropper publica desde Telegram y graba el comprobante en una PC con Windows. El panel de Cloudflare administra los bots y permite consultar las confirmaciones de cada modelo.

## Integración de HERS · 23 de noviembre de 2026

La rama `codex/integracion-hers-y-windows` sirve vistas de Bots y Drops para Hers-prueba y valida el rol de administrador con su Supabase. Usa los perfiles, las publicaciones y la sesión de Chrome que ya guarda D1. El workflow prepara `HERS-Dropper.exe` con la misma base de código y mantiene `Dropper.exe` como descarga compatible. Pasaron las 42 pruebas del Worker y su compilación. Pendientes el flujo de navegador en CI, el ejecutable de Windows y el despliegue.

## Resumen diario y recuperación desde Telegram

- El [PR #35](https://github.com/Hers-NSB/Dropper/pull/35) incorpora el resumen diario por modelo en hora de Caracas. Dropper conserva las confirmaciones pendientes y las sincroniza cuando recupera la conexión.
- Si falla un post, **Enviar enlace** permite confirmar la publicación manual y **Omitir post** continúa con las demás. El video conserva el orden del muro e incluye los posts automáticos y manuales confirmados.
- La compilación de Windows genera `Dropper.exe`. Pasaron las [pruebas en Ubuntu y Windows](https://github.com/Hers-NSB/Dropper/actions/runs/44774214889) y la [compilación y prueba del EXE](https://github.com/Hers-NSB/Dropper/actions/runs/44774215246).

## Producción

- Worker v9 activo en el [panel de Cloudflare](https://dropper.datosenviados07.workers.dev/admin). La base D1 existente ya contiene el esquema de **Drops**. Se comprobó que `/health` devuelve la versión 9, el panel incluye el resumen y la consulta requiere sesión de administrador.
- El [workflow de Windows](https://github.com/Hers-NSB/Dropper/actions/workflows/windows-exe.yml) compila y publica `Dropper.exe` desde `main`. Usa la [última versión oficial](https://github.com/Hers-NSB/Dropper/releases/latest) para conectar la app al nuevo dominio de Dropper.

Consulta [README.md](README.md) para configurar los bots, recuperar publicaciones y consultar el resumen.
