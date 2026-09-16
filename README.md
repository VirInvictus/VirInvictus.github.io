---
layout: default
image: /assets/img/og-card.png
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
My work focuses on native Linux desktop software. I build with Rust and GTK4, C built with Meson, and Python where the standard library reaches. Everything is local-first by default. I rely on SQLite in WAL mode with a single-writer worker, read-only connection pools, and FTS5 for search. No cloud accounts. No Docker. No Electron. No telemetry.
</div>

Where a rule can be a compile error instead of a convention, I make it one. I would rather ship against a hard memory ceiling than an optional benchmark, and I will port a battle-tested architecture with attribution before I invent a new one.

I came to this work late. I spent nearly twenty years in restaurants and mining camps before picking up *The C Programming Language*. I read it at night between shifts because the cover looked serious and I wanted to know what serious looked like. I am a Computer Engineering Technician student now with a CS bachelor's underway at Algoma; the paperwork is catching up to two decades of practice.

By temperament I am an archivist. I keep a private Calibre library that runs into the four figures, a music collection sorted by hand, and an RSS spool I read every morning. Friends have called the practice *shadow librarianship*. The catalogue is my own, kept on my own disks, and indexed by my own tools. Most of what I build is designed for people who treat their library as a resource worth maintaining.

The site is named *Vir Invictus*, *the unconquered*. I picked it a long time ago and it stuck.

<p class="ornament ornament--fleuron">❦</p>

