# Swoopic website

Static support / marketing / legal site for the Swoopic app, served at
**https://swoopic.zazavoxbox.com** (same domain as the API).

Pages: `index.html` (landing), `support.html`, `privacy.html`, `terms.html`,
`delete-account.html`.

## Hosting

Unlike mindstock-web (GitHub Pages), this domain also serves the Swoopic API,
so the site is hosted on the VPS behind the same nginx vhost:

- Repo is cloned at `/opt/swoopic-web` on `root@173.249.9.31`.
- The `swoopic-api` nginx vhost serves this folder at `/` and proxies
  `/v1/*`, `/healthz`, `/docs`, `/openapi.json` to the API container
  (127.0.0.1:8010).

## Deploy

```bash
git push
ssh root@173.249.9.31 'cd /opt/swoopic-web && git pull'
# no reload needed — nginx serves the files directly
```
