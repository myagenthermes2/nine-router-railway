# 9Router on Railway — One-Click Deploy

Self-hosted AI gateway ([decolua/9router](https://github.com/decolua/9router)):
one OpenAI-compatible endpoint (`/v1`) in front of 40+ providers,
with dashboard, combos, quota tracking and SQLite persistence on a Railway volume.

[![Deploy on Railway](https://railway.com/button.svg)](https://railway.com/deploy?repoUrl=https://github.com/myagenthermes2/nine-router-railway)

## Deploy (1 click)

1. Click **Deploy on Railway** above.
2. Railway generates `INITIAL_PASSWORD`, `JWT_SECRET`, `API_KEY_SECRET`, `MACHINE_ID_SALT` automatically.
3. Open the service URL → login with `INITIAL_PASSWORD` (from Variables tab).
4. Set your own password under Profile, add providers, create an API key under Endpoint.
5. Point any OpenAI-compatible client at `https://<your-service>.up.railway.app/v1`.

## What gets provisioned

- Image: `decolua/9router:latest`
- Volume: `nine-router-volume` → `/app/data` (SQLite db, backups, catalog survive redeploys)
- Healthcheck: `/api/health`
- Public domain: auto-generated

## Manual deploy (CLI)

```bash
railway init -n nine-router
railway add -s nine-router -i decolua/9router:latest
# add volume /app/data, set variables from railway.json, deploy
```
