---
layout: codex
title: "deadbeef-cui"
codex_num: "No. 007"
description: "A faceted-browser plugin for the DeaDBeeF music player, bringing foobar2000-style Columns UI / Facets to Linux."
permalink: /codex/deadbeef-cui/
---

<p class="codex-meta">C <span class="stack-sep">·</span> GTK3 <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.3.3</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/deadbeef-cui-facets.webp' | relative_url }}" alt="deadbeef-cui's three facet columns narrowing genre, album artist, and album above the playlist, with cover art and a waveform seekbar" loading="lazy">
</div>

A faceted-browser plugin for the [DeaDBeeF](https://deadbeef.sourceforge.io/) music player, bringing foobar2000-style Columns UI / Facets to Linux. 1–5 dynamic filter columns with hierarchical narrowing, full title-formatting support, multi-select aggregation across genres and artists via Ctrl/Shift-click, an in-pane search bar (`Ctrl+Shift+F`), and a settings dialog with per-instance configuration so multiple Facet Browsers can coexist in one layout.

The standard DeaDBeeF track context menu is wired in (Play Next / Play Later / Properties / Convert / Reload metadata alongside the facet-specific items), tracks drag out of facet rows onto playlist tabs via the same `DDB_PLAYITEM_POINTERLIST` payload the GTKUI medialib widget uses, and "Send to new playlist `<row name>`" names the destination after the right-clicked tag. Everything targets a dedicated "Library Viewer" playlist so the plugin never touches curated playlists. Built natively against `DB_mediasource_t`, with an in-tree GTest suite driving the real engine against a mocked DeaDBeeF API, clean under ASan/UBSan. Complete; fixes only from here.

<p class="codex-link"><a href="https://github.com/VirInvictus/deadbeef-cui">github.com/VirInvictus/deadbeef-cui →</a></p>
