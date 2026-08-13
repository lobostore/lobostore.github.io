# AGENTS.md

Hugo static site — "LOBO STORE", an affiliate storefront with pt-BR content. The Hugo project lives in `blog/`, not at the repo root.

## Layout

- `blog/` — the actual Hugo project (`config.toml`, `content/`, `layouts/`, `assets/`, `static/`). Read `blog/AGENTS.md` first; it has the full commands, content model, and layout reference.
- Root-level `index.html`, `css/`, `images/`, `produtos/` — generated Hugo build output (a copy of `public/`), not source. Never hand-edit; they're overwritten on every build.
- `blog/.opencode/skills/product-description/` — skill for authoring `blog/content/produtos/*.md`.

## Commands (run from `blog/`)

- `hugo server` — dev server, hot reload at http://localhost:1313
- `hugo --minify` — production build → `blog/public/`
- Requires Hugo **Extended** (SCSS `toCSS` pipeline fails on the standard edition). v0.161.1 extended is installed locally.

## Gotchas

- Content is pt-BR; keep all copy in Brazilian Portuguese.
- `blog/public/` and `blog/resources/` are generated and gitignored — don't commit or edit them.
- `baseURL` = `https://lobostore.github.io/` (GitHub Pages org site), so generated URLs are absolute at the root (`/`, not `/lobostore/`).
- Deploy: repo-root `.github/workflows/hugo.yaml` builds `blog/` (`cd blog`) and uploads `blog/public/`. Workflows only trigger from the repo-root `.github/workflows/`.
