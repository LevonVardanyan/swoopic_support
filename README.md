# Swoopic website

Static support / marketing / legal site for the Swoopic app, served at
**https://swoopic.zazavoxbox.com**. The API lives on its own subdomain,
**https://swoopicapi.zazavoxbox.com** (mirrors the mindstock/mindstockapi split).

Pages: `index.html` (landing), `support.html`, `privacy.html`, `terms.html`,
`delete-account.html`.

## Hosting

Unlike mindstock-web (GitHub Pages), this site is hosted on the VPS:

- Repo is cloned at `/opt/swoopic-web` on `root@173.249.9.31`.
- The `swoopic-api` nginx vhost serves this folder at `/` on
  swoopic.zazavoxbox.com. It still proxies `/v1/*`, `/healthz`, `/docs`,
  `/openapi.json` to the API container (127.0.0.1:8010) as a transition
  shim for app builds made before the API moved to swoopicapi — safe to
  remove once no such builds are in use.
- The `swoopicapi` nginx vhost is the canonical API entry
  (swoopicapi.zazavoxbox.com → 127.0.0.1:8010).

## Deploy

```bash
git push
ssh root@173.249.9.31 'cd /opt/swoopic-web && git pull'
# no reload needed — nginx serves the files directly
```
