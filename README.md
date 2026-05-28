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

Thirteen projects. Native Linux desktop software at the centre, with game-design work and an Emacs theme at the edges. Local-first by default; the throughline is curation. Atrium is the largest piece and the one in motion; the rest sort by current state.

<div class="codex-entry">
  <span class="codex-num">No. 001</span>
  <div class="codex-body" markdown="1">
### Atrium
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.27.0</span></p>

The native GNOME task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface that never asks you to open Emacs. **Simple Mode** for *what am I doing right now* (six canonical lists, no defer dates, Things 3 calm); **Builder Mode** for the days the system has to do the work (Forecast, Agenda, Kanban, Calendar, Review, Perspectives, repeating and sequential projects, a live Inspector). Same data, two surfaces, no migration: flipping modes is a UI re-render over an OmniFocus-superset schema that was there on day one.

Local-first SQLite in WAL mode, single-writer worker, read-only connection pool. FTS5 search through a hand-written **Calibre-style expression grammar** (`tag:work AND is:overdue sort:-due`, `due:2026-05-01..2026-05-31`, `tag:?wrok` for fuzzy match). A six-crate workspace; the extracted `atrium-inline` engine (`#tag`, `@today`, `!priority` with tab-completion) and the `atrium-org` round-trip layer are both tested headlessly, away from the UI. 974 tests and 15 migrations, with a 1K-fixture smoke and cold-start check gating every push. Org is the two-way mirror, and importers bring the rest across: Todoist CSV, Taskwarrior `task export` JSON, todo.txt, and iCalendar VTODO (import and export). A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 002</span>
  <div class="codex-body" markdown="1">
### Viaduct
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v2.8.1</span></p>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary, making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** against ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio across three WAL databases (articles, feed settings, sync). OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire; NetNewsWire-faithful parsing of RSS 2.0, RDF, Atom, JSON Feed, and RSS-in-JSON. Local and Inoreader accounts, the latter a port of NetNewsWire's ReaderAPI sync engine. The article pane is exactly one neutered WebKit instance: JS, WebGL, WebRTC, DevTools, and LocalStorage off, strict CSP, every image routed through a custom `viaduct-img://` scheme so the WebView never reaches the open internet.

The v2.x line built an original surface on top of the port: **Custom Smart Feeds** (rule-driven saved searches), an Activity Log over a ring buffer, a Send-to menu, Reader View, OPML import/export, and adaptive `AdwBreakpoint` layout that collapses the three-pane split into mobile stacks. All eight NetNewsWire themes plus an Adwaita variant, with the theme accent propagating across the GTK chrome. A background-daemon mode runs Viaduct as an XDG autostart agent and re-summons the window over D-Bus. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 003</span>
  <div class="codex-body" markdown="1">
### Hermitage
<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Libadwaita <span class="stack-sep">·</span> <span class="status">active · v0.15.0</span></p>

A local-first, native gallery for Calibre libraries, for the single user who wants a modern desktop experience without Docker or a web auth layer. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: an edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive genre browser that unfolds dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Virtual Libraries and the full Calibre search-query language (`Ctrl+F`), with a 512-entry texture LRU and three-tier colour cache to keep scrolling smooth on integrated graphics. Ships `hermitage-verify`, a standalone CLI that audits integrity, cover presence, and format resolution. Zero telemetry, zero network calls, zero accounts. A GNOME 50 Flatpak ships alongside the native build: 8 MB, sandboxed, with arbitrary library paths reached through the file-chooser portal.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 004</span>
  <div class="codex-body" markdown="1">
### Lattice
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status">active · v4.6.0</span></p>

A toolkit for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre. Parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shelling out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking, an art-quality audit against a configurable resolution floor, and tag, bitrate, and duplicate audits. Smart `.m3u` generation from dynamic rules (`rating >= 4 and genre == 'Jazz'`), per-genre **wings** (one library file per genre, like Calibre virtual libraries for music), and a token-efficient `--ai-library` export sized to fit a 4,000-album collection inside an LLM context window. The directory layout is configurable, so the tools never fight you about your shelving. Bare `lattice` opens a full-screen curses TUI.

The package is read-only by design: it reads tags, decodes audio, writes reports. Two destructive companions live at the repo root, deliberately outside the package boundary so the read-only contract holds. `retag.py` is the universal genre rewriter, abstracting the ID3 / Vorbis / iTunes-atom multi-genre chaos for safe bulk retagging. `cleaner.py` consolidates fragmented album folders: it finds sibling directories whose names normalize to the same key (curly→straight quotes, dash variants→ASCII hyphen, NFKC, lowercase) and merges them via `shutil.move`, touching no audio bytes. Size-differing collisions keep both copies under a `.from-fragment` suffix; `--dry-run` previews every move and the operation is idempotent on re-run.

<p class="codex-link"><a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 005</span>
  <div class="codex-body" markdown="1">
### Framework
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status">active · v0.68.0</span></p>

