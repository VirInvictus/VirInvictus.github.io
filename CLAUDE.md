# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`VirInvictus.github.io` — Brandon's personal site, served by **GitHub Pages** as a Jekyll site under the `jekyll-theme-minimal` fallback. There is no `Gemfile`; the build runs on GitHub Pages' pinned Jekyll stack on push to `main`.

The site is titled **Vir Invictus** — *the unconquered*. It reads as a private codex / archival notebook, not a terminal session. The previous terminal-window layout (titlebar, traffic-light dots, blinking cursor, `$ ` h2 prefixes) was retired in favour of editorial typography.

## Architecture

The minimal theme is still set in `_config.yml` as a fallback, but **all layouts and styles are overridden in this repo** — the theme's chrome is not used.

- `_config.yml` — `theme: jekyll-theme-minimal`, `title: Vir Invictus`, site description. The title threads through the `<title>` tag and the colophon footer.
- `README.md` — the landing page. Front matter `layout: default`. Structured as:
  1. **Masthead** (`<header class="masthead">`) — framed `VIR · INVICTVS` lockup with `Ex libris Brandon LaRocque` beneath.
  2. **Sigils strip** (`<p class="sigils">`) — six identity tokens: *curator · shadow librarian · coder · gamer · father · former chef* — bracketed by `❦` ornaments.
  3. **§ I. On the Author** — long-form personal prose, opens with a `.dropcap` paragraph.
  4. **§ II. The Collection** — numbered codex entries, one per project. Each entry uses `<div class="codex-entry">` with a left-column `codex-num` (`No. 001`) and a `codex-body` containing `### Title`, `<p class="codex-meta">` (stack + status), prose, and a `codex-link` paragraph.
  5. **§ III. Marginalia** — interests as a `<dl class="marginalia">` definition list.
  6. **§ IV. Writing** — Liquid `{% for post in site.posts %}` rendered through `<ul class="post-list">`.
- `_layouts/default.html` — minimal: `<main class="codex">{{ content }}</main>` plus a tiny colophon footer (`Source Serif 4 · IBM Plex Mono · Hosted by GitHub Pages · MMXXVI`). The masthead lives in the README, not the layout, so posts get a lighter chrome.
- `_layouts/post.html` — extends `default`. Adds a centered `post__header` with a `From the marginalia` chapter line, the title, and the post date. Closes with a centered `← Return to the codex` back-link.
- `_posts/YYYY-MM-DD-slug.md` — `layout: post`, `title:`. Filename date controls ordering.
- `assets/css/style.scss` — Kanagawa Dragon palette retained (`--peach #b6927b`, `--paper #d4cfb8`). **Source Serif 4** for body and headings (also bundled by Atrium — full circle), **IBM Plex Mono** for chrome, dates, statuses, and code. `§` heading prefix is rendered via `h2::before`. Section dividers are `❦` (fleuron) and `⁂` (asterism). The leading `---\n---` front matter is required for Jekyll to compile the SCSS; do not remove it.

No JavaScript. No build script. No test suite. GitHub Pages builds Jekyll on push.

## Local preview

GitHub Pages builds on push, so most edits are validated by pushing. To preview locally before pushing:

```sh
bundle init && bundle add jekyll github-pages   # one-time
bundle exec jekyll serve                         # http://127.0.0.1:4000
```

The user has not committed a `Gemfile`; ask before adding one.

## Conventions

- **New blog post:** create `_posts/YYYY-MM-DD-slug.md` with front matter `layout: post` and a `title:`. The post layout will frame it; do not include a masthead in post content.
- **New project entry on the index:** add a `<div class="codex-entry">` block in `README.md` § II, with the next sequential `No. 00X` number. Match the structure of existing entries — `codex-meta` line with stack tokens separated by `<span class="stack-sep">·</span>` and a status span (`status`, `status--shipping`, `status--wip`, `status--design`, or `status--complete`). The `codex-body` div needs `markdown="1"` so kramdown parses the prose inside.
- **Status colours** are wired in `style.scss` — green for *active*, peach for *shipping*, yellow for *wip*, mauve for *design*, teal for *complete*. Use the existing class names; don't introduce new statuses without adding the colour.
- **Colour / typography changes** go in `assets/css/style.scss`. The palette is locked to Kanagawa Dragon — match the existing tokens (`--paper`, `--peach`, `--surface0`, etc.) rather than introducing new ones.
- **Ornaments** — `❦` (fleuron) for in-section dividers, `⁂` (asterism) for between-section dividers. Both render via `<p class="ornament ornament--fleuron">` / `class="ornament ornament--asterism">` or via the `hr` element (which is styled to render `⁂`).
- **Do not commit or push on Brandon's behalf** unless he explicitly asks (per `~/CLAUDE.md`).
