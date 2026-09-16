---
layout: codex
title: "Viaduct"
codex_num: "No. 002"
description: "A Linux port of Brent Simmons' NetNewsWire RSS reader. A Cargo workspace split between a headless viaduct-core (database, network, parser"
permalink: /codex/viaduct/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> WebKit <span class="stack-sep">·</span> <span class="status">active · v4.0.2</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/viaduct-main.webp' | relative_url }}" alt="Viaduct's three-pane layout: feed sidebar with unread counts, article timeline, and the reading pane on the v3.0 flat Kanagawa design" loading="lazy">
</div>

A Linux port of Brent Simmons' [NetNewsWire](https://netnewswire.com/) RSS reader. A Cargo workspace split between a headless `viaduct-core` (database, network, parser, models) and a `viaduct` GTK binary, making the architectural boundary a *compile error* rather than a code-review rule. Idles at **100–300 MB** against ~600 MB for the closest Linux competitor on the same OPML, with a hard **500 MB** ceiling enforced by an in-tree `mem_check` harness.

Single-writer SQLite worker on tokio across three WAL databases (articles, feed settings, sync). OPML on disk as the source of truth, byte-for-byte compatible with NetNewsWire; NetNewsWire-faithful parsing of RSS 2.0, RDF, Atom, JSON Feed, and RSS-in-JSON. Local and Inoreader accounts, the latter a port of NetNewsWire's ReaderAPI sync engine. The article pane is exactly one neutered WebKit instance: JS, WebGL, WebRTC, DevTools, and LocalStorage off, strict CSP, every image routed through a custom `viaduct-img://` scheme so the WebView never reaches the open internet.

The v2.x line built an original surface on top of the port: **Custom Smart Feeds** (rule-driven saved searches parsed via **[vir-search](/codex/vir-search/)**), an Activity Log over a ring buffer, a Send-to menu, Reader View, OPML import/export, and a width-driven adaptive layout. A background-daemon mode runs Viaduct as an XDG autostart agent and re-summons the window over D-Bus. A Flatpak manifest ships alongside the native build. **v3.0.0 dropped libadwaita entirely** for a viaduct-owned design layer powered by **[vir-gtk](/codex/vir-gtk/)**, a flat Kanagawa palette on plain GTK4, so it belongs equally on GNOME, Hyprland, or any Wayland desktop rather than reading as a GNOME app; the eight NetNewsWire reading-pane themes are unchanged. Removing a whole shared library also lowered memory, a full refresh now peaks around 300 MB.

<p class="codex-link"><a href="https://github.com/VirInvictus/Viaduct">github.com/VirInvictus/Viaduct →</a></p>