A native GNOME document viewer for **PDF, DjVu, CBZ, CBR, XPS, EPUB, FB2, and MOBI**: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux. A three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction, parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline that builds the pixmap *around* the Cairo surface buffer.

A *velocity engine* throttles render dispatch by scroll speed so fast-scrolling never queues stale work, a thread-pool sort keeps the viewport ahead of the queue, and mid-render `fz_cookie` abort lets workers bail in milliseconds. Manga (RTL), Webtoon, and facing-pages comic layouts, all live-toggleable, with aspect-ratio and filename-based double-spread detection for scanlation rips. Async progressive search over cached structured text (332 ms cold → 48 ms warm on a 901-page textbook), reading-order-aware text selection, a magnifying loupe (F7), and `GFileMonitor` auto-reload that refreshes a recompiled LaTeX or Typst doc with scroll position preserved.

EPUB / MOBI / FB2 get a Foliate-style reflow architecture (a `GListModel` of structurally-typed blocks, OPF spine walker, MOBI / KF7 / KF8 / AZW3 parser with HuffDic decompression). A process-scoped Linux **Landlock LSM** sandbox drops filesystem `EXECUTE` and `MAKE_*` rights at startup, so a malicious document exploiting MuPDF / DjVuLibre / libarchive into RCE cannot escalate to a shell. Strictly a viewer: no annotations, no library, no conversion. Every borrowed pattern (SumatraPDF, zathura, Sioyek, YACReader, Foliate, MComix, Komikku, Plato) is attributed in the README with upstream `file:line`. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 006</span>
  <div class="codex-body" markdown="1">
### CalibreQuarry
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v3.0.0</span></p>

