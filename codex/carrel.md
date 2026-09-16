---
layout: codex
title: "Carrel"
description: "A carrel is a private desk in a library, and that is the whole design brief: no accounts, no sharing, no dashboard."
permalink: /codex/carrel/
---

<p class="codex-meta">CSS <span class="stack-sep">·</span> docs <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.9.10</span></p>

A carrel is a private desk in a library, and that is the whole design brief: no accounts, no sharing, no dashboard. One reader, seven thousand books, and an interface that gets out of the way. Built on [calibre-web](https://github.com/janeczku/calibre-web), it has since become a different program.

**There is no login.** Rather than strip out authentication and fight every future rebase, a thirty-line shim authenticates the owner on each request, so upstream's own route protections pass untouched: the 42 `@login_required_if_no_ano` decorators across ten modules need no edits, the 94 `admin.py` checks ride upstream's wrappers, and the credential routes simply answer 404. `metadata.db` is attached read-only at the connection level, so the web layer cannot write to the library even by accident.

**The search bar speaks Calibre.** Upstream has no expression grammar at all: it lowercases the term and hands it to FTS5 as a phrase, so `author:"King"` searched for that literal string and returned nothing. Carrel evaluates through **[CalibreQuarry](/codex/calibrequarry/)**'s stdlib port of Calibre's parser, and the numbers invert: 0 to 55 for that query, 0 to 1368 for `tags:Fic.Fantasy`, 0 to 244 for a custom column. Field prefixes, boolean logic, hierarchical tags and virtual-library references all behave as they do in Calibre.

**Wings** surface Calibre's virtual libraries as browse sections through that same engine, so the sidebar and a `vl:` search can never disagree. A **category browser** walks the library's dot taxonomy, synthesising the intermediate nodes because only leaves are assigned, and **Ctrl-K** fuzzy-jumps to any of 6,975 destinations, falling through to a search when what you typed is not one.

The theme stopped being a theme. caliBlur is gone and the stylesheet is owned outright: ledger hairlines instead of cards, serif for prose and mono for every label and count. One measurement shaped the statistics surfaces more than any taste decision. Kanagawa fails as a categorical chart palette, measurably: the worst adjacent accent pair sits at ΔE 6.7 for normal vision, before colour blindness is considered. So magnitude rides a single sequential ramp and identity is carried by position and a label. The constraint pushed the design further toward the ledger idiom.

<p class="codex-link"><a href="https://github.com/VirInvictus/Carrel">github.com/VirInvictus/Carrel →</a></p>
<p class="codex-link"><a href="https://github.com/VirInvictus/Carrel-calibre-web">github.com/VirInvictus/Carrel-calibre-web →</a></p>
