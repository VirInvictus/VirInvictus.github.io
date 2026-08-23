---
layout: codex
title: "Conservatory"
codex_num: "No. 009"
description: "Conservatory owns and organizes your music, podcasts, and audiobooks on disk"
permalink: /codex/conservatory/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status">active · v0.3.12</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/conservatory-library.webp' | relative_url }}" alt="Conservatory's music library: three Columns UI facet panes over genre, album artist, and album, above a rated track list and the player bar" loading="lazy">
</div>

Conservatory *owns and organizes* your music, podcasts, and audiobooks on disk, presenting them through a foobar2000 Columns UI browse surface and played through a libmpv daily-driver engine that runs all three media types from one queue. Designed as **Calibre for audio**.

It absorbed the Belfry podcast client (No. 008), converging that engine and triage model with a massive faceted music browser. The database is truth; the on-disk tree is a rendered template; moving an album re-renders the filesystem. A Calibre-shaped search expression language powered by **[vir-search](/codex/vir-search/)**, multi-select bulk actions, and embedded-tag write-back so files stay portable. The headless manager imports, resolves, and crash-safely moves files with a full undo journal and roll-forward recovery; the GTK app stands up the deadbeef Columns UI faceted browse (configurable columns and facet panes), a sortable track list, saved Perspectives, the unified play queue with drag-reorder, shuffle and repeat, and a libmpv player carrying ReplayGain, a 10-band graphic EQ, a DSP rack (compressor, limiter, leveler), a real-time spectrum visualizer, a Now-bar transport, and a Preferences window over a real config file. All three media types are in: music, podcasts, and audiobooks browse and play from the one queue, and it holds up as a daily driver, down to gapless album transitions (the next track is prefetched across mpv's decoder boundary so the seam never reaches the speakers). A CLI health suite audits integrity, duplicates, tags, and cover art, strips stray APE tags, and imports and exports `.m3u`. Built concurrently with Atrium under hard phasing; Belfry was retired at podcast parity (v0.0.52) and its subsystem now lives here whole. The v0.3.x line took the app tiling-first (libadwaita is gone; the same feature set runs on plain GTK4 under a flat Kanagawa Dragon stylesheet provided by **[vir-gtk](/codex/vir-gtk/)**), turned the seek slider into the track's real loudness-envelope waveform, and grew a full scrobbler: Last.fm and ListenBrainz, now-playing included, through an offline-safe outbox, off by default.

<p class="codex-link"><a href="https://github.com/VirInvictus/Conservatory">github.com/VirInvictus/Conservatory →</a></p>