## II. The Collection
{: #the-collection}

Native Linux desktop software sits at the centre, with games, KOReader companions, and small utilities at the edges. Local-first is the default; the throughline is curation. What follows is a selection of the most active work. Atrium is the largest piece in motion. The rest are sorted by category.

### Applications

<div class="codex-grid">
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 001</span>
<h3><a href="{{ '/codex/atrium/' | relative_url }}">Atrium</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.76.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/atrium-today.webp' | relative_url }}" alt="Atrium's Today view: six canonical lists in the sidebar, coloured tag pills, and the Area › Project chip on each row" loading="lazy">
</div>
<p class="card-desc">The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface styled by vir-gtk that never asks you to open Emacs, with search powered by vir-search.</p>
<p class="card-link-container"><a href="{{ '/codex/atrium/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 002</span>
<h3><a href="{{ '/codex/viaduct/' | relative_url }}">Viaduct</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v4.0.2</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/viaduct-main.webp' | relative_url }}" alt="Viaduct's three-pane layout: feed sidebar with unread counts, article timeline, and the reading pane on the v3.0 flat Kanagawa design" loading="lazy">
</div>
<p class="card-desc">A Linux port of Brent Simmons\' <a href="https://netnewswire.com/">NetNewsWire</a> RSS reader. Styled by vir-gtk with search powered by vir-search.</p>
<p class="card-link-container"><a href="{{ '/codex/viaduct/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 003</span>
<h3><a href="{{ '/codex/framework/' | relative_url }}">Framework</a></h3>
<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.0.1</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/framework-viewer.webp' | relative_url }}" alt="Framework rendering a 168-page PDF with the table-of-contents sidebar open and two pages visible in the scroll" loading="lazy">
</div>
<p class="card-desc">A native Linux document viewer for <strong>PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, TXT, and Markdown</strong>: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux.</p>
<p class="card-link-container"><a href="{{ '/codex/framework/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 004</span>
<h3><a href="{{ '/codex/raindrop-cli/' | relative_url }}">raindrop-cli</a></h3>
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.6.1</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/raindrop-cli-list.webp' | relative_url }}" alt="raindrop-cli output showing bookmarked links" loading="lazy">
</div>
<p class="card-desc">Dependency-free CLI for raindrop.io and pinboard. Full REST API coverage over stdlib <code>urllib</code>; designed ANSI for humans and <code>--json</code> for scripts and agents, typed errors, rate-limit backoff, <code>--dry-run</code> on every write, blast-radius-gated confirmation prompts, and a two-way additive sync between the two services.</p>
<p class="card-link-container"><a href="{{ '/codex/raindrop-cli/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 005</span>
<h3><a href="{{ '/codex/vir-gtk/' | relative_url }}">vir-gtk</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">active · v1.4.2</span></p>
</div>
<p class="card-desc">A standalone Rust library extracting the shared GTK4 styling and D-Bus portal interaction layer for the VirInvictus desktop suite, providing the foundational visual identity without libadwaita.</p>
<p class="card-link-container"><a href="{{ '/codex/vir-gtk/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 006</span>
<h3><a href="{{ '/codex/vir-search/' | relative_url }}">vir-search</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> <span class="status">active · v1.4.3</span></p>
</div>
<p class="card-desc">A domain-agnostic Rust library for parsing Calibre-style search expressions into a typed AST. It provides the lexer, generic recursive-descent parser, and date-range resolvers that underpin the VirInvictus ecosystem.</p>
<p class="card-link-container"><a href="{{ '/codex/vir-search/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
</div>

### Books & Calibre

<div class="codex-grid">
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 007</span>
<h3><a href="{{ '/codex/hermitage/' | relative_url }}">Hermitage</a></h3>
<p class="codex-meta">Python 3.13+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.8.5</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/hermitage-gallery.webp' | relative_url }}" alt="Hermitage's cover-art grid filtered to a virtual library, with the Wing sidebar open and the search bar showing the active expression" loading="lazy">
</div>
<p class="card-desc">Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way, powered by cquarry.</p>
<p class="card-link-container"><a href="{{ '/codex/hermitage/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 008</span>
<h3><a href="{{ '/codex/calibrequarry/' | relative_url }}">CalibreQuarry</a></h3>
<p class="codex-meta">Python <span class="stack-sep">·</span> cquarry <span class="stack-sep">·</span> vir-tui <span class="stack-sep">·</span> <span class="status">active · v3.45.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/calibrequarry-stats.webp' | relative_url }}" alt="CalibreQuarry's --stats output: hierarchical dot-taxonomy tag counts, series with book totals, publishers, languages, and recent additions" loading="lazy">
</div>
<p class="card-desc">Calibre power-user tooling built on cquarry: catalogs, statistics, integrity audits, and write-capable curation verbs behind <code>--apply</code>-shaped guards. Installs from PyPI as <code>calibrequarry</code>.</p>
<p class="card-link-container"><a href="{{ '/codex/calibrequarry/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 009</span>
<h3><a href="{{ '/codex/bindery/' | relative_url }}">bindery-cli</a></h3>
<p class="codex-meta">Python (tqdm) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.41.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/bindery-cli-sweep.webp' | relative_url }}" alt="bindery-cli's dry-run library sweep: per-book epubcheck results above a summary table ending in 'no files written'" loading="lazy">
</div>
<p class="card-desc">A command-line surgeon for malformed EPUBs. Evaluates thousands of books in minutes, repairing structural defects, unwrapping illegal HTML markup, and auditing for content damage (OCR, wrong-language tags) before swapping the fixed formats natively into your Calibre database via cquarry.</p>
<p class="card-link-container"><a href="{{ '/codex/bindery/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 010</span>
<h3><a href="{{ '/codex/cquarry/' | relative_url }}">cquarry</a></h3>
<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v1.23.1</span></p>
</div>
<p class="card-desc">A lightweight, canonical Python package providing read-only access to Calibre's <code>metadata.db</code> and a full parser for Calibre's native search expression grammar; the opt-in <code>cquarry.write</code> module is the ecosystem's only sanctioned write path.</p>
<p class="card-link-container"><a href="{{ '/codex/cquarry/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
</div>
### Music & Audio

<div class="codex-grid">
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 011</span>
<h3><a href="{{ '/codex/conservatory/' | relative_url }}">Conservatory</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status">active · v0.8.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/conservatory-library.webp' | relative_url }}" alt="Conservatory's music library: three Columns UI facet panes over genre, album artist, and album, above a rated track list and the player bar" loading="lazy">
</div>
<p class="card-desc">Conservatory <em>owns and organizes</em> your music, podcasts, and audiobooks on disk, presenting them through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs all three media types from one queue. UI styled by vir-gtk and search powered by vir-search.</p>
<p class="card-link-container"><a href="{{ '/codex/conservatory/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 012</span>
<h3><a href="{{ '/codex/lattice/' | relative_url }}">lattice-music</a></h3>
<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status">active · v5.5.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/lattice-music-tui.webp' | relative_url }}" alt="lattice-music's curses TUI: a bordered menu grouped into Library, Integrity, Artwork, Metadata, and Settings sections" loading="lazy">
</div>
<p class="card-desc">Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre.</p>
<p class="card-link-container"><a href="{{ '/codex/lattice/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 013</span>
<h3><a href="{{ '/codex/deadbeef-cui/' | relative_url }}">deadbeef-cui</a></h3>
<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.5</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/deadbeef-cui-facets.webp' | relative_url }}" alt="deadbeef-cui's three facet columns narrowing genre, album artist, and album above the playlist, with cover art and a waveform seekbar" loading="lazy">
</div>
<p class="card-desc">A faceted-browser plugin for the <a href="https://deadbeef.sourceforge.io/">DeaDBeeF</a> music player, bringing foobar2000-style Columns UI / Facets to Linux.</p>
<p class="card-link-container"><a href="{{ '/codex/deadbeef-cui/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
</div>

### KOReader

<div class="codex-grid">
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 014</span>
<h3><a href="{{ '/codex/colophon/' | relative_url }}">Colophon</a></h3>
<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Cairo <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v2.6.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/colophon-per-book.webp' | relative_url }}" alt="Colophon rendering reading statistics with Cairo charts" loading="lazy">
</div>
<p class="card-desc">Native statistics viewer for KOReader. Imports a copy of <code>statistics.sqlite3</code>, draws its own Cairo charts, ships the reading analytics nobody else has.</p>
<p class="card-link-container"><a href="{{ '/codex/colophon/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 015</span>
<h3><a href="{{ '/codex/dead-reckoning/' | relative_url }}">Dead Reckoning</a></h3>
<p class="codex-meta">Lua <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>
</div>
<p class="card-desc">Navigation-cockpit preset for KOReader's bookends plugin: session pace, chapter ETA, projected finish date, and chapter ticks on the progress bar.</p>
<p class="card-link-container"><a href="{{ '/codex/dead-reckoning/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 016</span>
<h3><a href="{{ '/codex/kobo-style-sleepscreen-banner/' | relative_url }}">Sleepscreen Banner</a></h3>
<p class="codex-meta">Lua <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>
</div>
<p class="card-desc">KOReader user patch: redraws the sleep screen as a Kobo-style floating card over your cover, with a random highlight as a pull-quote. A prettified fork of zenixlabs' patch.</p>
<p class="card-link-container"><a href="{{ '/codex/kobo-style-sleepscreen-banner/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 017</span>
<h3><a href="{{ '/codex/1-timezone/' | relative_url }}">1-timezone</a></h3>
<p class="codex-meta">Lua <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>
</div>
<p class="card-desc">KOReader user patch: forces a correct POSIX timezone inside the process (<code>setenv</code> + <code>tzset</code>), fixing the clock, time sync, and autowarmth on framework-less installs where no <code>TZ</code> is set.</p>
<p class="card-link-container"><a href="{{ '/codex/1-timezone/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
</div>

### Games & Engines

<div class="codex-grid">
<div class="codex-card">
<div class="card-header">
<span class="codex-num">No. 018</span>
<h3><a href="{{ '/codex/hearthfall/' | relative_url }}">Hearthfall</a></h3>
<p class="codex-meta">Python <span class="stack-sep">·</span> Textual <span class="stack-sep">·</span> <span class="status">active · v0.28.0</span></p>
</div>
<div class="codex-plate">
<img src="{{ '/assets/img/hearthfall-run.webp' | relative_url }}" alt="Hearthfall's terminal UI showing a map and clan statistics" loading="lazy">
</div>
<p class="card-desc">Grimdark clan-survival for the terminal. Seasonal turns, a fog-black map, and a finite clan split between foraging, exploring, and war. The engine is stdlib-only pure logic with no i/o and no rendering, driveable from a repl; every draw goes through one seeded RNG, so a seed replays a run exactly.</p>
<p class="card-link-container"><a href="{{ '/codex/hearthfall/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
</div>
</div>

### The rest of the codex

The collection keeps eleven more volumes on the shelf, each with its own page: [AudiobookTools]({{ '/codex/audiobooktools/' | relative_url }}), [Carrel]({{ '/codex/carrel/' | relative_url }}), [Catagotchi]({{ '/codex/catagotchi/' | relative_url }}), [dragon-agents]({{ '/codex/dragon-agents/' | relative_url }}), [Haveli]({{ '/codex/haveli/' | relative_url }}), [Hearth]({{ '/codex/hearth/' | relative_url }}), [opends]({{ '/codex/opends/' | relative_url }}), [project-void]({{ '/codex/project-void/' | relative_url }}), [project-yeschef]({{ '/codex/project-yeschef/' | relative_url }}), [Topograph]({{ '/codex/topograph/' | relative_url }}), and [vir-tui]({{ '/codex/vir-tui/' | relative_url }}).

<p class="ornament ornament--fleuron">❦</p>

## III. Dispatches
{: #dispatches}

<ul class="post-list">
  {% for post in site.posts %}
  <li>
    <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
  {% endfor %}
</ul>
