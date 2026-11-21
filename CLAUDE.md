# RunnerApp — memoria del proyecto (copia en el repo)

La versión principal vive en el Proyecto de claude.ai "CREAR APPS" como `claude/POKER_TEAM_APP_PROYECTO.md`. Leerla al empezar y actualizar ambas tras cada cambio.

## Resumen
- App del team de póker de David (6 jugadores + 2 coaches). Un solo `index.html` sin frameworks.
- Supabase: proyecto `runnerapp` (ref `hwxckgwswhyqarhcxave`, sa-east-1). Vercel publica `main` automáticamente.
- Cada jugador sube el .zip de PokerCraft (un .txt por torneo) → historial diario, stats, makeup (por torneos y en vivo por caja), cierre mensual con split según su deal, rakeback mensual.
- Coaches: correos en la tabla `coaches`; ven a todos vía `es_coach()` y RLS.

## Reglas del parser PokerCraft
- Re-entradas → costo = buy-in × (1+N).
- Day 2 / Final (`[Final…]`, `[Day 2+]`, `[Stage 2+]`) → costo 0.
- Monedas $ y ¥; ¥ se convierte con la tasa del día (Frankfurter, caché en `tipos_cambio`).
- Único por (jugador_id, gg_id).

## Tablas
coaches · perfiles · torneos · rakeback · cierres_mes · caja_mes · caja_registros · tipos_cambio (detalle en el doc del Proyecto).

## Cómo trabajar cada mejora
1. Leer este archivo y el `index.html`.
2. Hacer el cambio y probarlo en navegador headless.
3. Commit + push a `main` → Vercel publica solo; migraciones en Supabase si cambia la base.
4. Actualizar este archivo y el doc del Proyecto.