A CLI toolkit for power users of Calibre. Zero external dependencies: `sqlite3`, `argparse`, `curses`, and nothing else. Its hand-written recursive-descent parser hits **100% parity with Calibre's internal search-expression syntax**, validated by a test suite mapped against Calibre's own `SearchQueryParser`. The same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` mode (author / `vl:` / boolean / parens / `=`-prefix exact match).

Author-grouped catalogs, with `--all-wings` emitting one per virtual library. Library statistics across format, rating, tag taxonomy, and top authors / tags. **Audit** modes for untagged, unrated, coverless, series-gap, duplicate, and low-resolution covers (parsing on-disk JPEGs with no external libraries); **analytics** modes for per-author breakdowns, added-per-month pace, hierarchical tag trees, and wing overlap. JSON / CSV / AI exports, custom-column extraction, and an automatic DB snapshot when Calibre holds a write lock. Installs as `cquarry`. Complete software, tested on Fedora 43 against Calibre 9.7.

<p class="codex-link"><a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 007</span>
  <div class="codex-body" markdown="1">
### deadbeef-cui
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.2</span></p>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, an in-pane search bar (`Ctrl+Shift+F`), and a settings dialog with per-instance configuration so multiple Facet Browsers can coexist in one layout.

The standard DeaDBeeF track context menu is wired in (Play Next / Play Later / Properties / Convert / Reload metadata alongside the facet-specific items), tracks drag out of facet rows onto playlist tabs via the same `DDB_PLAYITEM_POINTERLIST` payload the GTKUI medialib widget uses, and "Send to new playlist `<row name>`" names the destination after the right-clicked tag. Everything targets a dedicated "Library Viewer" playlist so the plugin never touches curated playlists. Built natively against `DB_mediasource_t`. Complete; fixes only from here.

<p class="codex-link"><a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 008</span>
  <div class="codex-body" markdown="1">
### Belfry
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--design">design · v0.0.2</span></p>

A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can `ls`. Smart Speed and Voice Boost are ffmpeg filter chains (`silenceremove`, `acompressor`, `loudnorm`, `rubberband`) calibrated against Overcast; the Castro **Inbox → Queue → Played** flow is the daily metaphor. The library is filesystem-canonical, so a user with `find` and `mpv` can play their shows without Belfry running, and deleting the database triggers a rescan rather than data loss.

The same single-writer SQLite worker that Viaduct and Atrium use feeds four concurrent producers here. A four-crate workspace, with Calibre's library-as-database UX (filter grammar, sortable columns, bulk actions, saved Perspectives, Wings-style collections) layered over the triage states, and per-show overrides so a four-hour history episode and a twenty-five-minute tech show keep independent playback rules. GPL-3, forced by librubberband. Phase 1 landed the SQLite worker, read pool, and fixtures; no UI yet. Slated for absorption into Conservatory, whose podcast subsystem retires Belfry at parity.

<p class="codex-link"><a href="https://github.com/VirInvictus/Belfry">github.com/VirInvictus/Belfry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 009</span>
  <div class="codex-body" markdown="1">
### Conservatory
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libadwaita <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--design">design · v0.0.1</span></p>

A native GNOME library manager that *owns and organizes* your music and podcasts on disk, presented through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs both media types from one queue. Designed as **Calibre for audio**.

It absorbs the Belfry podcast client, converging that engine and triage model with a massive faceted music browser. The database is truth; the on-disk tree is a rendered template; moving an album re-renders the filesystem. A Calibre-shaped search expression language, multi-select bulk actions, and embedded-tag write-back so files stay portable. The skeleton is bootstrapped and Phase 1 is underway, building concurrently with Atrium under hard phasing; Belfry retires only at podcast parity (Phase 6).

<p class="codex-link"><a href="https://github.com/VirInvictus/Conservatory">github.com/VirInvictus/Conservatory →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 010</span>
  <div class="codex-body" markdown="1">
### project-void
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> Tiled <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

A design-stage CRPG and the data-driven engine that ships under it. The engineering commitment is the engine: rules expressed as universal TOML/Lua state machines, decoupled from the renderer, so the same binary could host *Cairn*, 5e, or any other system with a sheet and a turn order. The campaign is the demonstration. **The Reach** is a tight 15–20-hour run through a region of city-states, free companies, counting houses, an inquisition, and a ruined library-city.

Lethal *Cairn*-derived combat math: attacks hit automatically, HP is low, damage drains into real wounds via attribute damage. Combat as a positional puzzle, not a dice minigame.

<p class="codex-link"><a href="https://github.com/VirInvictus/project-void">github.com/VirInvictus/project-void →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 011</span>
  <div class="codex-body" markdown="1">
### project-yeschef
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> TOML <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

*YES CHEF* (working title): a single-player, character-driven grand-strategy restaurant simulation in the lineage of *Crusader Kings 3* and *Victoria 3*, pointed at the most volatile small business there is. You play the General Manager. You do not cook. You hire, fire, schedule, invest, negotiate, and hold the room together while the restaurant tries to kill itself around you. People are the system: every mechanic flows through characters with stats, traits, opinions, and agendas, and the food is what comes out of the humans who make it.

There is no win condition. The player declares an ambition (Michelin star, neighborhood institution, empire, or simply survival) and the simulation generates the matching challenge. Each new game procedurally generates a city with its own demographics, regulatory climate, and competitive landscape, where rival restaurants each run their own GM, poaching staff, collapsing, and retaliating. Data-driven on Godot 4 with Lua, Ink, and TOML, so event packs, trait packs, and city templates ship as drop-in content for modders. The former chef's project. Pre-development: skeleton and design docs, no engine code yet.

<p class="codex-link"><a href="https://github.com/VirInvictus/project-yeschef">github.com/VirInvictus/project-yeschef →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 012</span>
  <div class="codex-body" markdown="1">
### opends
<p class="codex-meta">Reverse engineering <span class="stack-sep">·</span> DOSBox <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

An open community toolkit and bugfix-patch project for SSI's *Dark Sun* CRPGs, *Shattered Lands* (1993) and *Wake of the Ravager* (1994). Tools first, patches second: a GFF reader/writer, a GPL bytecode disassembler, a dialog extractor, a save inspector, and a region viewer, each shipping independently with its own README, tagged release, and MIT license. The *darkfix* patches are zips you apply to a GOG install; the game still launches under DOSBox, but the bugs you used to hit, you do not.

The hard problem is the engine's embedded scripting language, a GPL bytecode VM with no public spec; two decades of full-reimplementation attempts have all stalled there. OpenDS goes at it sideways, shipping the artifacts built on the way to an engine (disassemblers, chunk editors, format docs, patches) as standalone tools, each useful on its own. It stands on the deepest prior reverse-engineering work (paulofthewest and the dsoageofheroes org for the GFF layout and the 129-entry GPL opcode catalogue) and keeps a per-feature manifest mapping each tool to the upstream file it came from. Phase 0: documentation and extraction.

<p class="codex-link"><a href="https://github.com/VirInvictus/opends">github.com/VirInvictus/opends →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 013</span>
  <div class="codex-body" markdown="1">
### kanagawa-dragon-nvim-emacs
<p class="codex-meta">Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.2</span></p>

A faithful Emacs port of the Dragon variant from [kanagawa.nvim](https://github.com/rebelot/kanagawa.nvim). Not a repackaging of the existing `kanagawa-themes` package; that one has the palette right but covers too few faces to hold up in practice. This one maps the full set: every Emacs 29+ tree-sitter `font-lock-*` face, all Doom-specific surfaces (`doom-modeline-*`, `solaire-mode`, `doom-dashboard-*`), org-mode faces, magit, company, corfu, and the rest of the usual zoo. Implemented as a vanilla `deftheme` with no `doom-themes` macro dependency, so it works in stock Emacs and in Doom alike.

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
  <dd>TTRPGs. The Calibre library runs deep here: OSR (Old School Essentials, Carcosa, Mothership), Forged in the Dark (Blades in the Dark and its extended family), World of Darkness, Shadowrun, the classic AD&D and Dark Sun lines. Drawn less to the play and more to the engineering: games that keep real ideas behind their front pages.</dd>

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

A working notebook. Notes, post-mortems, the occasional manifesto, and once in a while a *What I Use*.

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
