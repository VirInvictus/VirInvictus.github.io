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

Thirty projects. Native Linux desktop software at the centre, with games and game-design work, KOReader companions, a calibre-web theme, an Emacs theme, and a few small single-purpose tools at the edges. Local-first by default; the throughline is curation. Atrium is the largest piece and the one in motion; the rest sort by current state.

<div class="codex-entry">
  <span class="codex-num">No. 001</span>
  <div class="codex-body" markdown="1">
### [Atrium]({{ '/codex/atrium/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.69.2</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/atrium-today.webp' | relative_url }}" alt="Atrium's Today view: six canonical lists in the sidebar, coloured tag pills, and the Area › Project chip on each row" loading="lazy">
</div>

The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface that never asks you to open Emacs. **Simple Mode** for *what am I doing right now* (six canonical lists, no defer dates, Things 3 calm); **Builder Mode** for the days the system has to do the work (Forecast, Agenda, Kanban, Calendar, Review with per-area cadences that cascade to the projects filed under an area, Perspectives, repeating and sequential projects, blocked-by task dependencies, time-based system reminders, a live Inspector). Same data, two surfaces, no migration: flipping modes is a UI re-render over an OmniFocus-superset schema that was there on day one.

<p class="codex-link"><a href="{{ '/codex/atrium/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 002</span>
  <div class="codex-body" markdown="1">
### [Viaduct]({{ '/codex/viaduct/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v3.2.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/viaduct-main.webp' | relative_url }}" alt="Viaduct's three-pane layout: feed sidebar with unread counts, article timeline, and the reading pane on the v3.0 flat Kanagawa design" loading="lazy">
</div>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary, making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** against ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

<p class="codex-link"><a href="{{ '/codex/viaduct/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 003</span>
  <div class="codex-body" markdown="1">
### [Hermitage]({{ '/codex/hermitage/' | relative_url }})
<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">active · v0.18.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/hermitage-gallery.webp' | relative_url }}" alt="Hermitage's cover-art grid filtered to a virtual library, with the Wing sidebar open and the search bar showing the active expression" loading="lazy">
</div>

Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: an edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive genre browser that unfolds dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

<p class="codex-link"><a href="{{ '/codex/hermitage/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 004</span>
  <div class="codex-body" markdown="1">
### [Lattice]({{ '/codex/lattice/' | relative_url }})
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status status--complete">complete · v4.10.2</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/lattice-tui.webp' | relative_url }}" alt="Lattice's curses TUI: a bordered menu grouped into Library, Integrity, Artwork, Metadata, and Settings sections" loading="lazy">
</div>

Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre. Parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shelling out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking, an art-quality audit against a configurable resolution floor, and tag, bitrate, and duplicate audits. Smart `.m3u` generation from dynamic rules (`rating >= 4 and genre == 'Jazz'`), per-genre **wings** (one library file per genre, like Calibre virtual libraries for music), and a token-efficient `--ai-library` export sized to fit a 4,000-album collection inside an LLM context window. The directory layout is configurable, so the tools never fight you about your shelving. Bare `lattice` opens a full-screen curses TUI.

<p class="codex-link"><a href="{{ '/codex/lattice/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 005</span>
  <div class="codex-body" markdown="1">
### [Framework]({{ '/codex/framework/' | relative_url }})
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.82.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/framework-viewer.webp' | relative_url }}" alt="Framework rendering a 168-page PDF with the table-of-contents sidebar open and two pages visible in the scroll" loading="lazy">
</div>

A native Linux document viewer for **PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, and Markdown**: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux. A three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction, parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline that builds the pixmap *around* the Cairo surface buffer.

<p class="codex-link"><a href="{{ '/codex/framework/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 006</span>
  <div class="codex-body" markdown="1">
### [CalibreQuarry]({{ '/codex/calibrequarry/' | relative_url }})
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v3.9.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/calibrequarry-stats.webp' | relative_url }}" alt="CalibreQuarry's --stats output: hierarchical dot-taxonomy tag counts, series with book totals, publishers, languages, and recent additions" loading="lazy">
</div>

