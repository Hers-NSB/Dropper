# Estado actual · 2026-11-24

Dropper publica desde Telegram y graba el comprobante en una PC con Windows. El panel de Cloudflare administra los bots y permite consultar las confirmaciones de cada modelo.

## Integración de HERS · 23 de noviembre de 2026

La rama `codex/integracion-hers-y-windows` sirve vistas de Bots y Drops para Hers-prueba y valida el rol de administrador con su Supabase. Usa los perfiles, las publicaciones y la sesión de Chrome que ya guarda D1. El workflow prepara `HERS-Dropper.exe` con la misma base de código y mantiene `Dropper.exe` como descarga compatible. Pasaron las 42 pruebas del Worker y su compilación. Pasaron las pruebas en navegador y la compilación y prueba de Windows en GitHub Actions.

## Resumen diario y recuperación desde Telegram

- El [PR #35](https://github.com/Hers-NSB/Dropper/pull/35) incorpora el resumen diario por modelo en hora de Caracas. Dropper conserva las confirmaciones pendientes y las sincroniza cuando recupera la conexión.
- Si falla un post, **Enviar enlace** permite confirmar la publicación manual y **Omitir post** continúa con las demás. El video conserva el orden del muro e incluye los posts automáticos y manuales confirmados.
- La compilación de Windows genera `Dropper.exe`. Pasaron las [pruebas en Ubuntu y Windows](https://github.com/Hers-NSB/Dropper/actions/runs/44774214889) y la [compilación y prueba del EXE](https://github.com/Hers-NSB/Dropper/actions/runs/44774215246).

## Producción

- Cloudflare sirve al 100 % la versión **17** del Worker, `248f16f5-0d8c-4df6-acb2-e929b04f2d45`, código `4de4ed3` del [PR #37](https://github.com/Hers-NSB/Dropper/pull/37). Las vistas de HERS usan la D1 existente. El [panel independiente](https://dropper.datosenviados07.workers.dev/admin) continúa disponible.
- El release [`hers-dropper-60-1`](https://github.com/Hers-NSB/Dropper/releases/tag/hers-dropper-60-1) contiene [`HERS-Dropper.exe`](https://github.com/Hers-NSB/Dropper/releases/download/hers-dropper-60-1/HERS-Dropper.exe). El [workflow de Windows](https://github.com/Hers-NSB/Dropper/actions/runs/45419721702) verificó el ejecutable publicado, incluido el icono redondeado de HERS en los siete tamaños. El [PR #38](https://github.com/Hers-NSB/Dropper/pull/38) aplica la paleta del Panel Administración a la app.

Consulta [README.md](README.md) para configurar los bots, recuperar publicaciones y consultar el resumen.
