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

<div class="codex-grid">
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 001</span>
      ### [Atrium]({{ '/codex/atrium/' | relative_url }})
      <p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.69.2</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/atrium-today.webp' | relative_url }}" alt="Atrium's Today view: six canonical lists in the sidebar, coloured tag pills, and the Area › Project chip on each row" loading="lazy">
</div>
    <p class='card-desc'>The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface that never asks you to open Emacs.</p>
    <p class='card-link-container'><a href="{{ '/codex/atrium/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 002</span>
      ### [Viaduct]({{ '/codex/viaduct/' | relative_url }})
      <p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v3.2.1</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/viaduct-main.webp' | relative_url }}" alt="Viaduct's three-pane layout: feed sidebar with unread counts, article timeline, and the reading pane on the v3.0 flat Kanagawa design" loading="lazy">
</div>
    <p class='card-desc'>A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader.</p>
    <p class='card-link-container'><a href="{{ '/codex/viaduct/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 003</span>
      ### [Hermitage]({{ '/codex/hermitage/' | relative_url }})
      <p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">active · v0.18.1</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/hermitage-gallery.webp' | relative_url }}" alt="Hermitage's cover-art grid filtered to a virtual library, with the Wing sidebar open and the search bar showing the active expression" loading="lazy">
</div>
    <p class='card-desc'>Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way.</p>
    <p class='card-link-container'><a href="{{ '/codex/hermitage/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 004</span>
      ### [Lattice]({{ '/codex/lattice/' | relative_url }})
      <p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status status--complete">complete · v4.14.0</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/lattice-tui.webp' | relative_url }}" alt="Lattice's curses TUI: a bordered menu grouped into Library, Integrity, Artwork, Metadata, and Settings sections" loading="lazy">
</div>
    <p class='card-desc'>Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre.</p>
    <p class='card-link-container'><a href="{{ '/codex/lattice/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 005</span>
      ### [Framework]({{ '/codex/framework/' | relative_url }})
      <p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.82.0</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/framework-viewer.webp' | relative_url }}" alt="Framework rendering a 168-page PDF with the table-of-contents sidebar open and two pages visible in the scroll" loading="lazy">
</div>
    <p class='card-desc'>A native Linux document viewer for **PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, and Markdown**: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux.</p>
    <p class='card-link-container'><a href="{{ '/codex/framework/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 006</span>
      ### [CalibreQuarry]({{ '/codex/calibrequarry/' | relative_url }})
      <p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v3.11.0</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/calibrequarry-stats.webp' | relative_url }}" alt="CalibreQuarry's --stats output: hierarchical dot-taxonomy tag counts, series with book totals, publishers, languages, and recent additions" loading="lazy">
</div>
    <p class='card-desc'>Calibre power-user tooling with zero external dependencies: `sqlite3`, `argparse`, `curses`, and nothing else.</p>
    <p class='card-link-container'><a href="{{ '/codex/calibrequarry/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 007</span>
      ### [deadbeef-cui]({{ '/codex/deadbeef-cui/' | relative_url }})
      <p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.3</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/deadbeef-cui-facets.webp' | relative_url }}" alt="deadbeef-cui's three facet columns narrowing genre, album artist, and album above the playlist, with cover art and a waveform seekbar" loading="lazy">
</div>
    <p class='card-desc'>A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux.</p>
    <p class='card-link-container'><a href="{{ '/codex/deadbeef-cui/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 008</span>
      ### [Belfry]({{ '/codex/belfry/' | relative_url }})
      <p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--retired">retired → Conservatory</span></p>
    </div>
    <p class='card-desc'>A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can `ls`.</p>
    <p class='card-link-container'><a href="{{ '/codex/belfry/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 009</span>
      ### [Conservatory]({{ '/codex/conservatory/' | relative_url }})
      <p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status">active · v0.3.14</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/conservatory-library.webp' | relative_url }}" alt="Conservatory's music library: three Columns UI facet panes over genre, album artist, and album, above a rated track list and the player bar" loading="lazy">
</div>
    <p class='card-desc'>Conservatory *owns and organizes* your music, podcasts, and audiobooks on disk, presenting them through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs all three media types from one queue.</p>
    <p class='card-link-container'><a href="{{ '/codex/conservatory/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 010</span>
      ### [project-void]({{ '/codex/project-void/' | relative_url }})
      <p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> Tiled <span class="stack-sep">·</span> <span class="status status--design">design</span></p>
    </div>
    <p class='card-desc'>A design-stage CRPG and the data-driven engine that ships under it. The engineering commitment is the engine: rules expressed as universal TOML/Lua state machines, decoupled from the renderer, so the same binary could host *Cairn*, 5e, or any other system with a sheet and a turn order.</p>
    <p class='card-link-container'><a href="{{ '/codex/project-void/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 011</span>
      ### [project-yeschef]({{ '/codex/project-yeschef/' | relative_url }})
      <p class="codex-meta">Godot 4 <span class="stack-sep">·</span> Lua <span class="stack-sep">·</span> Ink <span class="stack-sep">·</span> TOML <span class="stack-sep">·</span> <span class="status status--design">design</span></p>
    </div>
    <p class='card-desc'>*YES CHEF* (working title): a single-player, character-driven grand-strategy restaurant simulation in the lineage of *Crusader Kings 3* and *Victoria 3*, pointed at the most volatile small business there is.</p>
    <p class='card-link-container'><a href="{{ '/codex/project-yeschef/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 012</span>
      ### [opends]({{ '/codex/opends/' | relative_url }})
      <p class="codex-meta">Rust <span class="stack-sep">·</span> Python <span class="stack-sep">·</span> Reverse engineering <span class="stack-sep">·</span> DOSBox <span class="stack-sep">·</span> <span class="status">active</span></p>
    </div>
    <p class='card-desc'>An open community toolkit and bugfix-patch project for SSI's *Dark Sun* CRPGs, *Shattered Lands* (1993) and *Wake of the Ravager* (1994).</p>
    <p class='card-link-container'><a href="{{ '/codex/opends/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 013</span>
      ### [kanagawa-dragon-nvim-emacs]({{ '/codex/kanagawa-dragon-nvim-emacs/' | relative_url }})
      <p class="codex-meta">Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.3</span></p>
    </div>
    <p class='card-desc'>A faithful Emacs port of the Dragon variant from [kanagawa.nvim](https://github.com/rebelot/kanagawa.nvim).</p>
    <p class='card-link-container'><a href="{{ '/codex/kanagawa-dragon-nvim-emacs/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
  <div class="codex-card" markdown="1">
    <div class="card-header">
      <span class="codex-num">No. 014</span>
      ### [Bindery]({{ '/codex/bindery/' | relative_url }})
      <p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.12.0</span></p>
    </div>
    <div class="codex-plate">
  <img src="{{ '/assets/img/bindery-sweep.webp' | relative_url }}" alt="Bindery's dry-run library sweep: per-book epubcheck results above a summary table ending in 'no files written'" loading="lazy">
</div>
    <p class='card-desc'>A command-line surgeon for malformed EPUBs. The fixes are deliberately boring: self-close the void elements, convert named entities to numeric, sync the NCX `uid` with the OPF, put the `mimetype` entry first in the zip.</p>
    <p class='card-link-container'><a href="{{ '/codex/bindery/' | relative_url }}" class="card-link">View Details &rarr;</a></p>
  </div>