Calibre power-user tooling with zero external dependencies: `sqlite3`, `argparse`, `curses`, and nothing else. Its hand-written recursive-descent parser hits **100% parity with Calibre's internal search-expression syntax**, validated by a test suite mapped against Calibre's own `SearchQueryParser`. The same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` mode (author / `vl:` / boolean / parens / `=`-prefix exact match).

<p class="codex-link"><a href="{{ '/codex/calibrequarry/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 007</span>
  <div class="codex-body" markdown="1">
### [deadbeef-cui]({{ '/codex/deadbeef-cui/' | relative_url }})
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.3</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/deadbeef-cui-facets.webp' | relative_url }}" alt="deadbeef-cui's three facet columns narrowing genre, album artist, and album above the playlist, with cover art and a waveform seekbar" loading="lazy">
</div>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, an in-pane search bar (`Ctrl+Shift+F`), and a settings dialog with per-instance configuration so multiple Facet Browsers can coexist in one layout.

<p class="codex-link"><a href="{{ '/codex/deadbeef-cui/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 008</span>
  <div class="codex-body" markdown="1">
### [Belfry]({{ '/codex/belfry/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--retired">retired → Conservatory</span></p>

A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can `ls`. Smart Speed and Voice Boost are ffmpeg filter chains (`silenceremove`, `acompressor`, `loudnorm`, `rubberband`) calibrated against Overcast; the Castro **Inbox → Queue → Played** flow was the daily metaphor. The same single-writer SQLite worker that Viaduct and Atrium use fed four concurrent producers here, with Calibre's library-as-database UX (filter grammar, sortable columns, bulk actions, saved Perspectives) layered over the triage states.

<p class="codex-link"><a href="{{ '/codex/belfry/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Belfry">github.com/VirInvictus/Belfry →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 009</span>
  <div class="codex-body" markdown="1">
### [Conservatory]({{ '/codex/conservatory/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status">active · v0.3.12</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/conservatory-library.webp' | relative_url }}" alt="Conservatory's music library: three Columns UI facet panes over genre, album artist, and album, above a rated track list and the player bar" loading="lazy">
</div>

Conservatory *owns and organizes* your music, podcasts, and audiobooks on disk, presenting them through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs all three media types from one queue. Designed as **Calibre for audio**.

<p class="codex-link"><a href="{{ '/codex/conservatory/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Conservatory">github.com/VirInvictus/Conservatory →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 010</span>
  <div class="codex-body" markdown="1">
### [project-void]({{ '/codex/project-void/' | relative_url }})
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> Tiled <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

A design-stage CRPG and the data-driven engine that ships under it. The engineering commitment is the engine: rules expressed as universal TOML/Lua state machines, decoupled from the renderer, so the same binary could host *Cairn*, 5e, or any other system with a sheet and a turn order. The campaign is the demonstration. **The Reach** is a tight 15–20-hour run through a region of city-states, free companies, counting houses, an inquisition, and a ruined library-city.

<p class="codex-link"><a href="{{ '/codex/project-void/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 011</span>
  <div class="codex-body" markdown="1">
### [project-yeschef]({{ '/codex/project-yeschef/' | relative_url }})
<p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> TOML <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

*YES CHEF* (working title): a single-player, character-driven grand-strategy restaurant simulation in the lineage of *Crusader Kings 3* and *Victoria 3*, pointed at the most volatile small business there is. You play the General Manager. You do not cook. You hire, fire, schedule, invest, negotiate, and hold the room together while the restaurant tries to kill itself around you. People are the system: every mechanic flows through characters with stats, traits, opinions, and agendas, and the food is what comes out of the humans who make it.

<p class="codex-link"><a href="{{ '/codex/project-yeschef/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 012</span>
  <div class="codex-body" markdown="1">
### [opends]({{ '/codex/opends/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> Python <span class="stack-sep">·</span> Reverse engineering <span class="stack-sep">·</span> DOSBox <span class="stack-sep">·</span> <span class="status">active</span></p>

An open community toolkit and bugfix-patch project for SSI's *Dark Sun* CRPGs, *Shattered Lands* (1993) and *Wake of the Ravager* (1994). Tools first, patches second: a GFF container reader/writer, a GPL bytecode disassembler and byte-exact reassembler, a dialog extractor, a save inspector, and a region renderer, each a standalone MIT-licensed tool with its own README and version. Twelve ship today, working and tested (142 passing tests across a six-crate Rust workspace, with stdlib-Python companions). Nothing here redistributes a byte of the game: you bring your own GOG copy, and the toolkit reads and patches it through an overlay mount that never touches the original install. The *darkfix* patches the tools exist to produce are the next milestone, not yet shipped.

<p class="codex-link"><a href="{{ '/codex/opends/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/opends">github.com/VirInvictus/opends →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 013</span>
  <div class="codex-body" markdown="1">
### [kanagawa-dragon-nvim-emacs]({{ '/codex/kanagawa-dragon-nvim-emacs/' | relative_url }})
<p class="codex-meta">Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.3</span></p>

A faithful Emacs port of the Dragon variant from [kanagawa.nvim](https://github.com/rebelot/kanagawa.nvim). Not a repackaging of the existing `kanagawa-themes` package; that one has the palette right but covers too few faces to hold up in practice. This one maps the full set: every Emacs 29+ tree-sitter `font-lock-*` face, all Doom-specific surfaces (`doom-modeline-*`, `solaire-mode`, `doom-dashboard-*`), org-mode faces, magit, company, corfu, and the rest of the usual zoo. Implemented as a vanilla `deftheme` with no `doom-themes` macro dependency, so it works in stock Emacs and in Doom alike.

<p class="codex-link"><a href="{{ '/codex/kanagawa-dragon-nvim-emacs/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> not yet public</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 014</span>
  <div class="codex-body" markdown="1">
### [Bindery]({{ '/codex/bindery/' | relative_url }})
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.10.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/bindery-sweep.webp' | relative_url }}" alt="Bindery's dry-run library sweep: per-book epubcheck results above a summary table ending in 'no files written'" loading="lazy">
</div>

A command-line surgeon for malformed EPUBs. The fixes are deliberately boring: self-close the void elements, convert named entities to numeric, sync the NCX `uid` with the OPF, put the `mimetype` entry first in the zip. Each one is deterministic, and each one lands only if [epubcheck](https://github.com/w3c/epubcheck) confirms the patient actually improved. epubcheck stays an external oracle, never a Python dependency; the package itself is stdlib only. Dry-run is the default mode, and `--apply` backs up before it touches anything.

<p class="codex-link"><a href="{{ '/codex/bindery/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Bindery">github.com/VirInvictus/Bindery →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 015</span>
  <div class="codex-body" markdown="1">
### [oceanstrip]({{ '/codex/oceanstrip/' | relative_url }})
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

Strips producer and redistributor watermarks out of EPUBs. What began as an OceanofPDF.com-only tool is now a small signature registry: OceanofPDF's injected link (and its stray marker file), and the ABC Amber LIT Converter stamp that old `.lit` conversions leave on nearly every page, each caught in both an anchored form (the stamp is a link) and an anchorless form (plain text, with no `<a>` to catch). Adding another producer is one table entry. The removal is balanced-element surgery rather than regex slicing: find the stamp, walk up to the outermost wrapper whose entire visible text is the watermark, and delete that whole well-formed element, so real prose that merely mentions the URL is never touched and a well-formed file stays well-formed. Works on a single file or sweeps an entire library, always writing new copies (originals are never modified), and every output is epubcheck-clean. Stdlib only, like its sibling Bindery.

<p class="codex-link"><a href="{{ '/codex/oceanstrip/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Oceanstrip">github.com/VirInvictus/Oceanstrip →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 016</span>
  <div class="codex-body" markdown="1">
### [AudiobookTools]({{ '/codex/audiobooktools/' | relative_url }})
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> <span class="status">active · v0.2.0</span></p>

One catalogue file is the source of truth for an entire audiobook shelf: `retag` writes the embedded metadata from it, `reorg` renders the on-disk folder tree from it, and the files and the shelf cannot drift apart because both are projections of the same data. The engine is generic and the catalogue is data; the two never mix.

<p class="codex-link"><a href="{{ '/codex/audiobooktools/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/AudiobookTools">github.com/VirInvictus/AudiobookTools →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 017</span>
  <div class="codex-body" markdown="1">
### [Hearth]({{ '/codex/hearth/' | relative_url }})
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v0.12.1</span></p>

A native, two-player, local-network, fully offline digital build of a worker-placement and polyomino-economy Eurogame, riding on a content-agnostic engine built to outlive any one theme. The board, the goods, and the cards are data; the engine keeps a pure `State` / `Rules` / `Scoring` / `Loader` split so the same binary could host a different game with a sheet and a turn order. The distinctive subsystems are the home-board polyomino puzzle and a pure effect vocabulary the cards reuse: every action is a non-mutating transform over game state, which keeps the rules testable away from the renderer.

<p class="codex-link"><a href="{{ '/codex/hearth/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 018</span>
  <div class="codex-body" markdown="1">
### [Haveli]({{ '/codex/haveli/' | relative_url }})
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.0.0</span></p>

Two players, one LAN, no internet at any point: a digital build of a fast set-collection card game on a content-agnostic, deterministic engine. Sibling in shape to Hearth, but where Hearth's puzzle is the board, Haveli's is hidden information and reproducible randomness. It is a shuffled-deck game, so determinism is foundational: an `rng_seed` plus a draw cursor make every shuffle and every market refill replayable from the state alone, which is what lets the network layer stay honest.

<p class="codex-link"><a href="{{ '/codex/haveli/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, shipped v1.0.0</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 019</span>
  <div class="codex-body" markdown="1">
### [Colophon]({{ '/codex/colophon/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Cairo <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v2.1.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/colophon-per-book.webp' | relative_url }}" alt="Colophon's per-book view: a reading-stats table above the pace-through-the-book and reading-speed charts, all drawn in Cairo" loading="lazy">
</div>

A native Linux statistics viewer for [KOReader](https://koreader.rocks/). KOReader tracks a surprising amount about how you read (per-page timing, session history, running totals), and every existing way to look at that data is a web dashboard or a self-hosted Docker service. Colophon is neither: a local desktop app that imports a *copy* of `statistics.sqlite3` (staged, validated, never opened in place) and turns it into the analytics nobody else ships. A reading-speed trend across the library with a per-book overlay; a weekday-by-hour *when do I read* heatmap; session-length histograms and starts-by-hour patterns; a per-page activity strip that answers *did it drag in the middle*; inferred read-through detection with per-completion cards; a reading-personality card that reads traits (chronotype, session style, weekly rhythm) off your own behaviour; and the expected furniture (year heatmap, streaks, device-parity stat cards) done carefully. Per-book `.sdr` sidecars are strictly opt-in and user-provided: hand it one and the device's own finished verdict becomes authoritative over the position-based guess and your highlights land at their true place on the activity strip, but nothing on the device is ever scanned.

<p class="codex-link"><a href="{{ '/codex/colophon/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Colophon">github.com/VirInvictus/Colophon →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 020</span>
  <div class="codex-body" markdown="1">
### [Dead Reckoning]({{ '/codex/dead-reckoning/' | relative_url }})
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

The smallest thing in the collection: a preset for the [Bookends](https://github.com/AndyHazz/bookends.koplugin) KOReader plugin, styled as a navigation cockpit for the book in progress. Session pace in pages per hour, a chapter ETA, a projected finish date reckoned from the current pace, and a tick on the progress bar at every chapter waypoint. The telemetry renders in a soft low-contrast grey so the instruments never compete with the page. One Lua file; drop it in the presets folder.

<p class="codex-link"><a href="{{ '/codex/dead-reckoning/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/dead-reckoning-bookend-preset">github.com/VirInvictus/dead-reckoning-bookend-preset →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 021</span>
  <div class="codex-body" markdown="1">
### [Kobo-style Sleepscreen Banner]({{ '/codex/kobo-style-sleepscreen-banner/' | relative_url }})
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

A KOReader user patch that redraws the stock sleep screen as a Kobo-lockscreen-style floating card over your book cover: a serif title, a stats line, and a random highlight pulled from the last book you were reading, set as an italic pull-quote with an accent rule and a "saved on..." footer. The card carries a real visual identity, rounded corners over a hard offset drop shadow so it reads as a tag sitting above the cover, with per-element font control wired for the [ebook-fonts](https://github.com/nicoverbruggen/ebook-fonts) collection out of the box. It draws once on suspend, so there is no E Ink refresh cost while you read. Honest about its lineage: a prettified fork of zenixlabs' community patch (which designed the Kobo banner and the random-highlight feature), credited in the source header and README; this fork contributes the floating-card design and the font wiring. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `2-` prefix so it loads after KOReader's widget system. The third of the KOReader companions, alongside Colophon and Dead Reckoning.

<p class="codex-link"><a href="{{ '/codex/kobo-style-sleepscreen-banner/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified">github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 022</span>
  <div class="codex-body" markdown="1">
### [1-timezone]({{ '/codex/1-timezone/' | relative_url }})
<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

The tiniest fix in the collection, born from a real annoyance: on a jailbroken Kindle that boots straight into KOReader, no framework hands the process a timezone, so the base system falls back to a bogus Local Mean Time offset and every clock in the app is wrong by an odd fraction of an hour. "Synchronize time" never helps, because it corrects the instant, not the offset. This patch sets a real POSIX `TZ` inside the process and calls `tzset()` early, before the first clock read, so the footer clock, time sync, and AutoWarmth all agree again, with daylight saving flipping on its own. It ships defaulting to Eastern Time; one labelled line retargets it to any zone. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `1-` prefix so it runs first. The fourth of the KOReader companions, alongside Colophon, Dead Reckoning, and the Sleepscreen Banner.

<p class="codex-link"><a href="{{ '/codex/1-timezone/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/1-timezone">github.com/VirInvictus/1-timezone →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 023</span>
  <div class="codex-body" markdown="1">
### [Carrel]({{ '/codex/carrel/' | relative_url }})
<p class="codex-meta">Python <span class="stack-sep">·</span> Flask <span class="stack-sep">·</span> CSS <span class="stack-sep">·</span> <span class="status">active · v0.9.1</span></p>

A carrel is a private desk in a library, and that is the whole design brief: no accounts, no sharing, no dashboard. One reader, seven thousand books, and an interface that gets out of the way. Built on [calibre-web](https://github.com/janeczku/calibre-web), it has since become a different program.

<p class="codex-link"><a href="{{ '/codex/carrel/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Carrel">github.com/VirInvictus/Carrel →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 024</span>
  <div class="codex-body" markdown="1">
### [Coffer]({{ '/codex/coffer/' | relative_url }})
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> hledger <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

Envelope budgeting over a plain-text [hledger](https://hledger.org/) journal: Actual Budget's experience, hledger's data discipline, two-way. Atrium's sibling, but for money, and with the polarity inverted: the journal *is* the database, any SQLite is a disposable read cache, and the app shells out to the `hledger` binary for its reports rather than reimplementing the ledger. The hard problem, and the reason the research phase is real, is a safe append-and-edit write-back path onto a file the user also edits by hand.

<p class="codex-link"><a href="{{ '/codex/coffer/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Coffer">github.com/VirInvictus/Coffer →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 025</span>
  <div class="codex-body" markdown="1">
### [rd-cli]({{ '/codex/rd-cli/' | relative_url }})
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/rd-cli-list.webp' | relative_url }}" alt="rd-cli listing a collection: bookmark ids, titles, and URLs in designed ANSI colour, followed by account stats" loading="lazy">
</div>

Talks to the [Raindrop.io](https://raindrop.io/) bookmarking service with nothing from PyPI, built the way the other stdlib tools here are: `urllib`, `json`, `argparse`, `tomllib`. It covers the REST API a single user actually touches: raindrops, collections, tags, and highlights, plus the account endpoints (user, stats, filters, import-dedup, export, backups). Every command speaks two languages, designed ANSI for a human at a terminal and `--json` for scripts and agents, so the one binary is both a daily driver and an automation surface.

<p class="codex-link"><a href="{{ '/codex/rd-cli/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/rd-cli">github.com/VirInvictus/rd-cli →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 026</span>
  <div class="codex-body" markdown="1">
### [Catagotchi]({{ '/codex/catagotchi/' | relative_url }})
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v4.5.1</span></p>

A cozy cat tamagotchi wrapped around a Cookie-Clicker-scale idle empire, and the largest thing here that is not a desktop app. The two halves are welded together rather than stacked: five needs average into a *mood multiplier* running ×0.5 to ×2.0 that scales **all** gold income, so a neglected cat is not a guilt mechanic, it is a halved economy. Above that sit eight generators with endless ×2 and ×5 upgrade ladders, three skill trees, fourteen adventures, five story dungeons plus an infinite Endless Depths on seeded floor modifiers, a globally deterministic commodity exchange, and two layers of prestige. Six daily puzzle games (sudoku, crossword, jigsaw, memory, rhythm, and a hidden-object mode) rotate on a four-hour seed that is the same for every player, so a daily is a shared board rather than a private roll.

<p class="codex-link"><a href="{{ '/codex/catagotchi/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 027</span>
  <div class="codex-body" markdown="1">
### [Hearthfall]({{ '/codex/hearthfall/' | relative_url }})
<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> Textual <span class="stack-sep">·</span> <span class="status">active · v0.1.1</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/hearthfall-run.webp' | relative_url }}" alt="Hearthfall mid-run: the clan panel and fog-black map at left, the season log at right, and a story event offering two choices" loading="lazy">
</div>

A grimdark clan-survival game for the terminal: turn-based, season-timed, and fog-black. You start with a handful of villagers and a map you cannot see, send people out, and the world arrives tile by tile through scarcity, story, and violence. *A Dark Room* that grows a spine into *King of Dragon Pass*, rendered in glyphs. The design bet is that exploration and combat are the same loop rather than two: scouts reveal terrain **and** enemy composition, so a scout returning with *forty of them, mostly spears, no archers, holding the high ground* is worth more than a sword, and the game lives in assembling the counter-force rather than in the swing.

<p class="codex-link"><a href="{{ '/codex/hearthfall/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> <a href="https://github.com/VirInvictus/Hearthfall">github.com/VirInvictus/Hearthfall →</a></p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 028</span>
  <div class="codex-body" markdown="1">
### [Vestibule]({{ '/codex/vestibule/' | relative_url }})
<p class="codex-meta">Ruby <span class="stack-sep">·</span> pandoc <span class="stack-sep">·</span> Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.0</span></p>

A one-directional converter that turns an Obsidian vault into org-mode files org-roam can index, then installs them into a live Doom setup. Not a sync tool, and that is not a future phase. Half experiment, half write-up: *can you move an Obsidian vault into org-roam* gets asked often and answered in the abstract, usually stopping at "the links and frontmatter are easy, Dataview is impossible."

<p class="codex-link"><a href="{{ '/codex/vestibule/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> private, in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 029</span>
  <div class="codex-body" markdown="1">
### [Foyer]({{ '/codex/foyer/' | relative_url }})
<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> ENet <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.0</span></p>

The shared front door to Hearth (No. 017) and Haveli (No. 018): a small launcher and networked LAN lobby. Pick a game, find the other player on the network, agree the setup, lock in, and Foyer relaunches each side with the right arguments and steps out of the way.

<p class="codex-link"><a href="{{ '/codex/foyer/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> in development</p>
  </div>
</div>

<div class="codex-entry">
  <span class="codex-num">No. 030</span>
  <div class="codex-body" markdown="1">
### [dragon-themer]({{ '/codex/dragon-themer/' | relative_url }})
<p class="codex-meta">Ruby (stdlib only) <span class="stack-sep">·</span> ERB <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

Retheming a tiling desktop means hand-editing the same eight hex values into thirty files and finding the two you missed a week later. dragon-themer makes it one command: one palette as the source of truth, rendered through pure ERB templates into every colour-bearing config on the machine, with each group (desktop, terminal, editor, apps) able to move independently, because a terminal and a desktop do not have to agree.

<p class="codex-link"><a href="{{ '/codex/dragon-themer/' | relative_url }}">Read the full entry →</a> <span class="stack-sep">·</span> in development</p>
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
