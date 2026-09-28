# Goals

A static PWA to track goals by horizon (daily, weekly, monthly, quarterly, yearly and with a deadline) and by category. Anyone can use it with **their own private data**.

## How to use it

1. Create a **private** GitHub repo for your data (or use one you already have).
2. Create a *fine-grained* token in GitHub → Settings → Developer settings → Fine-grained tokens:
   - *Repository access*: **Only select repositories** → that repo.
   - *Permissions* → *Contents*: **Read and write**. Nothing else.
3. Open the app, tap ⚙ and enter the token, your username, the repo, the file (default `goals.json`) and the branch. If the file doesn't exist, the app creates an empty one.
4. Create your categories (“Categories” button) and your goals. On a phone you can install it as an app.

## Privacy

- The site has no server: your browser talks only to `api.github.com` (strict CSP, no third-party scripts).
- The token and a copy of your data are stored only in your browser's local storage.
- This repo contains code only: no categories, goals or anyone's data.

## Data format

```json
{
  "version": 1,
  "timeZone": "Area/City",
  "categories": ["…"],
  "goals": [{ "id": "…", "kind": "goal", "title": "…", "category": "…",
              "horizon": "day|week|month|quarter|year|deadline", "target": 3, "unit": "…",
              "deadline": null, "progress": { "2026-W40": 2 }, "createdAt": "…",
              "repo": null, "archived": false }]
}
```

Period keys (`YYYY-MM-DD`, `YYYY-Www` ISO week, `YYYY-MM`, `YYYY-Qn`, `YYYY`, `once`) are computed in the file's `timeZone`, so progress resets automatically every period. `js/periodo.js` also works as a Node CLI: `node js/periodo.js --file goals.json`.

## Development

Plain HTML + JS, no build step, with `// @ts-check` and JSDoc types.

```bash
python3 -m http.server 8000   # open http://localhost:8000
node --test tests/            # logic tests
```
