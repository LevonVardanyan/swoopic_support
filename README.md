# Swoopic website

Static support / marketing / legal site for the Swoopic app, served at
**https://swoopic.zazavoxbox.com**. The API lives on its own subdomain,
**https://swoopicapi.zazavoxbox.com** (mirrors the mindstock/mindstockapi split).

Pages: `index.html` (landing), `support.html`, `privacy.html`, `terms.html`,
`delete-account.html`.

## Hosting (GitHub Pages, same as mindstock-web)

- DNS: `swoopic` CNAME → `levonvardanyan.github.io`.
- Repo → Settings → Pages → Source: `main` branch, root (`/`); the `CNAME`
  file here sets the custom domain. Enable "Enforce HTTPS" once the
  certificate is issued.
- The API is separate: `swoopicapi.zazavoxbox.com` (nginx vhost `swoopicapi`
  on the VPS → 127.0.0.1:8010).

## Deploy

```bash
git push   # GitHub Pages redeploys automatically
```
