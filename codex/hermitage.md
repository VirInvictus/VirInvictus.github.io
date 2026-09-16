---
layout: codex
title: "Hermitage"
description: "Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way."
permalink: /codex/hermitage/
---

<p class="codex-meta">Python 3.13+ <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.8.5</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/hermitage-gallery.webp' | relative_url }}" alt="Hermitage's cover-art grid filtered to a virtual library, with the Wing sidebar open and the search bar showing the active expression" loading="lazy">
</div>

Built for the single user who wants a modern desktop experience over a Calibre library without Docker or a web auth layer in the way. Reads `metadata.db` in `mode=ro` and turns a 4,000+ item library into a cinematic gallery: an edge-to-edge cover grid with median-cut colour quantization for per-book accent tinting, a sliding hero-banner detail sidebar (the *Codex*), and a recursive genre browser that unfolds dot-separated Calibre tags (`Fic.Fantasy.Grimdark`) into a navigable tree.

Native support for Virtual Libraries and the full Calibre search-query language (`Ctrl+F`), powered by **[cquarry](/codex/cquarry/)** (the shared engine behind **[CalibreQuarry](/codex/calibrequarry/)** and **[bindery-cli](/codex/bindery/)**), with a 512-entry texture LRU and three-tier colour cache to keep scrolling smooth on integrated graphics. Ships `hermitage-verify`, a standalone CLI that audits integrity, cover presence, and format resolution; the v0.16.0 audit sweep added the project's first in-tree test suite and lint hygiene behind it. The v0.17.0 pass took it tiling-first: libadwaita is gone in favour of plain GTK4 under an owned Kanagawa Dragon stylesheet that follows the system dark/light preference through the desktop portal, with floating overlay sidebars, grid type-ahead, and per-scale HiDPI thumbnails. Zero telemetry, zero network calls, zero accounts. A Flatpak ships alongside the native build: 8 MB, sandboxed, with arbitrary library paths reached through the file-chooser portal. The 1.x line graduated the app to a stable v1.0.0 in August 2026, packaged for PyPI alongside the Flatpak, after a regression gauntlet against a live 7,600-book library; the releases since have ridden cquarry's growth: page counts in the Codex, user categories resolved natively through the search grammar, and a v1.8 performance tier that stopped bulk-fetching every book's comments at startup.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hermitage">github.com/VirInvictus/Hermitage →</a></p>
