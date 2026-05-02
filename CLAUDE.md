# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`VirInvictus.github.io` — Brandon's personal site / blog ("A Second Cup"), served by **GitHub Pages** as a Jekyll site using the `jekyll-theme-minimal` theme. There is no `Gemfile`; the build runs on GitHub Pages' pinned Jekyll stack on push to `main`.

## Architecture

The site is a "terminal-window" themed page rendered by Jekyll. The minimal theme is still set in `_config.yml` as a fallback, but **all layouts and styles are overridden in this repo** — the minimal theme's chrome is not used.

- `_config.yml` — sets `theme: jekyll-theme-minimal`, site title, description.
- `README.md` — the landing page. Has front matter (`layout: default`) and is structured as a fake shell session: `## whoami`, `## ls -l projects/`, `## cat projects/<name>/README.md`, `## ls _posts/`, etc. CSS prepends `$ ` to every h2 to render headings as prompts. The Liquid `{% for post in site.posts %}` block renders the post list. **Editing the README changes the homepage.**
- `_layouts/default.html` — wraps `{{ content }}` in a fake terminal window: titlebar with three traffic-light dots, centered `bdkl@fedora: ~ — zsh` title, and a trailing prompt line with a blinking peach cursor. Loads `style.css`.
- `_layouts/post.html` — extends `default`, prepends a `cat <slug>.md` command line, renders title + date, and adds a `cd ..` link back to the index.
- `_posts/YYYY-MM-DD-slug.md` — blog entries with `layout: post`, `title:`. Filename date controls ordering.
- `assets/css/style.scss` — Catppuccin Mocha palette (peach `#fab387` accent), IBM Plex Mono everywhere. The leading `---\n---` front matter is required for Jekyll to process the SCSS; do not remove it. The blinking cursor is `.cursor` driven by the `blink` keyframes (a `prefers-reduced-motion` block disables it).

No JavaScript, no build script, no test suite. GitHub Pages builds Jekyll on push.

## Local preview

GitHub Pages builds on push, so most edits are validated by pushing. To preview locally before pushing:

```sh
bundle init && bundle add jekyll github-pages   # one-time
bundle exec jekyll serve                         # http://127.0.0.1:4000
```

The user has not committed a `Gemfile`; ask before adding one.

## Conventions

- New blog post: create `_posts/YYYY-MM-DD-slug.md` with front matter `layout: post` and a `title:`. Use the existing `2026-04-16-welcome.md` as the template.
- Color/typography changes go in `assets/css/style.scss`. Match the existing palette (charcoal `#121212`, body `#d1d1d1`, orange accent `#ff8c00`, hover `#ffa500`) rather than introducing new tokens.
- Do not commit or push on Brandon's behalf unless he explicitly asks (per `~/CLAUDE.md` §7, §14).
