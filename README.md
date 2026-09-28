# Objetivos

PWA estática para seguir objetivos por plazo (diario, semanal, mensual, trimestral, anual y con fecha límite) y por categoría. Cualquiera puede usarla con **sus propios datos privados**.

## Cómo usarla

1. Crea un repo **privado** en GitHub para tus datos (o usa uno que ya tengas).
2. Crea un token *fine-grained* en GitHub → Settings → Developer settings → Fine-grained tokens:
   - *Repository access*: **Only select repositories** → ese repo.
   - *Permissions* → *Contents*: **Read and write**. Nada más.
3. Abre la app, pulsa ⚙ y pon el token, tu usuario, el repo, el archivo (por defecto `objetivos.json`) y la rama. Si el archivo no existe, la app lo crea vacío.
4. Crea tus categorías (botón «Categorías») y tus objetivos. En el móvil puedes instalarla como app.

## Privacidad

- La web no tiene servidor: solo habla con `api.github.com` desde tu navegador (CSP restringida, sin scripts de terceros).
- El token y una copia de tus datos se guardan solo en el almacenamiento local de tu navegador.
- Este repo contiene únicamente código; no hay categorías, objetivos ni datos de nadie.

## Formato de datos

```json
{
  "version": 1,
  "timeZone": "Zona/IANA",
  "categories": ["…"],
  "goals": [{ "id": "…", "kind": "goal", "title": "…", "category": "…",
              "horizon": "day|week|month|quarter|year|deadline", "target": 3, "unit": "…",
              "deadline": null, "progress": { "2026-W40": 2 }, "createdAt": "…",
              "repo": null, "archived": false }]
}
```

Las claves de periodo (`YYYY-MM-DD`, `YYYY-Www` semana ISO, `YYYY-MM`, `YYYY-Qn`, `YYYY`, `once`) se calculan en la zona `timeZone` del archivo, así que el progreso se reinicia solo en cada periodo. `js/periodo.js` funciona también como CLI de Node: `node js/periodo.js --file objetivos.json`.

## Desarrollo

HTML + JS sin build, con `// @ts-check` y tipos JSDoc.

```bash
python3 -m http.server 8000   # abrir http://localhost:8000
node --test tests/            # pruebas de la lógica
```
