# textlings.app

The Textlings website. Plain static HTML/CSS — no build step, no framework,
no trackers (the app's privacy promise extends to its website).

## Hosting & deployment

GitHub Pages, deploy-from-branch. Pushing to `main` IS the deploy.

One-time setup:

1. Create the GitHub repo (`textlings-site`, public) and push this folder.
2. Repo **Settings → Pages** → Source: "Deploy from a branch" → `main` / root.
3. Custom domain: `textlings.app` (the `CNAME` file in this repo keeps it
   pinned). Wait for the certificate check, then tick **Enforce HTTPS**
   (mandatory anyway — the whole `.app` TLD is HSTS-preloaded).
4. GitHub **account Settings → Pages → Verified domains**: verify
   `textlings.app` (prevents domain-takeover if the repo ever moves).

DNS records at the registrar:

| Type  | Host | Value |
|-------|------|-------|
| A     | @    | 185.199.108.153 |
| A     | @    | 185.199.109.153 |
| A     | @    | 185.199.110.153 |
| A     | @    | 185.199.111.153 |
| AAAA  | @    | 2606:50c0:8000::153 |
| AAAA  | @    | 2606:50c0:8001::153 |
| AAAA  | @    | 2606:50c0:8002::153 |
| AAAA  | @    | 2606:50c0:8003::153 |
| CNAME | www  | cz140.github.io |

Propagation is usually minutes, can be hours. The Pages cert issues itself
once the A records resolve.

## Planned structure

```
index.html        landing: what it is, screenshots, download buttons
download/         installer + Pi image (links to GitHub release assets)
packs/            store pages — one per pack, itch.io buy widget embedded
                  (itch stays merchant of record; see the embed snippet on
                  each pack's itch dashboard → "Distribute" → widget)
gallery/          points at the community gallery (in-app + repo link)
```

Rules: static files only, system fonts or one self-hosted font, no
analytics/trackers/cookies, every page works with JS disabled (the itch
widget iframe being the one exception, with a plain link fallback).
