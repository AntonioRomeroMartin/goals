# Progreso — goals

## Estado actual
- Versión 1.5: campos opcionales Location y Notes en los objetivos.

## Sesiones (más reciente arriba)
- 2026-09-29 · v1.5: campos opcionales `location` (chip 📍 en la tarjeta) y `notes` (texto de varias líneas bajo los chips) en el formulario de objetivo. Nueva prueba de lógica (19). Siguiente: probar en el navegador con datos reales.
- 2026-09-29 · v1.4: el plazo es cuándo caduca. Objetivos de una vez (`repeat:false`, `period`) que al caducar pasan a Past con ✓/✗ y % de cumplimiento; casilla Repeat para hábitos; selector Active/Past/Archived. 18 pruebas de lógica + 9 en navegador.
- 2026-09-28 · v1.3: prefijo de commits `goals:`; archivo de datos por defecto `goals.json` (también en el CLI de `period.js`).
- 2026-09-28 · v1.2: interfaz, errores, README y cuerpo de los commits en inglés (se mantiene el prefijo `objetivos:`); archivo por defecto `goals.json`.
- 2026-09-28 · v1.1: sin datos por defecto (usuario, repo, categorías, zona horaria); zona horaria en el archivo de datos; gestión de categorías (añadir/quitar); creación del archivo si no existe; README para otros usuarios.
- 2026-09-28 · v1: vistas por plazo y categoría, filtro, metas por periodo, archivar/borrar, guardado agrupado (2 s), resolución de conflictos, modo sin conexión de solo lectura, PWA.
