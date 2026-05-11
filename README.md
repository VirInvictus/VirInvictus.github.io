---
layout: default
title: Vir Invictus
description: Brandon LaRocque. Programmer, curator, former chef. Native Linux desktop work in Rust and C, local-first by default.
permalink: /
---

<header class="masthead">
  <h1 class="masthead__title">VIR <span class="dot">·</span> INVICTVS</h1>
  <p class="masthead__exlibris">Ex libris Brandon LaRocque</p>
</header>

<p class="sigils">
  <span class="sigils__ornament">❦</span>
  programmer
  <span class="sigils__sep">·</span> curator
  <span class="sigils__sep">·</span> former chef
  <span class="sigils__ornament">❦</span>
</p>

## I. On the Author
{: #on-the-author}

<div markdown="1" class="dropcap">
My work is native Linux desktop software. Rust with GTK4, C built with Meson, Python where the standard library reaches. Local-first by default. SQLite on the user's disk in WAL mode, single-writer worker, read-only connection pool, FTS5 for search. No cloud accounts. No Docker. No Electron. No telemetry.
</div>

I prefer compile-time boundaries to code-review rules, and hard memory ceilings to optional benchmarks. I will port a battle-tested architecture with attribution before I invent a new one.

I came to the work late. Ten years in restaurants and mining camps before *The C Programming Language*. I read it at night, between shifts, because the cover looked serious and I wanted to know what serious looked like. A Computer Engineering Technician student now, with a CS bachelor's underway at Algoma. The credential follows the practice.

By temperament I am an archivist. I keep a private Calibre library that runs into the four figures, a music collection sorted by hand, an RSS spool I read every morning. Friends have called the practice *shadow librarianship*. The catalogue is my own, kept on my own disks, indexed by my own tools. Most of what I build is for the kind of person who treats their library as worth maintaining.

The site is named *Vir Invictus*, *the unconquered*. It is a working motto, not a brand.

<p class="ornament ornament--fleuron">❦</p>

## II. The Collection
{: #the-collection}

Nine projects. Native Linux desktop software and one Emacs theme. Local-first by default; the throughline is curation. Atrium is the largest and most active piece; the rest sort by current state.

<div class="codex-entry">
  <span class="codex-num">No. 001</span>
  <div class="codex-body" markdown="1">
### Atrium
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.21.0</span></p>

The native GNOME task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, all in a fast GTK4 surface that does not require Emacs to operate. **Simple Mode** for *what am I doing right now*: six canonical lists, no defer dates, Things 3 calm. **Builder Mode** for the days the system has to do the work: Forecast, Agenda, Kanban, Calendar Month View, Review, Perspectives, repeating tasks, sequential projects, an always-visible Inspector pane. Same data, two surfaces, no migration. Flipping modes is a UI re-render; the schema is the OmniFocus superset on day one.

Local-first SQLite at `$XDG_DATA_HOME/atrium/atrium.db`. Single-writer worker thread, WAL mode, read-only connection pool. FTS5-backed search using a hand-written **Calibre-style expression grammar**: `tag:work AND is:overdue sort:-due`, `due:2026-05-01..2026-05-31`, `tag:?wrok` for fuzzy match. Five crates in the Rust workspace: `atrium-core`, `atrium-search`, `atrium-cli`, `atrium-inline`, and the `atrium` binary. `atrium-inline` is the extracted inline-syntax engine — `#tag`, `@today`, `@deadline`, `!priority` with tab-completion — decoupled from the UI so the parser is tested headlessly. 888 tests across the workspace, 13 migrations, a 1K-fixture smoke and cold-start sanity check on every push.

The current shipping surface covers CLOCK time-tracking that round-trips to Org `:LOGBOOK:` drawers; Quick Entry templates with org-capture-style `:LETTER ` activation; custom TODO keyword sequences that round-trip through `#+TODO:` declarations; DEADLINE warning windows; statistics cookies for checkbox groups; a Todoist CSV importer built on stdlib parsers; system-notification reminders; and an in-app preferences dialog. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 002</span>
  <div class="codex-body" markdown="1">
### Viaduct
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v2.7.0</span></p>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary, making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** versus ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio. OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire. FTS5 full-text search. Three databases (articles, feed-settings, sync), all in WAL mode. Local + Inoreader accounts; Inoreader sync is a port of NetNewsWire's ReaderAPI engine. NetNewsWire-faithful parsing of RSS 2.0, RDF, Atom, JSON Feed, and RSS-in-JSON, with the permissive `RSDateParser` ported across.

Exactly one neutered WebKit instance for the article pane: JS, WebGL, WebRTC, DevTools, and LocalStorage all off; strict CSP; every image routed through a custom `viaduct-img://` URI scheme so the WebView never reaches the public internet directly. Ships all eight NetNewsWire article themes plus an Adwaita variant; the accent colour from the selected theme propagates across the GTK chrome (sidebar selection, focus rings, switches), beating GNOME's system-accent integration.

The v2.x line has built up the surface around the port: **Custom Smart Feeds** (rule-driven persistent saved searches, the first viaduct-original feature), an **Activity Log** dialog backed by a 500-entry refresh-event ring buffer, a **Send to** menu for the article pane (Email Link, Pocket, Instapaper, Copy URL with Title), a **first-launch welcome dialog** with a curated suggested-feed list, OPML import/export, Reader View, and adaptive `AdwBreakpoint` layout that collapses the three-pane split at 900sp / 600sp into mobile-style stacks. The v2.0 architectural plan (modular widget decomposition, dedicated `ArticleRenderer` GObject, expanded reactive properties) was informed by a careful read of [NewsFlash](https://gitlab.com/news-flash/news_flash_gtk), credited in the project's README. A background-daemon mode runs Viaduct as an XDG autostart agent and re-summons the window from a system tray icon via D-Bus, without a fresh startup sequence. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 003</span>
  <div class="codex-body" markdown="1">
### Hermitage
<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Libadwaita <span class="stack-sep">·</span> <span class="status">active · v0.15.0</span></p>

A local-first, native gallery for Calibre libraries. Built for the single user who wants a modern desktop experience without Docker containers or a web auth layer. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive tag-hierarchy genre browser that turns dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Calibre's Virtual Libraries, the full Calibre search-query language in the search bar (`Ctrl+F`), and a 512-entry texture LRU plus three-tier colour cache to keep scrolling smooth on integrated graphics. Ships with `hermitage-verify`, a standalone CLI that audits library integrity, cover presence, and format resolution. Zero telemetry, zero network calls, zero accounts.

A Flatpak manifest landed at v0.15.0 against the GNOME 50 platform: 8 MB installable, sandboxed `--filesystem=home`, arbitrary library paths reachable via the GNOME file-chooser portal. Brandon's app icon shipped at v0.14.0: a Fraunces-inspired serif H monogram on a deep aubergine card with a warm candlelight glow.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 004</span>
  <div class="codex-body" markdown="1">
### Lattice
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status">active · v4.3.4</span></p>

A toolkit for music collectors who keep the filesystem as the source of truth. Library tree visualization with artist / album / track / rating / genre. Parallel FLAC / MP3 / Opus / WAV / WMA integrity verification, shelling out to `flac -t` and `ffmpeg`. Embedded cover-art extraction with format-priority ranking (FLAC → Opus → M4A → MP3) and an art-quality audit against a configurable resolution floor. Tag, bitrate, and duplicate audits. Smart `.m3u` playlist generation from dynamic rules (`rating >= 4 and genre == 'Jazz'`). Per-genre **wings**: one library file per genre tag, like Calibre virtual libraries for music. A token-efficient `--ai-library` export sized to fit a 4,000-album collection inside an LLM context window. Configurable directory layout (`{genre}/{artist}/{album}` or whatever your library uses), so the tools don't fight you about your shelving.

The package itself is read-only by design: it reads tags, decodes audio, writes reports. Two destructive companions live alongside it at the repo root, deliberately outside the package boundary so the read-only contract holds.

`retag.py` is the universal genre rewriter. It abstracts the ID3 / Vorbis / iTunes-atom multi-genre chaos and cleanly consumes the absolute paths from `--all-wings --paths` for safe, bulk directory-level retagging.

`cleaner.py` (added 2026-05-04) is the fragmented-album-folder consolidator. When import metadata varies across sources, the same album can land in two sibling folders, with no track overlap, separated only by a curly vs straight apostrophe, an en-dash vs a hyphen, or a casing variant. `cleaner.py` walks the library, finds folders whose names normalize to the same key (curly→straight quotes, dash variants→ASCII hyphen, NFKC, lowercase, strip), picks the larger as canonical, and merges the rest in via `shutil.move`. Filesystem operations only, no audio bytes touched. Audio collisions where sizes differ keep both copies under a `.from-fragment` suffix, never auto-deleted. `--dry-run` previews every move; per-file logging to `<directory>/cleanup.log` is on by default. Idempotent on re-run.

Bare `lattice` launches a full-screen curses TUI with colour-coded section groups (Library, Integrity, Artwork, Metadata, Statistics, Settings).

<p class="codex-link"><a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 005</span>
  <div class="codex-body" markdown="1">
### Framework
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status">active · v0.21.0</span></p>

A native GNOME document viewer for **PDF, DjVu, CBZ, CBR, XPS, EPUB, FB2, and MOBI**. Designed to fill the gap between feature-heavy clients (Okular) and bare MuPDF wrappers; a SumatraPDF-shaped experience for Linux. Three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction (default 512 MB, tunable), parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline that constructs the MuPDF pixmap *around* the Cairo surface buffer.

A *velocity engine* throttles render-job dispatch by scroll speed so fast-scrolling never queues stale work; a `g_thread_pool` sort function reorders the queue by `last_view_time` so the viewport always wins; mid-render `fz_cookie` abort lets workers bail in milliseconds. Manga (RTL), Webtoon (zero-gap continuous strip), and facing-pages comic layouts, all live-toggleable, with both aspect-ratio and filename-based double-spread detection for scanlation rips. Async progressive search with cached structured text (332 ms cold → 48 ms warm on a 901-page textbook). Smart text selection: double-click selects a word, triple-click selects a line, drag follows reading order across line wraps. Magnifying loupe (F7) for circular zoom-around-cursor. `GFileMonitor` auto-reload: recompile a LaTeX or Typst doc and the viewer refreshes with scroll position preserved.

The v0.40+ line added a Foliate-style reflow architecture for EPUB / MOBI / FB2 with a `GListModel` of structurally-typed blocks, EPUB OPF spine walker, FB2 walker, MOBI / KF7 / KF8 / AZW3 parser including HuffDic decompression. Process-scoped Linux **Landlock LSM** sandbox at startup drops filesystem `EXECUTE` and `MAKE_*` rights so a malicious document exploiting MuPDF / DjVuLibre / libarchive into RCE cannot escalate to spawning a shell. Strictly a viewer: no annotations, no library, no conversion. Every borrowed pattern (SumatraPDF, zathura-pdf-mupdf, Sioyek, YACReader, Foliate, MComix, Komikku, Plato) is named and attributed in the README with upstream `file:line`. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 006</span>
  <div class="codex-body" markdown="1">
### CalibreQuarry
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v2.6.0</span></p>

A CLI toolkit for power users of Calibre. Zero external dependencies: `sqlite3`, `argparse`, `curses`, and nothing else. Ships a hand-written recursive-descent parser at **100% parity with Calibre's internal search-expression syntax**, validated by an automated test suite mapped against Calibre's own `SearchQueryParser`. The same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` CLI mode (with full author / `vl:` / boolean / parens / `=`-prefix exact-match support).

Catalog generation grouped by author. `--all-wings` emits a separate catalog for every virtual library. Library statistics with format breakdown, rating distribution, tag taxonomy, top authors, top tags. **Extended audit** modes: untagged, unrated, coverless, series-gap, duplicate-title-and-author, low-resolution covers (parses on-disk JPEGs without external libraries), legacy-format migration flags. **Extended analytics** modes: `author` (per-author breakdowns), `pace` (added-per-month trend), `tags` (hierarchical taxonomy tree), `overlap` (virtual library wing overlap). `--tags` is a flat alphabetized tag dump with book counts, dropping in for `calibredb list_categories -r tags`. JSON / CSV / AI exports. Custom-column extraction. Auto-snapshots the database when Calibre holds a write lock. Installs as `cquarry`. Considered complete software, fully tested on Fedora 43 against Calibre 9.7.

<p class="codex-link"><a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 007</span>
  <div class="codex-body" markdown="1">
### deadbeef-cui
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.0</span></p>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full DeaDBeeF title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, an in-pane search bar (`Ctrl+Shift+F`), and a settings dialog with per-instance configuration (column titles, formats, split tags) so multiple Facet Browsers can coexist in one layout with different settings.

The v1.3.0 release wired in the standard DeaDBeeF track context menu: right-clicking any facet row exposes Play Next / Play Later / Properties / Convert / Reload metadata and any other plugin-contributed track actions, alongside the facet-specific items. Tracks can be dragged out of facet rows onto playlist tabs, using the same `DDB_PLAYITEM_POINTERLIST` payload format the GTKUI medialib widget uses. A new "Send to new playlist `<row name>`" item names the destination playlist after the right-clicked tag. Targets a dedicated "Library Viewer" playlist so the plugin never touches the user's curated playlists. Built natively against `DB_mediasource_t`. Effectively complete; fixes only from here.

<p class="codex-link"><a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 008</span>
  <div class="codex-body" markdown="1">
### project-void
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> Tiled <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

A design-stage CRPG and the data-driven engine that ships under it. The engineering commitment is the engine: rules expressed as universal TOML/Lua state machines, decoupled from the renderer, so the same binary could host *Cairn*, 5e, or any other system with a sheet and a turn order. The campaign is the demonstration. **The Reach** is a tight 15–20-hour run through a region of city-states, free companies, counting houses, an inquisition, and a ruined library-city.

Lethal *Cairn*-derived combat math: attacks hit automatically, HP is low, damage drains into real wounds via attribute damage. Combat as a positional puzzle, not a dice minigame.

<p class="codex-link"><a href="https://github.com/VirInvictus/project-void">github.com/VirInvictus/project-void →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 009</span>
  <div class="codex-body" markdown="1">
### kanagawa-dragon-nvim-emacs
<p class="codex-meta">Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.x</span></p>

A faithful Emacs port of the Dragon variant from [kanagawa.nvim](https://github.com/rebelot/kanagawa.nvim). Not a repackaging of the existing `kanagawa-themes` package — the existing package has the palette right but covers too few faces to hold up in practice. This one maps the full set: every Emacs 29+ tree-sitter `font-lock-*` face, all Doom-specific surfaces (`doom-modeline-*`, `solaire-mode`, `doom-dashboard-*`), org-mode faces, magit, company, corfu, and the rest of the usual zoo. Implemented as a vanilla `deftheme` with no `doom-themes` macro dependency, so it works in stock Emacs and in Doom alike.

An ERT test suite checks palette byte-for-byte parity against the upstream nvim theme and validates representative face attributes. The acceptance criterion is visual: `sample.java` in Doom at `treesit-font-lock-level 4` should match the same file in nvim with `:colorscheme kanagawa-dragon`.

<p class="codex-link"><a href="https://github.com/VirInvictus/kanagawa-dragon-nvim-emacs">github.com/VirInvictus/kanagawa-dragon-nvim-emacs →</a></p>
  </div>
</div>

<p class="ornament ornament--asterism">⁂</p>

## III. Marginalia
{: #marginalia}

Off-screen taste. Most of the projects above trace back to one collection or another.

<dl class="marginalia">
  <dt>Reading</dt>
  <dd>10–20 books a year. Grimdark fantasy, cyberpunk, horror. Authors I return to: <strong>Joe Abercrombie</strong>, <strong>Brandon Sanderson</strong>, <strong>Morgan Housel</strong>, <strong>Terry Pratchett</strong>. Shelf at <a href="https://www.goodreads.com/user/show/125925803-brandon-larocque">Goodreads</a>.</dd>

  <dt>Collecting</dt>
  <dd>TTRPGs. The Calibre library runs deep here: OSR (Old School Essentials, Carcosa, Mothership), Forged in the Dark (Blades in the Dark and its extended family), World of Darkness, Shadowrun, the classic AD&D and Dark Sun lines. Drawn less to the play and more to the engineering — games that keep real ideas behind their front pages.</dd>

  <dt>Music</dt>
  <dd>Hip-hop, emo, orgcore. The collection runs into four figures across 86 genre wings: abstract rap (<strong>Aesop Rock</strong>, <strong>Armand Hammer</strong>, <strong>Earl Sweatshirt</strong>), hardcore hip-hop (the Griselda family, <strong>Ka</strong>, <strong>Billy Woods</strong>), emo and post-hardcore (<strong>Brand New</strong>, <strong>The Menzingers</strong>, <strong>Self Defense Family</strong>, <strong>Drug Church</strong>), orgcore (<strong>Jeff Rosenstock</strong>, <strong>Propagandhi</strong>, <strong>Jawbreaker</strong>). Neoclassical at the edges where the math works the same way: <strong>Ólafur Arnalds</strong>, <strong>Nils Frahm</strong>, <strong>Ryuichi Sakamoto</strong>. Scrobbles at <a href="https://www.last.fm/user/bdkl__">Last.fm</a>.</dd>

  <dt>Food</dt>
  <dd>Chefs I follow (and one place I sat down at): <strong>David Chang</strong>; <strong>David McMillan & Frédéric Morin</strong> at <strong>Joe Beef</strong> (ate there myself, a high point); <strong>Danny Bowien</strong> (Mission Chinese); <strong>Daniel Patterson</strong> (Coi).</dd>

  <dt>Tools</dt>
  <dd>Fedora 44 on a ThinkPad T14s. Ghostty + zsh + starship. Neovim and Doom Emacs. <code>eza</code>, <code>bat</code>, <code>zoxide</code>, <code>fzf</code>. IBM Plex Mono in the terminal; Source Serif 4 here.</dd>
</dl>

<p class="ornament ornament--fleuron">❦</p>

## IV. Writing
{: #writing}

A working notebook. Notes, post-mortems, and the occasional manifesto.

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <span class="post-date">{{ post.date | date: "%Y · %m · %d" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>

<p class="ornament ornament--fleuron">❦</p>

## V. Support
{: #support}

The projects live at [github.com/VirInvictus](https://github.com/VirInvictus). On Mastodon at [@Bdkl@mastodon.social](https://mastodon.social/@Bdkl). Professional profile at [linkedin.com/in/bdkl](https://www.linkedin.com/in/bdkl/).

If any of this is useful to you and you'd like to chip in:

```
bc1qkge6zr45tzqfwfmvma2ylumt6mg7wlwmhr05yv
```
