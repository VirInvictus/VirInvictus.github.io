---
layout: default
title: Vir Invictus
description: Brandon LaRocque — sous-chef turned programmer. A working notebook on native Linux software, libraries, and the long obsession of building things by hand.
permalink: /
---

<header class="masthead">
  <h1 class="masthead__title">VIR <span class="dot">·</span> INVICTVS</h1>
  <p class="masthead__exlibris">Ex libris Brandon LaRocque</p>
</header>

<p class="sigils">
  <span class="sigils__ornament">❦</span>
  curator
  <span class="sigils__sep">·</span> shadow librarian
  <span class="sigils__sep">·</span> coder
  <span class="sigils__sep">·</span> gamer
  <span class="sigils__sep">·</span> father
  <span class="sigils__sep">·</span> former chef
  <span class="sigils__ornament">❦</span>
</p>

## I. On the Author
{: #on-the-author}

<div markdown="1" class="dropcap">
I am a thirty-eight-year-old Canadian, a father, and a Computer Engineering Technician student at Northern College — headed for a Computer Science bachelor's at Algoma. None of that is the most useful thing to know about me. The most useful thing to know is that I cook the same way I write code: by reading carefully, paying attention to the room, and refusing to rush a thing that wants to be done well.
</div>

I was a sous-chef for ten years. Restaurants and mining camps. I read Kernighan & Ritchie's *The C Programming Language* in my bedroom at night, between shifts, because the cover looked serious and I wanted to know what serious looked like. The throughline from then to now is the same — a craftsman's obsession with making something durable with my hands.

I am a shadow librarian. I curate a Calibre library that runs into the four-figure mark, sort the music collection by hand, and care about ID3 vs Vorbis vs iTunes-atom multi-genre conventions in a way that should probably embarrass me. Most of what I build comes from that — software for the kind of person who treats their library as worth maintaining.

These days I write **native Linux desktop software** out of a Fedora 44 ThinkPad in northern Ontario. Rust + GTK4. Python. C built with Meson. Local-first. No cloud accounts, no Docker, no telemetry. I lean on the standard library before reaching for a framework, prefer compile-time boundaries over code-review rules, and would rather port a battle-tested architecture than invent a new one.

The site is named *Vir Invictus* — the unconquered. The motto is mine before it is a brand: I came to this late, and I am not surrendering the work to age, doubt, or the easier path.

<p class="ornament ornament--fleuron">❦</p>

## II. The Collection
{: #the-collection}

A standing assembly of native Linux desktop software, built mostly out of curiosity, mostly for an audience of one. *Atrium* is the largest and most active piece; the rest are sorted by what they curate and what state they're in.

<div class="codex-entry">
  <span class="codex-num">No. 001</span>
  <div class="codex-body" markdown="1">
### Atrium
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.6.7</span></p>

The native GNOME task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise — UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data — but in a fast GTK4 surface that does not require Emacs to operate. **Simple Mode** for *what am I doing right now*: six canonical lists, no defer dates, Things 3 calm. **Builder Mode** for the days the system has to do the work: Forecast, Review, Perspectives, repeating tasks, sequential projects, an always-visible Inspector pane. Same data, two surfaces, no migration — flipping modes is a UI re-render; the schema is the OmniFocus superset on day one.

Local-first SQLite at `$XDG_DATA_HOME/atrium/atrium.db`. Single-writer worker thread, WAL mode, read-only connection pool. FTS5-backed search using a hand-written **Calibre-style expression grammar** — `tag:work AND is:overdue sort:-due`, `due:2026-05-01..2026-05-31`, `tag:?wrok` for fuzzy match. A four-crate Rust workspace — `atrium-core`, `atrium-search`, `atrium-cli`, and the `atrium` binary — so every non-GUI surface stays headless and testable. 375 tests, a regression gate that runs fmt + clippy + tests + a 1K-fixture smoke + a cold-start sanity check. **Phase 16 — the Things 3 importer — is what comes next.**

<p class="codex-link"><a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 002</span>
  <div class="codex-body" markdown="1">
### Viaduct
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> <span class="status">active</span></p>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary — making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** versus ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio. OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire. FTS5 full-text search. Exactly one neutered WebKit instance for the article pane — JS, WebGL, WebRTC, DevTools, and LocalStorage all off, strict CSP, every image routed through a custom `viaduct-img://` URI scheme so the WebView never reaches the public internet directly. Ships all eight NetNewsWire article themes plus an Adwaita variant; the accent color from the selected theme propagates across the GTK chrome.

<p class="codex-link"><a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 003</span>
  <div class="codex-body" markdown="1">
### Hermitage
<p class="codex-meta">Python 3.14 <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Libadwaita <span class="stack-sep">·</span> <span class="status">active</span></p>

A local-first, native gallery for Calibre libraries. Built for the single user who wants a modern desktop experience without Docker containers or a web auth layer. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive tag-hierarchy genre browser that turns dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Calibre's Virtual Libraries, the full Calibre search-query language in the search bar (`Ctrl+F`), and a 512-entry texture LRU plus three-tier colour cache to keep scrolling smooth on integrated graphics. Ships with `hermitage-verify`, a standalone CLI that audits library integrity, cover presence, and format resolution. Zero telemetry, zero network calls, zero accounts.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 004</span>
  <div class="codex-body" markdown="1">
### Lattice
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status">active</span></p>

A toolkit for music collectors who keep the filesystem as the source of truth. Library tree visualization with artist / album / track / rating / genre, parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shells out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking (FLAC → Opus → M4A → MP3), tag and bitrate audits, duplicate detection across formats and directories, smart `.m3u` playlist generation from dynamic rules (e.g. `rating >= 4`), and a token-efficient `--ai-library` export designed to fit a 4,000-album collection inside an LLM context window.

Ships with `retag.py`, a companion that abstracts away the ID3 / Vorbis / iTunes-atom multi-genre chaos for safe directory-wide retagging. Bare `lattice` launches a full-screen curses TUI with colour-coded section groups.

<p class="codex-link"><a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 005</span>
  <div class="codex-body" markdown="1">
### Framework
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> <span class="status status--wip">wip</span></p>

A native GNOME document viewer for **PDF, DjVu, CBZ, CBR, XPS, EPUB, FB2, and MOBI**. Designed to fill the gap between feature-heavy clients (Okular) and bare MuPDF wrappers — a SumatraPDF-shaped experience for Linux. Three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction, parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline.

A *velocity engine* throttles render-job dispatch by scroll speed so fast-scrolling never queues stale work, and a `g_thread_pool` sort function reorders the queue by `last_view_time` so the viewport always wins. Manga (RTL), Webtoon (zero-gap continuous strip), and facing-pages comic layouts, all live-toggleable. `GFileMonitor` auto-reload — recompile a LaTeX or Typst doc and the viewer refreshes with scroll position preserved. Strictly a viewer: no annotations, no library, no conversion.

<p class="codex-link"><a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 006</span>
  <div class="codex-body" markdown="1">
### CalibreQuarry
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

A CLI toolkit for power users of Calibre. Zero external dependencies — `sqlite3`, `argparse`, `curses`, and nothing else. Ships a hand-written recursive-descent parser at **100% parity with Calibre's internal search-expression syntax** (validated by an automated test suite); the same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` CLI mode.

Catalog generation grouped by author, library statistics, audit reports (untagged, unrated, coverless, series gaps), `--all-wings` to emit a separate catalog for every virtual library, JSON / CSV export. Auto-snapshots the database when Calibre holds a write lock. Installs as `cquarry`. Considered complete software — fully tested on Fedora 43 against Calibre 9.7.

<p class="codex-link"><a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 007</span>
  <div class="codex-body" markdown="1">
### deadbeef-cui
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.2.3</span></p>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full DeaDBeeF title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, and an in-pane search bar (`Ctrl+Shift+F`). Targets a dedicated "Library Viewer" playlist so it never touches the user's curated playlists. Built natively against `DB_mediasource_t`. Effectively complete — fixes only.

<p class="codex-link"><a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 008</span>
  <div class="codex-body" markdown="1">
### project-void
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> Tiled <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

A design-stage CRPG in the lineage of *Dark Sun: Shattered Lands*, *Fallout 2*, *Arcanum*, and *Disco Elysium*. Lethal *Cairn* combat math: attacks hit automatically, HP is low, damage drains into real wounds via attribute damage — combat as a positional puzzle, not a dice minigame. Fallout-style character sheet. Low-fantasy world that owes more to Joe Abercrombie than to Tolkien.

Ships as two products: **The Reach** — a tight 15–20-hour campaign through a patchwork region of city-states, free companies, counting houses, an inquisition, and a ruined library-city — and **The Engine**, a data-driven moddable platform. The ruleset is decoupled from the engine via universal TOML/Lua state machines, so the same engine could host *Cairn*, 5e, or anything else with a sheet and a turn order.

<p class="codex-link"><a href="https://github.com/VirInvictus/project-void">github.com/VirInvictus/project-void →</a></p>
  </div>
</div>

<p class="ornament ornament--asterism">⁂</p>

## III. Marginalia
{: #marginalia}

When I am not writing code I am usually busy with other forms of world-building. Most of these projects exist because I am trying to be a better steward of one collection or another — the overlap with off-screen taste is not coincidental.

<dl class="marginalia">
  <dt>Reading</dt>
  <dd>10–20 books a year. Grimdark fantasy, cyberpunk, horror. Authors I return to: <strong>Joe Abercrombie</strong>, <strong>Brandon Sanderson</strong>, <strong>Morgan Housel</strong>, <strong>Terry Pratchett</strong>.</dd>

  <dt>Collecting</dt>
  <dd>TTRPGs, mostly. Obsessing over their well-built systems, beautiful art, and the concepts kept behind their front pages.</dd>

  <dt>Music</dt>
  <dd>Hip-hop, post-hardcore, mid-'00s-to-mid-'10s emo. On rotation: <strong>Brand New</strong>, <strong>50 Cent</strong>, <strong>Ka</strong>, <strong>Ólafur Arnalds</strong>, <strong>Self Defense Family</strong>.</dd>

  <dt>Food</dt>
  <dd>Chefs I follow (and one place I sat down at): <strong>David Chang</strong>; <strong>David McMillan & Frédéric Morin</strong> at <strong>Joe Beef</strong> (ate there myself — a high point); <strong>Danny Bowien</strong> (Mission Chinese); <strong>Daniel Patterson</strong> (Coi).</dd>

  <dt>Games</dt>
  <dd>Dark Souls 3. RimWorld. Hollow Knight. Dwarf Fortress. <em>project-void</em> is the answer to "what would I want next?"</dd>
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
