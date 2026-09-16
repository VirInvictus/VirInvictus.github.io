---
layout: codex
image: /assets/img/og-card.png
title: "Topograph"
description: "A native Qt6/QML file system size explorer: fast, local-first, and styled with Kanagawa Dragon."
permalink: /codex/topograph/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> Qt6/QML <span class="stack-sep">·</span> CXX-Qt <span class="stack-sep">·</span> <span class="status">active · v0.3.2</span></p>

Where did the disk go? Topograph answers that the way a native app should: point it at a directory, hit Scan, and read the tree. The scanner core (`topograph-core`) is pure Rust with no Qt dependency, so the walk is fast and headless-scriptable; only the GUI shell links Qt6, through CXX-Qt. Directories expand and collapse on click, so only the levels you open are ever materialized, the header sorts any level by size, name, or file count, and every row draws its share of the parent's size as an inline bar. The tree is keyboard navigable: arrows move, collapse, and expand, and the selection follows the row through expanding, collapsing, and re-sorting.

Honest about its scope: the qdirstat-style treemap visualization is planned, not built. What ships today is the listing surface, and it is deliberately conservative with memory: a scan builds the tree it needs and nothing more. Styled with the house Kanagawa Dragon palette.

<p class="codex-link"><a href="https://github.com/VirInvictus/Topograph">github.com/VirInvictus/Topograph →</a></p>
