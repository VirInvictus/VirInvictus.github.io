# CLAUDE.md

Guidance for any coding agent working in this repository.

## What this is

`VirInvictus.github.io` is Brandon's personal site, served by **GitHub Pages** as a Jekyll site. There is no `Gemfile`; the build runs on GitHub Pages' pinned Jekyll stack on every push to `main`. **Every push is a deploy**: a Liquid error takes the whole site down, so check the Pages build after every push (`gh run list -R VirInvictus/VirInvictus.github.io --limit 1`). A broken deploy is reverted, not debugged live.

The site is titled **Vir Invictus**, *the unconquered*. It reads as a private codex / archival notebook: editorial typography on a locked Kanagawa Dragon palette. No JavaScript, no build script, no test suite.

## Architecture

There is **no theme**: `_config.yml` sets none, and every layout and style is owned in this repo. (The old `jekyll-theme-minimal` line was removed once every page came onto repo layouts; do not re-add a theme without a reason.)

- `_config.yml\`: \`title`, `description`, canonical `url`, `lang`, author/social metadata, the two opt-in plugins (`jekyll-seo-tag`, `jekyll-sitemap`), and the exclude list. **The exclude list must keep BOTH `CLAUDE.md` and `AGENTS.md`** with the explanatory comment: the build ignores the `CLAUDE.md` exclude when the same content also appears under the name `AGENTS.md`, tries to render it as a page, and Liquid dies on its raw content (`'for' tag was never closed`), failing the deployment.
- `README.md`: the landing page (front matter `layout: default`, `permalink: /`). Structure: the masthead (`<header class="masthead">`, the framed `VIR · INVICTVS` lockup with `Ex libris Brandon LaRocque` beneath), the sigils strip (`<p class="sigils">`: *programmer · curator · former chef*), § I On the Author (long-form prose opening with a `.dropcap` paragraph), § II The Collection (category-grouped card grids plus the shelf line), § III Dispatches (Liquid `{% for post in site.posts %}` over `<ul class="post-list">`).
- **Cards** in § II: a `<div class="codex-grid">` wrapping `<div class="codex-card">` blocks. Each card is pure HTML in the markdown source: `card-header` with `codex-num` (`No. NNN`, the curated shelf number), an `h3` title link, `codex-meta` (stack tokens joined by `<span class="stack-sep">·</span>` plus a status span), an optional `codex-plate` screenshot, `card-desc`, and a `card-link-container` "View Details" link. No `markdown="1"` is involved.
- `codex/*.md`: one detail page per project. Front matter: `layout: codex`, `title:`, `description:` (plain text only; it feeds the meta description tag, so no markdown links), `permalink: /codex/<slug>/`. Body shape: the `codex-meta` status line first, an optional `codex-plate`, prose, and a closing `codex-link` paragraph. **Two asymmetric slugs by design**: `codex/bindery-cli.md` serves `/codex/bindery/` and `codex/lattice-music.md` serves `/codex/lattice/`. Pages carry no numbering; in-body cross-links use absolute paths (`/codex/<slug>/`).
- `_layouts/default.html`: the shell: a hand-rolled `<title>` (jekyll-seo-tag runs with `title=false`; the comment in the file explains why), `theme-color` + favicon + feed `alternate` links, Google Fonts, `<main class="codex">`, and the colophon footer.
- `_layouts/codex.html`: extends default: the "From the collection" header and the back-link to `/#the-collection`.
- `_layouts/post.html`: extends default: the "From the marginalia" chapter line, title, date, and the back-link to `/#dispatches`.
- `_posts/YYYY-MM-DD-slug.md\`: \`layout: post`, `title:`. The filename date controls ordering.
- `feed.xml`: hand-rolled Atom over `site.posts` (`layout: null`). Deliberately not the jekyll-feed plugin: plugin additions are ask-first in this workspace, and keeping the plugin list opt-in is the house style.
- `404.html`, `robots.txt`, `assets/img/favicon.svg`, `assets/img/og-card.png`: the static plumbing: a themed not-found page on the default layout, the sitemap declaration for crawlers, the hand-drawn VI monogram favicon, and the 1200x630 link-preview card, set as `image:` in every page's front matter (jekyll-seo-tag reads page.image and ignores a site-level key).
- `assets/css/style.scss`: all styling. The leading `---`\n`---` front matter is required for Jekyll to compile the SCSS; do not remove it. Kanagawa Dragon tokens live in `:root` (`--paper #d4cfb8`, `--peach #b6927b`, and the rest). **Source Serif 4** for prose and headings, **IBM Plex Mono** for chrome, dates, statuses, and code. The `§ ` heading prefix renders via `h2::before`; ornaments are `❦` (fleuron, in-section) and `⁂` (asterism, between-sections); the `hr` element renders `⁂`.

The status vocabulary for `codex-meta` spans: `status` (green, active), `status--shipping` (peach), `status--complete` (teal), `status--design` (mauve). `status--wip` (yellow) and `status--retired` (grey) are defined but unused: they are the reserved half of the designed vocabulary. Keep them; do not flag them as dead CSS.

## Conventions

- **New project**: create `codex/<slug>.md` (structure above) AND add a card to the matching category grid in README § II. The card's `No. NNN` takes the next sequential shelf number; the codex page itself carries no number. Every page without a card must appear in the shelf line ("The rest of the codex"), or it is an orphan.
- **New blog post**: `_posts/YYYY-MM-DD-slug.md` with front matter `layout: post` and a `title:`. The post layout frames it; do not include a masthead in post content.
- **Status colours** are wired in `style.scss`; use the existing class names, and a new status means adding its colour.
- **Colour / typography changes** go in `assets/css/style.scss`. The palette is locked to Kanagawa Dragon: match the existing tokens rather than introducing new ones.
- **Version strings are claims.** Before pushing any card or page touch, grep each edited version against the live repo's own source (its `VERSION` file, `Cargo.toml`, `pyproject.toml`, or `meson.build`); stack tokens in `codex-meta` lines are claims too.
- **Hand-written voice.** Posts and codex prose are Brandon's long-form writing: update facts, never rewrite prose wholesale, ship corrections as dated postscripts (posts) or minimal fact edits (cards and pages), and draft any new long-form content for his review.
- **No em-dashes anywhere rendered** (posts, cards, codex pages, commit messages). EN-dashes in numeric ranges are correct.
- **Internal links must resolve** to real permalinks (mind the two asymmetric slugs), and `assets/img/*.webp` references must point at files that exist.
- **Do not commit or push on Brandon's behalf** unless he explicitly asks. (A blitz lane with a push grant still batches content updates into reviewed commits and verifies each Pages build.)

## Local preview

GitHub Pages builds on push, so most edits are validated by pushing. To preview locally before pushing:

```sh
bundle init && bundle add jekyll github-pages   # one-time
bundle exec jekyll serve                         # http://127.0.0.1:4000
```

No `Gemfile` is committed; ask before adding one.
