---
layout: codex
image: /assets/img/og-card.png
title: "hex"
description: "A Discworld MUD plugin suite for Blightmud: GMCP vitals, Quow database searches, and room awareness, with the semantics ported from tt_dw."
permalink: /codex/hex/
---

<p class="codex-meta">Lua 5.4 <span class="stack-sep">·</span> stdlib Python <span class="stack-sep">·</span> <span class="status">active · pre-release</span></p>

Discworld MUD has twenty-five years of player tooling, and nearly all of it orbits two artifacts: Quow's database, the community's index of seventeen thousand rooms and ten thousand items, and tt_dw, the TinTin++ suite that carries that data to the terminal. Blightmud, the Rust terminal client, had neither. Hex is the port: it was the first Discworld plugin suite the client ever had, because when I checked in November 2026 there was nothing there at all.

So the semantics are borrowed and the code is new. The Quow query builder reproduces tt_dw's SQL down to the article-insensitive ordering; the gag set starts from tt_dw's pet-and-summon spam filters; the XP-rate model and the HP bar color bands are tt_dw's thresholds. Onto that goes what only Blightmud can do cheaply: GMCP vitals decoded from raw JSON into a three-row status area, the MUD's own ASCII room maps, and room awareness keyed on the forty-character room identifier the server sends, which turns out to be the same identifier in Quow's tables and in tt_dw's map file. A stdlib Python converter turns tt_dw's 62,130-room map into a SQLite database keyed by that identifier, so one room number means the same thing everywhere.

It is named for the computer in Unseen University, and it obeys the same rule the game does: Hex renders, looks up, and tracks; it never sends a thing to the MUD that the player did not ask for.

<p class="codex-link"><a href="https://github.com/VirInvictus/hex">github.com/VirInvictus/hex &rarr;</a></p>
