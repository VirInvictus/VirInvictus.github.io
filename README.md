---
layout: default
title: A Second Cup
description: Brandon LaRocque — sous-chef turned programmer. Notes and projects on building native Linux desktop software.
---

Last login: {{ site.time | date: "%a %b %e %H:%M:%S %Y" }} on tty1

## whoami

**Brandon LaRocque** — sous-chef turned programmer after embracing a life-long obsession with the craft. Software should matter. Good software should be maintained and cared for. I'm a thirty-something Canadian who spent years working in restaurants and mining camps while reading Kernighan & Ritchie's *The C Programming Language* in my bedroom at night.

These days I write **native Linux desktop software** out of Fedora: Rust + GTK4, Python, and C built with Meson. I lean on the standard library before reaching for a framework, prefer compile-time boundaries over code-review rules, and would rather port a battle-tested architecture than invent a new one.

I obsess over curation and organization — books, music, feeds, documents — and most of what I build is for the kind of person who treats their library as worth maintaining. I also write Discord bots: quote archives, multi-server moderation, game-night helpers for friends and small communities.

## ls -l projects/

| Project | Stack | Status |
|---|---|---|
| [**viaduct**](https://github.com/VirInvictus/Viaduct) | Rust · GTK4 · tokio | active |
| [**hermitage**](https://github.com/VirInvictus/Hermitage) | Python 3.14 · GTK4 · Libadwaita | active |
| [**calibrequarry**](https://github.com/VirInvictus/CalibreQuarry) | Python (stdlib only) | complete |
| [**lattice**](https://github.com/VirInvictus/Lattice) | Python · mutagen · ffmpeg | active |
| [**framework**](https://github.com/VirInvictus/Framework) | C · Meson · GTK4 · MuPDF | wip |
| [**deadbeef-cui**](https://github.com/VirInvictus/deadbeef-cui) | C · GTK3 | complete |
| [**project-void**](https://github.com/VirInvictus/project-void) | Godot 4 · Lua · Ink · Tiled | design |

## cat projects/viaduct/README.md

### viaduct — *Rust · GTK4 · tokio*

A Linux port of [NetNewsWire](https://netnewswire.com/), Brent Simmons' macOS RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary — making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** versus ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio. Three databases, all WAL-mode. OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire. FTS5 full-text search. Exactly one neutered WebKit instance for the article pane — JS, WebGL, WebRTC, DevTools, and LocalStorage all off, strict CSP, every image routed through a custom `viaduct-img://` URI scheme so the WebView never reaches the public internet directly. Ships all eight NetNewsWire article themes plus an Adwaita variant for system-native feel. The accent color from the selected theme propagates across the GTK chrome — sidebar selection, focus rings, switches — beating GNOME's system-accent integration. NetNewsWire-faithful parser handles RSS 2.0, RDF, Atom, JSON Feed, and RSS-in-JSON.

→ [github.com/VirInvictus/Viaduct](https://github.com/VirInvictus/Viaduct)

## cat projects/hermitage/README.md

### hermitage — *Python 3.14 · GTK4 · Libadwaita*

A local-first, native gallery for Calibre libraries. Built for the single user who wants a modern desktop experience without Docker containers or a web auth layer. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: edge-to-edge cover grid with median-cut color quantization for per-book accent tinting, sliding hero-banner detail sidebar (the Codex), and a recursive tag-hierarchy genre browser that turns dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Calibre's Virtual Libraries, full Calibre search-query language in the search bar (`Ctrl+F`), and a 512-entry texture LRU plus three-tier color cache to keep scrolling smooth on integrated graphics. Ships with `hermitage-verify`, a standalone CLI that validates library integrity, cover presence, and format resolution. Zero telemetry, zero network calls, zero accounts.

→ [github.com/VirInvictus/Hermitage](https://github.com/VirInvictus/Hermitage)

## cat projects/calibrequarry/README.md

### calibrequarry — *Python (stdlib only)*

A CLI toolkit for power users of Calibre. Zero external dependencies — `sqlite3`, `argparse`, `curses`, and nothing else. Ships a hand-written recursive-descent parser at **100% parity with Calibre's internal search-expression syntax** (validated by an automated test suite); the same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` CLI mode.

Catalog generation grouped by author, library statistics, audit reports (untagged, unrated, coverless, series gaps), `--all-wings` to emit a separate catalog for every virtual library, JSON / CSV export. Auto-snapshots the database when Calibre holds a write lock. Installs as `cquarry`; running with no arguments launches a curses TUI with arrow-key navigation that remembers the database path between sessions. Considered complete software — fully tested on Fedora 43 against Calibre 9.7.

→ [github.com/VirInvictus/CalibreQuarry](https://github.com/VirInvictus/CalibreQuarry)

## cat projects/lattice/README.md

### lattice — *Python · mutagen · ffmpeg*

A toolkit for music collectors who keep the filesystem as the source of truth. Library tree visualization with artist / album / track / rating / genre, parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shells out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking (FLAC → Opus → M4A → MP3), tag and bitrate audits, duplicate detection across formats and directories, smart `.m3u` playlist generation from dynamic rules (e.g. `rating >= 4`), and a token-efficient `--ai-library` export designed to fit a 4,000-album collection inside an LLM context window.

Ships with `retag.py`, a companion that abstracts away the ID3 / Vorbis / iTunes-atom multi-genre chaos for safe directory-wide retagging. Bare `lattice` launches a full-screen curses TUI with color-coded section groups (Library, Integrity, Artwork, Metadata).

→ [github.com/VirInvictus/Lattice](https://github.com/VirInvictus/Lattice)

## cat projects/framework/README.md

### framework — *C · Meson · GTK4 · MuPDF*

A native GNOME document viewer for **PDF, DjVu, CBZ, CBR, XPS, EPUB, FB2, and MOBI**. Designed to fill the gap between feature-heavy clients (Okular) and bare MuPDF wrappers — a SumatraPDF-shaped experience for Linux. Three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction (default 512 MB cap), parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→cairo pipeline.

A *velocity engine* throttles render-job dispatch by scroll speed so fast-scrolling never queues stale work, and a `g_thread_pool` sort function reorders the queue by `last_view_time` so the viewport always wins; mid-render `fz_cookie` abort lets workers bail in milliseconds. Manga (RTL), Webtoon (zero-gap continuous strip), and facing-pages comic layouts, all live-toggleable. Async search with cached structured text. `GFileMonitor` auto-reload — recompile a LaTeX or Typst doc and the viewer refreshes with scroll position preserved. HiDPI-aware on Wayland fractional scaling. A deliberate synthesis of patterns from SumatraPDF, zathura, YACReader, and Fractal — every borrow attributed in the README. Strictly a viewer: no annotations, no library, no conversion.

→ [github.com/VirInvictus/Framework](https://github.com/VirInvictus/Framework)

## cat projects/deadbeef-cui/README.md

### deadbeef-cui — *C · GTK3*

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full DeaDBeeF title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, and an in-pane search bar (`Ctrl+Shift+F`). Targets a dedicated "Library Viewer" playlist so it never touches the user's curated playlists. Built natively against `DB_mediasource_t`. Effectively complete at v1.2.3 — fixes only.

→ [github.com/VirInvictus/deadbeef-cui](https://github.com/VirInvictus/deadbeef-cui)

## cat projects/project-void/README.md

### project-void — *Godot 4 · Lua · Ink · Tiled · TOML*

A design-stage CRPG in the lineage of *Dark Sun: Shattered Lands*, *Fallout 2*, *Arcanum*, and *Disco Elysium*. Lethal *Cairn* combat math: attacks hit automatically, HP is low, damage drains into real wounds via attribute damage — combat as a positional puzzle, not a dice minigame. Fallout-style character sheet. Low-fantasy world that owes more to Joe Abercrombie than Tolkien.

Ships as two products: **The Reach** — a tight 15–20 hour campaign through a patchwork region of city-states, free companies, counting houses, an inquisition, and a ruined library-city — and **The Engine**, a data-driven moddable platform. The ruleset is decoupled from the engine via universal TOML/Lua state machines, so the same engine could host *Cairn*, 5e, or anything else with a sheet and a turn order.

→ [github.com/VirInvictus/project-void](https://github.com/VirInvictus/project-void)

## cat ~/.interests

When I'm not writing code, I'm usually busy with other forms of world-building. Most of these projects exist because I'm trying to be a better steward of one collection or another — the overlap with off-screen taste is not coincidental.

- **Reading** — 10–20 books a year. Grimdark fantasy, cyberpunk, horror. Authors I return to: **Joe Abercrombie**, **Brandon Sanderson**, **Morgan Housel**, **Terry Pratchett**.
- **Collecting** — TTRPGs, mostly. Obsessing over their well-built systems, beautiful art, and the concepts kept behind their front pages.
- **Music** — Hip-hop, post-hardcore, mid-'00s-to-mid-'10s emo. On rotation: **Brand New**, **50 Cent**, **Ka**, **Ólafur Arnalds**, **Self Defense Family**.
- **Food** — Chefs I follow (and one place I sat down at): **David Chang**; **David McMillan & Frédéric Morin** at **Joe Beef** (ate there myself — a high point); **Danny Bowien** (Mission Chinese); **Daniel Patterson** (Coi).
- **Games that still own my soul** — Dark Souls 3, RimWorld, Hollow Knight, Dwarf Fortress.

## ls _posts/

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>
