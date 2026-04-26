# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal blog/portfolio site for Alberto Diéguez, built by forking the [Chirpy Jekyll Theme](https://github.com/cotes2020/jekyll-theme-chirpy) (v6.4.1). The site is deployed to GitHub Pages via GitHub Actions on every push to `main`.

## Commands

### Install dependencies

```bash
bundle install   # Ruby/Jekyll gems
npm install      # Node.js build tools
```

### Local development

```bash
bash tools/run                          # Serves at http://0.0.0.0:4000 with live reload
bundle exec jekyll s                    # Alternative: serve without live-reload binding
```

### Build

```bash
npm run build                           # Build JS assets (outputs to assets/js/dist/)
npm run watch                           # Watch and rebuild JS assets
JEKYLL_ENV=production bundle exec jekyll b  # Build site to _site/
```

### Lint / test

```bash
npm test                                # Lint SCSS with stylelint
npm run fixlint                         # Auto-fix SCSS lint issues
bash tools/test                         # Build site + run html-proofer
```

## Architecture

### Theme structure

This repo is a **fork** of the Chirpy theme, not a Chirpy Starter site. The full theme source is present here alongside site content:

- **`_sass/`** — SCSS source. `addon/variables.scss` contains theme design tokens; `variables-hook.scss` is for local overrides without touching upstream files. `colors/` holds dark/light mode palettes.
- **`_javascript/`** — JS source modules (not served directly). Built via Rollup into `assets/js/dist/`.
  - Entry points: `commons.js`, `home.js`, `categories.js`, `misc.js`
  - `commons/` — small feature scripts imported by `commons.js`
  - `modules/components/` — reusable UI components (clipboard, image popup, etc.)
- **`_includes/`** — Liquid partials. `js-selector.html` and `css-selector.html` control which assets load per layout.
- **`_layouts/`** — Page layouts (referenced by front matter).
- **`_data/locales/`** — UI string translations (`en.yml`, `es.yml`, `zh-CN.yml`, `id-ID.yml`). Site is configured for Spanish (`lang: es`).

### Content

- **`_posts/`** — Blog posts in Markdown, named `YYYY-MM-DD-title.md`.
- **`_tabs/`** — Top-level navigation pages (`sobre-mi.md`, `categorias.md`, `archivos.md`, `tags.md`). Rendered as sidebar links.
- **`_data/contact.yml`** — Sidebar contact/social icons.

### Configuration

`_config.yml` is the primary configuration file. Key settings already customized for this site:
- `lang: es`, `timezone: Europe/Madrid`
- `jekyll-archives` configured with Spanish URL slugs (`/categorias/:name/`, `/tags/:name/`)
- `theme: jekyll-theme-chirpy` (gem reference, though gemspec is also present since it's a fork)

### Deployment

Pushing to `main` triggers `.github/workflows/pages.yml`, which builds with `JEKYLL_ENV=production` and deploys to GitHub Pages. The `ci.yml` workflow runs on all non-production pushes and also builds JS assets (`npm i && npm run build`) before testing with `html-proofer`.

**Important**: JS assets in `assets/js/dist/` must be built before Jekyll can serve properly. In CI this is handled automatically; locally run `npm run build` if you see missing JS.
