# A Second Cup

This is where I'll post observations and thoughts about programming as I pursue my Bachelor's degree in Computer Science. I obsess over curation and organization, and have a natural interest in well-built systems in general.

### Who I am

I'm **Brandon LaRocque** — a sous-chef turned programmer after embracing a life-long obsession with the craft. Software should matter. Good software should be maintained and cared for. I'm a thirty-something Canadian who spent years working in restaurants and mining camps while reading Kernighan & Ritchie's *The C Programming Language* in my bedroom at night.

These days I write systems for people who treat their libraries — books, music, feeds, documents — as curated collections worth maintaining. Most of my work is **native Linux desktop software**: Rust + GTK4, Python, and C built with Meson, all out of Fedora. I lean on the standard library before I reach for a framework, prefer compile-time boundaries over code-review rules, and would rather port a battle-tested architecture than invent a new one.

Outside of those tools, I've also built Discord bots — quote-archive bots, multi-server moderation utilities, and game-night helpers for friends and small communities.

### Projects

#### [Viaduct](https://github.com/VirInvictus/Viaduct) — *Rust, GTK4, tokio*

A Linux port of [NetNewsWire](https://netnewswire.com/) (Brent Simmons' macOS RSS reader). A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary — making the architectural boundary a compile error rather than a code-review rule. Idles at 100–300 MB versus ~600 MB for the closest Linux competitor, with a hard 500 MB ceiling enforced by an in-tree `mem_check` harness. Single-writer SQLite worker on tokio, OPML on disk as the source of truth (NNW-compatible byte-for-byte), FTS5 search, and exactly one neutered WebKit instance for the article pane (JS / WebGL / WebRTC / DevTools / LocalStorage off, strict CSP, images routed through a custom `viaduct-img://` URI scheme). Ships all eight NetNewsWire article themes and an Adwaita theme.

#### [Hermitage](https://github.com/VirInvictus/Hermitage) — *Python 3.14, GTK4, Libadwaita*

A local-first, native gallery for Calibre libraries. Built for the single user who wants a modern desktop experience without Docker containers or a web auth layer. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: edge-to-edge cover grid with median-cut color quantization for per-book accent tinting, hero-banner detail sidebar, recursive tag-hierarchy genre browser, and full Calibre virtual-library support. A 512-entry texture LRU and a three-tier color cache keep scrolling smooth on integrated graphics.

#### [CalibreQuarry](https://github.com/VirInvictus/CalibreQuarry) — *Python (stdlib only)*

A CLI toolkit for power users of Calibre. Zero external dependencies — `sqlite3`, `argparse`, `curses`, and nothing else. Includes a hand-written recursive-descent parser at **100% parity with Calibre's internal search-expression syntax** (validated by an automated test suite); the same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` CLI mode. Catalog generation, library statistics, audit reports (untagged / unrated / coverless / series gaps), and JSON/CSV export. Auto-snapshots the database when Calibre holds a write lock.

#### [Lattice](https://github.com/VirInvictus/Lattice) — *Python, Mutagen, FFmpeg*

A toolkit for music collectors who keep the filesystem as the source of truth. Library tree visualization, parallel FLAC / MP3 / Opus / WAV / WMA integrity verification, embedded cover-art extraction with format-priority ranking (FLAC → Opus → M4A → MP3), tag and bitrate audits, duplicate detection across formats, smart `.m3u` playlist generation, and a token-efficient `--ai-library` export designed to fit a 4,000-album collection inside an LLM context window. Ships with `retag.py`, a companion that abstracts away ID3 / Vorbis / iTunes-atom multi-genre chaos for safe directory-wide retagging.

#### [Framework](https://github.com/VirInvictus/Framework) — *C, Meson, GTK4, MuPDF*

A native GNOME document viewer for PDF and DjVu. Designed to fill the gap between feature-heavy clients (Okular) and bare MuPDF wrappers — a SumatraPDF-shaped experience for Linux. Two-tier cache separates parsed page objects from rendered Cairo surfaces, parallel rendering across MuPDF instances, and a *velocity engine* that throttles render jobs by scroll speed so fast-scrolling never queues stale work. HiDPI-aware on Wayland. Strictly a viewer — no annotations, no library, no conversion.

#### [deadbeef-cui](https://github.com/VirInvictus/deadbeef-cui) — *C/C++, GTK3*

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full DeaDBeeF title-formatting support, multi-select aggregation, and an in-pane search bar. Targets a dedicated "Library Viewer" playlist so it never touches the user's curated playlists. Built natively against `DB_mediasource_t`. Considered effectively complete.

#### [project-void](https://github.com/VirInvictus/project-void) — *Godot 4, Lua, Ink, Tiled, TOML*

Design-stage CRPG in the lineage of *Dark Sun: Shattered Lands*, *Fallout 2*, *Arcanum*, and *Disco Elysium*. Lethal *Cairn* combat math, Fallout-style character sheet, low-fantasy world that owes more to Joe Abercrombie than Tolkien. Ships as two products: **The Reach** (a 15–20 hour campaign) and **The Engine** (a data-driven moddable platform). The ruleset is decoupled from the engine via universal TOML/Lua state machines, so the same engine could host *Cairn*, 5e, or anything else with a sheet and a turn order.

### Beyond the terminal

When I'm not writing code, you'll likely find me immersed in other forms of world-building. Most of these projects exist because I'm trying to be a better steward of one collection or another — the overlap with off-screen taste is not coincidental.

- **Reading:** I try to read 10–20 books a year. My primary obsessions are grimdark fantasy, cyberpunk, and anything horror. Authors I return to: **Joe Abercrombie, Brandon Sanderson, Morgan Housel, Terry Pratchett**. Follow me on GoodReads or BookWyrm for reviews.
- **Collecting:** I'm an avid collector of TTRPGs — obsessing over their well-built systems, beautiful art, and the concepts kept behind their front pages.
- **Music:** Has been one of the most important things in my life since I was a teenager. Favourite genres: hip-hop, post-hardcore, and mid-'00s-to-mid-'10s emo. On rotation: **Brand New, 50 Cent, Ka, Ólafur Arnalds, Self Defense Family**.
- **Food:** Chefs I've followed (and one place I sat down at): **David Chang**, the crew at **Joe Beef** (ate there myself — a high point), **Danny Bowien** (Mission Chinese), **Daniel Patterson** (Coi).
- **Games that took the most hours:** Dark Souls 3, RimWorld, Hollow Knight, Dwarf Fortress.

This space is a collection of my thoughts, code, and the various projects I'm currently cultivating. Thanks for stopping by.

### Recent blog posts
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span style="color: #a1a1aa; font-size: 0.9em; margin-left: 10px;">{{ post.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
</ul>
