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

Where a rule can be a compile error instead of a convention, I make it one, and I would rather ship against a hard memory ceiling than an optional benchmark. I will port a battle-tested architecture with attribution before I invent a new one.

I came to the work late. Ten years in restaurants and mining camps before *The C Programming Language*. I read it at night, between shifts, because the cover looked serious and I wanted to know what serious looked like. I am a Computer Engineering Technician student now, with a CS bachelor's underway at Algoma, which is the paperwork catching up to about a decade of practice.

By temperament I am an archivist. I keep a private Calibre library that runs into the four figures, a music collection sorted by hand, an RSS spool I read every morning. Friends have called the practice *shadow librarianship*. The catalogue is my own, kept on my own disks, indexed by my own tools. Most of what I build is for the kind of person who treats their library as worth maintaining.

The site is named *Vir Invictus*, *the unconquered*. I picked it a long time ago and it stuck.

<p class="ornament ornament--fleuron">❦</p>

## II. The Collection
{: #the-collection}

Twenty-five projects. Native Linux desktop software at the centre, with game-design work, KOReader companions, a calibre-web theme, and an Emacs theme at the edges. Local-first by default; the throughline is curation. Atrium is the largest piece and the one in motion; the rest sort by current state.

<div class="codex-entry">
  <span class="codex-num">No. 001</span>
  <div class="codex-body" markdown="1">
### Atrium
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.65.1</span></p>

<div class="codex-plate codex-plate--pair">
  <img src="{{ '/assets/img/atrium-today-simple.webp' | relative_url }}" alt="Atrium's Today view in Simple Mode: a calm two-pane list with areas, tags, and two tasks due today" loading="lazy">
  <img src="{{ '/assets/img/atrium-today-builder.webp' | relative_url }}" alt="Atrium's Today view in Builder Mode: three panes with the live Inspector open on a task's schedule, project, tags, and notes" loading="lazy">
</div>

The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface that never asks you to open Emacs. **Simple Mode** for *what am I doing right now* (six canonical lists, no defer dates, Things 3 calm); **Builder Mode** for the days the system has to do the work (Forecast, Agenda, Kanban, Calendar, Review with per-area cadences that cascade to the projects filed under an area, Perspectives, repeating and sequential projects, blocked-by task dependencies, time-based system reminders, a live Inspector). Same data, two surfaces, no migration: flipping modes is a UI re-render over an OmniFocus-superset schema that was there on day one.

Local-first SQLite in WAL mode, single-writer worker, read-only connection pool. FTS5 search through a hand-written **Calibre-style expression grammar** (`tag:work AND is:overdue sort:-due`, `due:2026-05-01..2026-05-31`, `tag:?wrok` for fuzzy match). A seven-crate workspace; the extracted `atrium-inline` engine (`#tag`, `@today`, `!priority` with tab-completion) and the `atrium-org` round-trip layer are both tested headlessly, away from the UI. more than a thousand tests and 19 migrations, with a 1K-fixture smoke and cold-start check gating every push. Org is the two-way mirror, and importers bring the rest across: Todoist CSV, Taskwarrior `task export` JSON, todo.txt, and iCalendar VTODO (import and export). A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 002</span>
  <div class="codex-body" markdown="1">
### Viaduct
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v3.0.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/viaduct-main-adwaita.webp' | relative_url }}" alt="Viaduct's three-pane layout: feed sidebar with unread badges, timeline, and a rendered Daring Fireball article" loading="lazy">
</div>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary, making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** against ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio across three WAL databases (articles, feed settings, sync). OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire; NetNewsWire-faithful parsing of RSS 2.0, RDF, Atom, JSON Feed, and RSS-in-JSON. Local and Inoreader accounts, the latter a port of NetNewsWire's ReaderAPI sync engine. The article pane is exactly one neutered WebKit instance: JS, WebGL, WebRTC, DevTools, and LocalStorage off, strict CSP, every image routed through a custom `viaduct-img://` scheme so the WebView never reaches the open internet.

The v2.x line built an original surface on top of the port: **Custom Smart Feeds** (rule-driven saved searches), an Activity Log over a ring buffer, a Send-to menu, Reader View, OPML import/export, and a width-driven adaptive layout. A background-daemon mode runs Viaduct as an XDG autostart agent and re-summons the window over D-Bus. A Flatpak manifest ships alongside the native build. **v3.0.0 dropped libadwaita entirely** for a viaduct-owned design layer, a flat Kanagawa palette on plain GTK4, so it belongs equally on GNOME, Hyprland, or any Wayland desktop rather than reading as a GNOME app; the eight NetNewsWire reading-pane themes are unchanged. Removing a whole shared library also lowered memory, a full refresh now peaks around 300 MB.

<p class="codex-link"><a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 003</span>
  <div class="codex-body" markdown="1">
### Hermitage
<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">active · v0.18.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/hermitage-gallery.webp' | relative_url }}" alt="Hermitage's cover-art grid filtered to a virtual library, with the Wing sidebar open and the search bar showing the active expression" loading="lazy">
</div>

Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: an edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive genre browser that unfolds dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Virtual Libraries and the full Calibre search-query language (`Ctrl+F`), with a 512-entry texture LRU and three-tier colour cache to keep scrolling smooth on integrated graphics. Ships `hermitage-verify`, a standalone CLI that audits integrity, cover presence, and format resolution; the v0.16.0 audit sweep added the project's first in-tree test suite and lint hygiene behind it. The v0.17.0 pass took it tiling-first: libadwaita is gone in favour of plain GTK4 under an owned Kanagawa Dragon stylesheet that follows the system dark/light preference through the desktop portal, with floating overlay sidebars, grid type-ahead, and per-scale HiDPI thumbnails. Zero telemetry, zero network calls, zero accounts. A Flatpak ships alongside the native build: 8 MB, sandboxed, with arbitrary library paths reached through the file-chooser portal.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 004</span>
  <div class="codex-body" markdown="1">
### Lattice
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status status--complete">complete · v4.10.1</span></p>

Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre. Parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shelling out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking, an art-quality audit against a configurable resolution floor, and tag, bitrate, and duplicate audits. Smart `.m3u` generation from dynamic rules (`rating >= 4 and genre == 'Jazz'`), per-genre **wings** (one library file per genre, like Calibre virtual libraries for music), and a token-efficient `--ai-library` export sized to fit a 4,000-album collection inside an LLM context window. The directory layout is configurable, so the tools never fight you about your shelving. Bare `lattice` opens a full-screen curses TUI.

The package is read-only by design: it reads tags, decodes audio, writes reports. Seven destructive companions live in `scripts/`, deliberately outside the package boundary so the read-only contract holds: `genre_tidy.py` applies a genre policy map library-wide, `rerate.py` reconciles MP3 POPM rating bytes with DeaDBeeF and foobar, `genre_foldermap.py` restructures the tree into Genre / Artist / Album, `replaygain.py` writes ReplayGain 2.0 tags through `rsgain`, and `apestrip.py` removes stray APEv2 tags. Two are worth spelling out. `retag.py` is the universal genre rewriter, abstracting the ID3 / Vorbis / iTunes-atom multi-genre chaos for safe bulk retagging. `cleaner.py` consolidates fragmented album folders: it finds sibling directories whose names normalize to the same key (curly→straight quotes, dash variants→ASCII hyphen, NFKC, lowercase) and merges them via `shutil.move`, touching no audio bytes. Size-differing collisions keep both copies under a `.from-fragment` suffix; `--dry-run` previews every move and the operation is idempotent on re-run.

<p class="codex-link"><a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 005</span>
  <div class="codex-body" markdown="1">
### Framework
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.82.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/framework-viewer.webp' | relative_url }}" alt="Framework rendering a 168-page PDF with the table-of-contents sidebar open and two pages visible in the scroll" loading="lazy">
</div>

A native Linux document viewer for **PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, and Markdown**: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux. A three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction, parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline that builds the pixmap *around* the Cairo surface buffer.

A *velocity engine* throttles render dispatch by scroll speed so fast-scrolling never queues stale work, a thread-pool sort keeps the viewport ahead of the queue, and mid-render `fz_cookie` abort lets workers bail in milliseconds. Manga (RTL), Webtoon, and facing-pages comic layouts, all live-toggleable, with aspect-ratio and filename-based double-spread detection for scanlation rips. Async progressive search over cached structured text (332 ms cold → 48 ms warm on a 901-page textbook), reading-order-aware text selection, a magnifying loupe (F7), and `GFileMonitor` auto-reload that refreshes a recompiled LaTeX or Typst doc with scroll position preserved.

The ebook formats reflow natively through an embedded WebKitGTK view: each backend parses its format (an OPF spine walker for EPUB, a MOBI / KF7 / KF8 / AZW3 parser with HuffDic decompression ported from foliate-js, vendored md4c for Markdown) and emits one stitched HTML document, with images served over an internal `framework-img://` scheme and typography and reading themes pushed in live as CSS custom properties. EPUBs and AZW3 keep their publisher stylesheets and embedded fonts (KF8's CSS flows served through the same `framework-img://` scheme), a dark reading theme transforms those publisher colours in HSL so a book's own light callout never glares, internal links and TOC navigation work across all the reflow formats, and the HTML is scrubbed of scripts and active content before it ever reaches the view, which itself cannot touch the network. A process-scoped Linux **Landlock LSM** sandbox drops filesystem `EXECUTE` and `MAKE_*` rights at startup, so a malicious document exploiting MuPDF / DjVuLibre / libarchive into RCE cannot escalate to a shell. The v0.80.0 pass took it tiling-first: libadwaita is gone in favour of plain GTK4 under an owned Kanagawa Dragon stylesheet that follows the system dark/light preference through the desktop portal, with a floating table-of-contents overlay and hidden window chrome. Strictly a viewer: no annotations, no library, no conversion. Every borrowed pattern (SumatraPDF, zathura, Sioyek, YACReader, Foliate, MComix, Komikku, Plato) is attributed in the README with upstream `file:line`. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 006</span>
  <div class="codex-body" markdown="1">
### CalibreQuarry
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v3.6.0</span></p>

Calibre power-user tooling with zero external dependencies: `sqlite3`, `argparse`, `curses`, and nothing else. Its hand-written recursive-descent parser hits **100% parity with Calibre's internal search-expression syntax**, validated by a test suite mapped against Calibre's own `SearchQueryParser`. The same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` mode (author / `vl:` / boolean / parens / `=`-prefix exact match).

Author-grouped catalogs, with `--all-wings` emitting one per virtual library. Library statistics across format, rating, tag taxonomy, and top authors / tags. **Audit** modes for untagged, unrated, coverless, series-gap, duplicate, and low-resolution covers (parsing on-disk JPEGs with no external libraries); **analytics** modes for per-author breakdowns, added-per-month pace, hierarchical tag trees, and wing overlap. JSON / CSV / AI exports, custom-column extraction, and an automatic DB snapshot when Calibre holds a write lock. Installs as `cquarry`. Complete software, tested on Fedora 44 against Calibre 9.7.

Alongside the stdlib package sits a `scripts/` shelf of write-capable companions, deliberately outside the read-only contract: `audit_epub.py` reads the actual prose of every book to catch wrong-language editions and OCR damage that structural validators miss, `audit_drm.py` scans every format for encryption a metadata sweep would wave through, `reconcile_file_metadata.py` compares curated database values against the metadata embedded in each file (and can push the database back into the files), `validate_metadata.py` lints the `metadata.db` itself, `spot_check.py` samples random books for the corruption pattern sweeps miss, and `compress_pdf.py` shrinks the occasional 1 GB sourcebook through ghostscript.

<p class="codex-link"><a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 007</span>
  <div class="codex-body" markdown="1">
### deadbeef-cui
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.3</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/deadbeef-cui-facets.webp' | relative_url }}" alt="deadbeef-cui's three facet columns narrowing genre, album artist, and album above the playlist, with cover art and a waveform seekbar" loading="lazy">
</div>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, an in-pane search bar (`Ctrl+Shift+F`), and a settings dialog with per-instance configuration so multiple Facet Browsers can coexist in one layout.

The standard DeaDBeeF track context menu is wired in (Play Next / Play Later / Properties / Convert / Reload metadata alongside the facet-specific items), tracks drag out of facet rows onto playlist tabs via the same `DDB_PLAYITEM_POINTERLIST` payload the GTKUI medialib widget uses, and "Send to new playlist `<row name>`" names the destination after the right-clicked tag. Everything targets a dedicated "Library Viewer" playlist so the plugin never touches curated playlists. Built natively against `DB_mediasource_t`, with an in-tree GTest suite driving the real engine against a mocked DeaDBeeF API, clean under ASan/UBSan. Complete; fixes only from here.

<p class="codex-link"><a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 008</span>
  <div class="codex-body" markdown="1">
### Belfry
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--retired">retired → Conservatory</span></p>

A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can `ls`. Smart Speed and Voice Boost are ffmpeg filter chains (`silenceremove`, `acompressor`, `loudnorm`, `rubberband`) calibrated against Overcast; the Castro **Inbox → Queue → Played** flow was the daily metaphor. The same single-writer SQLite worker that Viaduct and Atrium use fed four concurrent producers here, with Calibre's library-as-database UX (filter grammar, sortable columns, bulk actions, saved Perspectives) layered over the triage states.

Retired June 2026 and absorbed into Conservatory (No. 009). The podcast fetch/parse/triage subsystem, the libmpv Smart Speed / Voice Boost engine, and the sleep timer all moved across whole, joining a music and audiobook library on one unified queue; the one design change is that Conservatory owns and moves the files (database-canonical) rather than reading a filesystem-canonical tree. The repo is frozen and archived at the parity release, kept public as reference. Belfry got as far as the SQLite worker, read pool, and fixtures before the merge.

<p class="codex-link"><a href="https://github.com/VirInvictus/Belfry">github.com/VirInvictus/Belfry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 009</span>
  <div class="codex-body" markdown="1">
### Conservatory
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status">active · v0.3.9</span></p>

Conservatory *owns and organizes* your music, podcasts, and audiobooks on disk, presenting them through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs all three media types from one queue. Designed as **Calibre for audio**.

It absorbed the Belfry podcast client (No. 008), converging that engine and triage model with a massive faceted music browser. The database is truth; the on-disk tree is a rendered template; moving an album re-renders the filesystem. A Calibre-shaped search expression language, multi-select bulk actions, and embedded-tag write-back so files stay portable. The headless manager imports, resolves, and crash-safely moves files with a full undo journal and roll-forward recovery; the GTK app stands up the deadbeef Columns UI faceted browse (configurable columns and facet panes), a sortable track list, saved Perspectives, the unified play queue with drag-reorder, shuffle and repeat, and a libmpv player carrying ReplayGain, a 10-band graphic EQ, a DSP rack (compressor, limiter, leveler), a real-time spectrum visualizer, a Now-bar transport, and a Preferences window over a real config file. All three media types are in: music, podcasts, and audiobooks browse and play from the one queue, and it holds up as a daily driver, down to gapless album transitions (the next track is prefetched across mpv's decoder boundary so the seam never reaches the speakers). A CLI health suite audits integrity, duplicates, tags, and cover art, strips stray APE tags, and imports and exports `.m3u`. Built concurrently with Atrium under hard phasing; Belfry was retired at podcast parity (v0.0.52) and its subsystem now lives here whole. The v0.3.x line took the app tiling-first (libadwaita is gone; the same feature set runs on plain GTK4 under an owned, flat Kanagawa Dragon stylesheet), turned the seek slider into the track's real loudness-envelope waveform, and grew a full scrobbler: Last.fm and ListenBrainz, now-playing included, through an offline-safe outbox, off by default.

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

<p class="codex-link">private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 011</span>
  <div class="codex-body" markdown="1">
### project-yeschef
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> TOML <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

*YES CHEF* (working title): a single-player, character-driven grand-strategy restaurant simulation in the lineage of *Crusader Kings 3* and *Victoria 3*, pointed at the most volatile small business there is. You play the General Manager. You do not cook. You hire, fire, schedule, invest, negotiate, and hold the room together while the restaurant tries to kill itself around you. People are the system: every mechanic flows through characters with stats, traits, opinions, and agendas, and the food is what comes out of the humans who make it.

There is no win condition. The player declares an ambition (Michelin star, neighborhood institution, empire, or simply survival) and the simulation generates the matching challenge. Each new game procedurally generates a city with its own demographics, regulatory climate, and competitive landscape, where rival restaurants each run their own GM, poaching staff, collapsing, and retaliating. Data-driven on Godot 4 with Lua, Ink, and TOML, so event packs, trait packs, and city templates ship as drop-in content for modders. The former chef's project. Pre-development: skeleton and design docs, no engine code yet.

<p class="codex-link">private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 012</span>
  <div class="codex-body" markdown="1">
### opends
<p class="codex-meta">Rust <span class="stack-sep">·</span> Python <span class="stack-sep">·</span> Reverse engineering <span class="stack-sep">·</span> DOSBox <span class="stack-sep">·</span> <span class="status">active</span></p>

An open community toolkit and bugfix-patch project for SSI's *Dark Sun* CRPGs, *Shattered Lands* (1993) and *Wake of the Ravager* (1994). Tools first, patches second: a GFF container reader/writer, a GPL bytecode disassembler and byte-exact reassembler, a dialog extractor, a save inspector, and a region renderer, each a standalone MIT-licensed tool with its own README and version. Twelve ship today, working and tested (142 passing tests across a six-crate Rust workspace, with stdlib-Python companions). Nothing here redistributes a byte of the game: you bring your own GOG copy, and the toolkit reads and patches it through an overlay mount that never touches the original install. The *darkfix* patches the tools exist to produce are the next milestone, not yet shipped.

The hard problem is the engine's embedded scripting language, a GPL bytecode VM with no public spec; two decades of full-reimplementation attempts have all stalled there. OpenDS goes at it sideways, shipping the artifacts built on the way to an engine (disassemblers, chunk editors, format docs) as standalone tools, each useful on its own. The disassembler carries the full 129-entry opcode catalogue, and the reassembler round-trips the games' bytecode chunks byte-for-byte. It stands on the deepest prior reverse-engineering work (paulofthewest and the dsoageofheroes org for the GFF layout and that opcode catalogue) and keeps a per-feature manifest mapping each tool to the upstream file it came from.

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

<p class="codex-link">not yet public</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 014</span>
  <div class="codex-body" markdown="1">
### Bindery
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.9.0</span></p>

A command-line surgeon for malformed EPUBs. The fixes are deliberately boring: self-close the void elements, convert named entities to numeric, sync the NCX `uid` with the OPF, put the `mimetype` entry first in the zip. Each one is deterministic, and each one lands only if [epubcheck](https://github.com/w3c/epubcheck) confirms the patient actually improved. epubcheck stays an external oracle, never a Python dependency; the package itself is stdlib only. Dry-run is the default mode, and `--apply` backs up before it touches anything.

Built to operate inside a Calibre library without breaking it: a repair atomically replaces only the `.epub`, leaving `metadata.opf`, `cover.jpg`, and the database for Calibre's own Quality Check to re-sync. An opt-in lossy mode (`--strip-pagination`) goes further, removing the baked-in page-number furniture that PDF and OCR conversions leave behind, behind its own safety guards. Sibling to oceanstrip; the two share the epubcheck no-regression gate.

<p class="codex-link"><a href="https://github.com/VirInvictus/Bindery">github.com/VirInvictus/Bindery →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 015</span>
  <div class="codex-body" markdown="1">
### oceanstrip
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

Strips producer and redistributor watermarks out of EPUBs. What began as an OceanofPDF.com-only tool is now a small signature registry: OceanofPDF's injected link (and its stray marker file), and the ABC Amber LIT Converter stamp that old `.lit` conversions leave on nearly every page, each caught in both an anchored form (the stamp is a link) and an anchorless form (plain text, with no `<a>` to catch). Adding another producer is one table entry. The removal is balanced-element surgery rather than regex slicing: find the stamp, walk up to the outermost wrapper whose entire visible text is the watermark, and delete that whole well-formed element, so real prose that merely mentions the URL is never touched and a well-formed file stays well-formed. Works on a single file or sweeps an entire library, always writing new copies (originals are never modified), and every output is epubcheck-clean. Stdlib only, like its sibling Bindery.

<p class="codex-link"><a href="https://github.com/VirInvictus/Oceanstrip">github.com/VirInvictus/Oceanstrip →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 016</span>
  <div class="codex-body" markdown="1">
### AudiobookTools
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> <span class="status">active · v0.2.0</span></p>

One catalogue file is the source of truth for an entire audiobook shelf: `retag` writes the embedded metadata from it, `reorg` renders the on-disk folder tree from it, and the files and the shelf cannot drift apart because both are projections of the same data. The engine is generic and the catalogue is data; the two never mix.

The operational contract does the heavy lifting. Dry-run is the default for everything; every `--apply` writes a manifest that fully reverses it; a second dry-run after an apply must report zero changes. The tests enforce all three properties, which is what lets a bulk retag of irreplaceable audio feel routine instead of reckless.

<p class="codex-link"><a href="https://github.com/VirInvictus/AudiobookTools">github.com/VirInvictus/AudiobookTools →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 017</span>
  <div class="codex-body" markdown="1">
### Hearth
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v0.12.1</span></p>

A native, two-player, local-network, fully offline digital build of a worker-placement and polyomino-economy Eurogame, riding on a content-agnostic engine built to outlive any one theme. The board, the goods, and the cards are data; the engine keeps a pure `State` / `Rules` / `Scoring` / `Loader` split so the same binary could host a different game with a sheet and a turn order. The distinctive subsystems are the home-board polyomino puzzle and a pure effect vocabulary the cards reuse: every action is a non-mutating transform over game state, which keeps the rules testable away from the renderer.

Hot-seat is the development default; the authoritative-host LAN layer lands late, once the economy and the full score are settled. The faithful ruleset is transcribed from the physical book, git-ignored, and never committed; the asset meant to ship is the engine plus an original-theme dataset, a deliberate post-1.0 extraction. Sibling in shape to Haveli.

<p class="codex-link">private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 018</span>
  <div class="codex-body" markdown="1">
### Haveli
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v0.11.2</span></p>

Two players, one LAN, no internet at any point: a digital build of a fast set-collection card game on a content-agnostic, deterministic engine. Sibling in shape to Hearth, but where Hearth's puzzle is the board, Haveli's is hidden information and reproducible randomness. It is a shuffled-deck game, so determinism is foundational: an `rng_seed` plus a draw cursor make every shuffle and every market refill replayable from the state alone, which is what lets the network layer stay honest.

Hidden hands force a host-authoritative, per-seat-**redacted** model: the host owns the truth, validates every move, and pushes each peer only the view its seat is allowed to see. There is no move relay, because relaying moves would leak the deck order. The engine keeps the same `State` / `Rules` / `Scoring` / `Loader` split, with moves as serializable dictionaries; the ENet transport is in and verified live across two machines, disconnect and reconnect included. The faithful dataset is git-ignored and never committed; the engine is the asset that ships.

<p class="codex-link">private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 019</span>
  <div class="codex-body" markdown="1">
### Colophon
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Cairo <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v2.1.0</span></p>

A native Linux statistics viewer for [KOReader](https://koreader.rocks/). KOReader tracks a surprising amount about how you read (per-page timing, session history, running totals), and every existing way to look at that data is a web dashboard or a self-hosted Docker service. Colophon is neither: a local desktop app that imports a *copy* of `statistics.sqlite3` (staged, validated, never opened in place) and turns it into the analytics nobody else ships. A reading-speed trend across the library with a per-book overlay; a weekday-by-hour *when do I read* heatmap; session-length histograms and starts-by-hour patterns; a per-page activity strip that answers *did it drag in the middle*; inferred read-through detection with per-completion cards; a reading-personality card that reads traits (chronotype, session style, weekly rhythm) off your own behaviour; and the expected furniture (year heatmap, streaks, device-parity stat cards) done carefully. Per-book `.sdr` sidecars are strictly opt-in and user-provided: hand it one and the device's own finished verdict becomes authoritative over the position-based guess and your highlights land at their true place on the activity strip, but nothing on the device is ever scanned.

The spec pins a normative definition for every derived metric (what counts as a session, a streak, a page read) so the numbers reconcile with the device and with each other; progress is an interval union on the page axis, immune to re-reads and to pagination drift when font sizes change. A two-crate workspace splits the headless ingestion-and-metrics core from the GTK shell, the charts are hand-drawn cairo on `GtkDrawingArea` across eight switchable themes (Kanagawa Dragon/Wave/Lotus, Gruvbox, Nord, Rosé Pine, Solarized) that drive both the window chrome and the graphs (no charting crate, zero new dependencies), and the tests include a reconciliation run against the real device sample. It reached 1.0 on 2026-07-05, feature-complete against the spec with Meson and Flatpak packaging shipped; the 2.0 line then dropped libadwaita for a flat, hard-edged look of Colophon's own, generated from the same `Theme` that colours the charts, tiling-first and portal-aware. A colophon is the note printers placed at the end of a book, the book's own record of its production; this is that idea turned toward the reading.

<p class="codex-link"><a href="https://github.com/VirInvictus/Colophon">github.com/VirInvictus/Colophon →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 020</span>
  <div class="codex-body" markdown="1">
### Dead Reckoning
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

The smallest thing in the collection: a preset for the [Bookends](https://github.com/AndyHazz/bookends.koplugin) KOReader plugin, styled as a navigation cockpit for the book in progress. Session pace in pages per hour, a chapter ETA, a projected finish date reckoned from the current pace, and a tick on the progress bar at every chapter waypoint. The telemetry renders in a soft low-contrast grey so the instruments never compete with the page. One Lua file; drop it in the presets folder.

<p class="codex-link"><a href="https://github.com/VirInvictus/dead-reckoning-bookend-preset">github.com/VirInvictus/dead-reckoning-bookend-preset →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 021</span>
  <div class="codex-body" markdown="1">
### Kobo-style Sleepscreen Banner
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

A KOReader user patch that redraws the stock sleep screen as a Kobo-lockscreen-style floating card over your book cover: a serif title, a stats line, and a random highlight pulled from the last book you were reading, set as an italic pull-quote with an accent rule and a "saved on..." footer. The card carries a real visual identity, rounded corners over a hard offset drop shadow so it reads as a tag sitting above the cover, with per-element font control wired for the [ebook-fonts](https://github.com/nicoverbruggen/ebook-fonts) collection out of the box. It draws once on suspend, so there is no E Ink refresh cost while you read. Honest about its lineage: a prettified fork of zenixlabs' community patch (which designed the Kobo banner and the random-highlight feature), credited in the source header and README; this fork contributes the floating-card design and the font wiring. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `2-` prefix so it loads after KOReader's widget system. The third of the KOReader companions, alongside Colophon and Dead Reckoning.

<p class="codex-link"><a href="https://github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified">github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 022</span>
  <div class="codex-body" markdown="1">
### 1-timezone
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

The tiniest fix in the collection, born from a real annoyance: on a jailbroken Kindle that boots straight into KOReader, no framework hands the process a timezone, so the base system falls back to a bogus Local Mean Time offset and every clock in the app is wrong by an odd fraction of an hour. "Synchronize time" never helps, because it corrects the instant, not the offset. This patch sets a real POSIX `TZ` inside the process and calls `tzset()` early, before the first clock read, so the footer clock, time sync, and AutoWarmth all agree again, with daylight saving flipping on its own. It ships defaulting to Eastern Time; one labelled line retargets it to any zone. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `1-` prefix so it runs first. The fourth of the KOReader companions, alongside Colophon, Dead Reckoning, and the Sleepscreen Banner.

<p class="codex-link"><a href="https://github.com/VirInvictus/1-timezone">github.com/VirInvictus/1-timezone →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 023</span>
  <div class="codex-body" markdown="1">
### Carrel
<p class="codex-meta">Python <span class="stack-sep">·</span> Flask <span class="stack-sep">·</span> CSS <span class="stack-sep">·</span> <span class="status">active · v0.9.0</span></p>

A carrel is a private desk in a library, and that is the whole design brief: no accounts, no sharing, no dashboard. One reader, seven thousand books, and an interface that gets out of the way. Built on [calibre-web](https://github.com/janeczku/calibre-web), it has since become a different program.

**There is no login.** Rather than strip out authentication and fight every future rebase, a thirty-line shim authenticates the owner on each request, so upstream's 154 `@login_required` decorators pass untouched and the credential routes simply answer 404. `metadata.db` is attached read-only at the connection level, so the web layer cannot write to the library even by accident.

**The search bar speaks Calibre.** Upstream has no expression grammar at all: it lowercases the term and hands it to FTS5 as a phrase, so `author:"King"` searched for that literal string and returned nothing. Carrel evaluates through CalibreQuarry's stdlib port of Calibre's parser (No. 006), and the numbers invert: 0 to 55 for that query, 0 to 1368 for `tags:Fic.Fantasy`, 0 to 244 for a custom column. Field prefixes, boolean logic, hierarchical tags and virtual-library references all behave as they do in Calibre.

**Wings** surface Calibre's virtual libraries as browse sections through that same engine, so the sidebar and a `vl:` search can never disagree. A **category browser** walks the library's dot taxonomy, synthesising the intermediate nodes because only leaves are assigned, and **Ctrl-K** fuzzy-jumps to any of 6,975 destinations, falling through to a search when what you typed is not one.

The theme stopped being a theme. caliBlur is gone and the stylesheet is owned outright: ledger hairlines instead of cards, serif for prose and mono for every label and count. One measurement shaped the statistics surfaces more than any taste decision. Kanagawa fails as a categorical chart palette, measurably: the worst adjacent accent pair sits at ΔE 6.7 for normal vision, before colour blindness is considered. So magnitude rides a single sequential ramp and identity is carried by position and a label. The constraint pushed the design further toward the ledger idiom.

<p class="codex-link"><a href="https://github.com/VirInvictus/Carrel">github.com/VirInvictus/Carrel →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 024</span>
  <div class="codex-body" markdown="1">
### Coffer
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> hledger <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

Envelope budgeting over a plain-text [hledger](https://hledger.org/) journal: Actual Budget's experience, hledger's data discipline, two-way. Atrium's sibling, but for money, and with the polarity inverted: the journal *is* the database, any SQLite is a disposable read cache, and the app shells out to the `hledger` binary for its reports rather than reimplementing the ledger. The hard problem, and the reason the research phase is real, is a safe append-and-edit write-back path onto a file the user also edits by hand.

A coffer is both a strongbox for valuables and the recessed panel in a coffered ceiling; finance and architecture in one word, the same dual reading as Atrium. Phase 0: the design dossier is committed, the spec is not yet locked, no code exists.

<p class="codex-link"><a href="https://github.com/VirInvictus/Coffer">github.com/VirInvictus/Coffer →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 025</span>
  <div class="codex-body" markdown="1">
### rd-cli
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.3.0</span></p>

Talks to the [Raindrop.io](https://raindrop.io/) bookmarking service with nothing from PyPI, built the way the other stdlib tools here are: `urllib`, `json`, `argparse`, `tomllib`. It covers the REST API a single user actually touches: raindrops, collections, tags, and highlights, plus the account endpoints (user, stats, filters, import-dedup, export, backups). Every command speaks two languages, designed ANSI for a human at a terminal and `--json` for scripts and agents, so the one binary is both a daily driver and an automation surface.

The whole client funnels through a single `_request` method: it attaches auth, applies a timeout, lowercases the boolean query params the API rejects otherwise, retries `429` and `5xx` with bounded backoff (honoring `Retry-After`), and maps every failure to a typed exception carrying the API's own message. The bulk verbs are grounded in an empirically verified quirk of Raindrop's batch endpoints, that they only touch raindrops actually in the path collection, so a naive id-based batch move silently no-ops; rd-cli loops the single-item endpoints for explicit id-lists and reserves the batch calls for `--from` collection scope, and a global `--dry-run` logs the method and payload of every write without making the call. A pytest suite drives the client against a fake `urllib` transport, so the tests need no network.

Since v0.2.0 it speaks a second service too: a `PinboardClient` sibling and an `rd pinboard` command group, honest to [Pinboard](https://pinboard.in)'s flat model (bookmarks keyed by URL, no collections, `toread`/`shared` flags, notes) with a paced client for Pinboard's strict rate limit. v0.3.0 adds `rd sync`, a two-way additive Raindrop and Pinboard sync that matches on a normalized URL (its dedup key), never deletes, and bridges the model gap reversibly in tags, with direction and collection/tag scoping so it converges what you choose rather than unioning everything by force.

<p class="codex-link"><a href="https://github.com/VirInvictus/rd-cli">github.com/VirInvictus/rd-cli →</a></p>
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
  <dd>Fedora 44 on a ThinkPad T14s, running Hyprland with a bar I wrote. Ghostty + zsh + starship. Neovim, Doom Emacs, and Helix. <code>eza</code>, <code>bat</code>, <code>zoxide</code>, <code>fzf</code>. TX-02 everywhere it can be; Source Serif 4 here.</dd>
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
