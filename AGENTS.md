# Project: grantbenjamin.github.io

Personal academic website for Grant Benjamin, hosted on GitHub Pages. Built on Jekyll with the **Minimal Mistakes** theme loaded as a `remote_theme` (`mmistakes/minimal-mistakes` in `_config.yml`).

## Critical implication of `remote_theme`

Layouts (`default`, `single`, `home`, `archive`, etc.) and most `_includes/*.html` are **NOT in this repo** — they are fetched from the gem at build time. Only files explicitly overridden locally exist here. To inspect a layout or include the user references but you can't find, fetch it from the upstream theme:

- Layouts: `https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_layouts/<name>.html`
- Includes: `https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_includes/<name>.html`

Use `curl` (not WebFetch — it summarizes instead of returning raw HTML).

## Where things live

- `_config.yml` — site title, URL, social handles, theme, skin (`minimal_mistakes_skin: custom`), markdown engine.
- `_data/navigation.yml` — top nav menu items (Home, Research, Vita).
- `_pages/` — non-post content: `home.md`, `research.md`, `404.md`, archive pages. Front matter `header.image` sets the hero image (e.g. `/assets/images/yukon4.jpeg`).
- `_posts/` — blog posts (mostly theme demo content from 2010 / a 2019 welcome post).
- `_includes/head.html` — local override of theme `head.html` (loads `main.css`, FontAwesome, academicons).
- `_sass/minimal-mistakes.scss` — partial-import manifest (mirrors upstream).
- `_sass/minimal-mistakes/` — full local copy of theme SCSS partials (`_masthead.scss`, `_navigation.scss`, `_page.scss`, `_variables.scss`, `_base.scss`, `_reset.scss`, etc.) and `skins/_custom.scss` (the active skin).
- `assets/css/main.scss` — Jekyll entry SCSS; imports the active skin then `minimal-mistakes`.
- `assets/images/` — photos and hero images (`yukon4.jpeg` is the home hero).
- `documents/` — CV PDF served at `/documents/GrantBenjaminPhDCV.pdf`.

## Where to edit common things

- **Header bar / nav** styling → `_sass/minimal-mistakes/_masthead.scss` and `_sass/minimal-mistakes/_navigation.scss` (`.greedy-nav`).
- **Header text size** → `font-size` on `.masthead__inner-wrap` (cascades to nav links and `.site-title`).
- **Header bar height** → padding on `.masthead__inner-wrap` + `min-height` on `.greedy-nav` (default `$nav-height: 2em` in `_variables.scss`).
- **Space below header** → `.masthead { border-bottom, margin-bottom }` and `.page__hero { margin-top }` in `_page.scss`.
- **Hero image behavior** → `.page__hero` / `.page__hero-image` in `_sass/minimal-mistakes/_page.scss`.
- **Colors / skin** → `_sass/minimal-mistakes/skins/_custom.scss`.
- **Typography scale** → `$type-size-*` and `$h-size-*` in `_sass/minimal-mistakes/_variables.scss`. Body font is `1em` and html scales 16→17px across breakpoints (`_reset.scss`). Headings are semibold 600 (`_base.scss`), site title too (`_masthead.scss`).
- **Nav menu items** → `_data/navigation.yml`.
- **Home page copy** → `_pages/home.md`.

## Conventions

- Variables in `_variables.scss` use `!default`, so they can be overridden by defining them earlier (e.g. before the `@import "minimal-mistakes"` in `assets/css/main.scss`).
- Don't edit theme partials at the gem — edit the local copies in `_sass/minimal-mistakes/`. They take precedence.
- The site is published from `master` to GitHub Pages; pushing to `master` is the deploy.
