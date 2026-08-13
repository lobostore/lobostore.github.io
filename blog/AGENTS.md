# AGENTS.md

Hugo static site (affiliate marketing storefront, "LOBO STORE"). No theme, no build tooling beyond Hugo itself, no tests, no CI.

## Commands

- Dev server: `hugo server` → http://localhost:1313 (hot reload).
- Production build: `hugo --minify` → writes `public/`.
- **Requires Hugo Extended.** The CSS pipeline (`assets/css/main.scss` via `toCSS`) only works with the Extended edition; standard `hugo` errors out.

## Runtime testing (required)

`hugo` build/`--quiet` only catch template *syntax*. To catch runtime errors (nil fields, wrong types), actually render pages:

```
hugo server --port 1313 --bind 127.0.0.1
# then curl / , /produtos/ , /produtos/mouse/
```

Every change under `layouts/` must be verified by rendering (build or server), not just by eyeballing the template.

## Content model

- Products are one Markdown file each in `content/produtos/` (section title in `content/produtos/_index.md`).
- To add a product, drop a `.md` with these front-matter fields:
  - `title`, `summary`, `price` (display string, e.g. `"$99,99"`), `old_price` (optional), `image` (`/images/<name>.svg`), `featured` (bool), `specs` (YAML list), `link_afiliado` (affiliate URL).
- `link_afiliado` is the critical field: `layouts/_default/single.html` injects it into the "COMPRAR NA AMAZON" CTA button's `href`. Placeholder tag is `lobostore-20`; replace with the real ID before shipping.

## Layouts (no theme)

- `layouts/_default/baseof.html` is the shell; `partials/` holds `head`, `header`, `footer`, `product-card`.
- Homepage grid = `layouts/index.html` (ranges `where .Site.RegularPages "Section" "produtos"`). Section grid = `layouts/_default/list.html` (ranges `.Pages`). Both reuse `partials/product-card.html`.
- Product detail = `layouts/_default/single.html`.
- `featured: true` renders a dashed accent border + "Destaque" badge on the card.
- Store logo is `static/images/lobostore.png` (referenced from `partials/header.html`); the other `static/images/*.svg` are placeholders.

## Gotchas

- `config.toml` sets `disableKinds` (no RSS/sitemap/taxonomy/404/robotsTXT) and `markup.goldmark.renderer.unsafe = true` (raw HTML in content). Don't remove without reason.
- Hugo ≥0.158 deprecates `languageCode`; this repo uses `defaultContentLanguage` + `locale`.
- `public/` and `resources/` are generated; never hand-edit them. No `.gitignore` exists yet.
- `baseURL` is `https://lobovit.github.io/lobostore/` (GitHub Pages project site); deploy via `.github/workflows/hugo.yaml`.
