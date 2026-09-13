---
layout: codex
title: "Framework"
codex_num: "No. 005"
description: "A native Linux document viewer for PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, TXT"
permalink: /codex/framework/
---

<p class="codex-meta">C <span class="stack-sep">·</span> Meson <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> MuPDF <span class="stack-sep">·</span> DjVuLibre <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.0.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/framework-viewer.webp' | relative_url }}" alt="Framework rendering a 168-page PDF with the table-of-contents sidebar open and two pages visible in the scroll" loading="lazy">
</div>

A native Linux document viewer for **PDF, DjVu, CBZ, CB7, CBT, CBR, XPS, EPUB, FB2, MOBI, AZW3, TXT, and Markdown**: the gap between feature-heavy clients (Okular) and bare MuPDF wrappers, a SumatraPDF-shaped experience for Linux. A three-tier cache (persistent thumbnails, parsed page handles, rendered Cairo surfaces) with bytes-aware eviction, parallel rendering across eight independent MuPDF instances, and a zero-copy MuPDF→Cairo pipeline that builds the pixmap *around* the Cairo surface buffer.

A *velocity engine* throttles render dispatch by scroll speed so fast-scrolling never queues stale work, a thread-pool sort keeps the viewport ahead of the queue, and mid-render `fz_cookie` abort lets workers bail in milliseconds. Manga (RTL), Webtoon, and facing-pages comic layouts, all live-toggleable, with aspect-ratio and filename-based double-spread detection for scanlation rips. Async progressive search over cached structured text (332 ms cold → 48 ms warm on a 901-page textbook), reading-order-aware text selection, a magnifying loupe (F7), and `GFileMonitor` auto-reload that refreshes a recompiled LaTeX or Typst doc with scroll position preserved.

The ebook formats reflow natively through an embedded WebKitGTK view: each backend parses its format (an OPF spine walker for EPUB, a MOBI / KF7 / KF8 / AZW3 parser with HuffDic decompression ported from foliate-js, vendored md4c for Markdown) and emits one stitched HTML document, with images served over an internal `framework-img://` scheme and typography and reading themes pushed in live as CSS custom properties. EPUBs and AZW3 keep their publisher stylesheets and embedded fonts (KF8's CSS flows served through the same `framework-img://` scheme), a dark reading theme transforms those publisher colours in HSL so a book's own light callout never glares, internal links and TOC navigation work across all the reflow formats, and the HTML is scrubbed of scripts and active content before it ever reaches the view, which itself cannot touch the network. A process-scoped Linux **Landlock LSM** sandbox drops filesystem `EXECUTE` and `MAKE_*` rights at startup, so a malicious document exploiting MuPDF / DjVuLibre / libarchive into RCE cannot escalate to a shell. The v0.80.0 pass took it tiling-first: libadwaita is gone in favour of plain GTK4 under an owned Kanagawa Dragon stylesheet that follows the system dark/light preference through the desktop portal, with a floating table-of-contents overlay and hidden window chrome. Strictly a viewer: no annotations, no library, no conversion. Every borrowed pattern (SumatraPDF, zathura, Sioyek, YACReader, Foliate, MComix, Komikku, Plato) is attributed in the README with upstream `file:line`. A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Framework">github.com/VirInvictus/Framework →</a></p>
