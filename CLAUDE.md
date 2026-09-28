# goals — app de objetivos (PWA)

Repo **público**: solo código. Nunca añadas datos personales, categorías u objetivos
reales, tokens, rutas locales ni nombres de repos privados (tampoco en tests ni docs).
Los datos de cada usuario viven en su propio repo privado.

## Reglas
- HTML + JS sin build, con `// @ts-check` y tipos JSDoc. Ningún script ni recurso de terceros
  (la CSP de `index.html` solo permite `'self'` y `https://api.github.com`).
- `js/periodo.js` puede tener una copia idéntica fuera de este repo (CLI); si lo cambias,
  indícalo al terminar para sincronizarla. Los periodos se calculan en la `timeZone` del archivo de datos.
- Esquema del JSON: ver `js/store.js` (tipos `Goal` y `GoalsDoc`). Commits de la app con prefijo `objetivos:`.
- Antes de subir: `node --test tests/`. Si cambia la lista `SHELL` de `sw.js`, sube `VERSION`.

## Al terminar cada sesión
Actualiza `progreso.md` (fecha, qué se hizo, siguiente paso) y haz commit y push a `main`.
