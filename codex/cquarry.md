---
layout: codex
title: "cquarry"
codex_num: "No. 029"
description: "A lightweight, canonical Python package providing read-only access to Calibre's metadata.db and a full parser for Calibre's native search expression grammar."
permalink: /codex/cquarry/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v1.20.0</span></p>

A lightweight, canonical Python package providing read-only access to Calibre's `metadata.db` and a full parser for Calibre's search expression grammar.

This library powers **[CalibreQuarry](/codex/calibrequarry/)** (CLI/TUI), **[Hermitage](/codex/hermitage/)** (GTK4 Desktop Gallery), **[bindery-cli](/codex/bindery/)** (EPUB repair tool), and [Carrel-calibre-web](https://github.com/VirInvictus/Carrel-calibre-web) (Web Reader) within the ecosystem, ensuring that Virtual Library definitions and search queries evaluate identically across all frontends.

It implements a recursive-descent parser that perfectly matches Calibre's native search capabilities (exact matches, substring, boolean logic, date math, custom columns, identifiers, and nested virtual libraries), bypassing Calibre's heavy Python initialization overhead.

<p class="codex-link"><a href="https://github.com/VirInvictus/cquarry">github.com/VirInvictus/cquarry →</a></p>
