# punkfab.com

Landing page for **PUNKFAB** — software-defined fabrication.

A single self-contained static page (`index.html`, no build step), hosted on
DigitalOcean App Platform as a static site.

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Deploy (DigitalOcean App Platform)

Static site from this repo; `deploy_on_push` is on, so pushing to `main` redeploys.

```bash
doctl apps create --spec .do/app.yaml           # first deploy
doctl apps list                                 # find the app id + live URL
doctl apps update <APP_ID> --spec .do/app.yaml  # redeploy from spec
```

## Custom domain — punkfab.com

1. Add the domain to the app (DO dashboard → app → Settings → Domains, or edit the spec).
2. Point DNS at the app, keeping your registrar's nameservers:
   - `punkfab.com` (apex) → **A / ALIAS** record to the app's ingress, or a CNAME if the
     registrar supports apex CNAME/flattening.
   - `www.punkfab.com` → **CNAME** → the app's `…ondigitalocean.app` hostname.
   DO shows the exact target under the domain once it's added.
3. TLS is issued automatically once DNS resolves.

## Content

Copy and the `hello@punkfab.com` address are first-draft — edit `index.html` directly.
