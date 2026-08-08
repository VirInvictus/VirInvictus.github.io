---
layout: codex
title: "Kobo-style Sleepscreen Banner"
codex_num: "No. 021"
description: "A KOReader user patch that redraws the stock sleep screen as a Kobo-lockscreen-style floating card over your book cover: a serif title, a stats line"
permalink: /codex/kobo-style-sleepscreen-banner/
---

<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

A KOReader user patch that redraws the stock sleep screen as a Kobo-lockscreen-style floating card over your book cover: a serif title, a stats line, and a random highlight pulled from the last book you were reading, set as an italic pull-quote with an accent rule and a "saved on..." footer. The card carries a real visual identity, rounded corners over a hard offset drop shadow so it reads as a tag sitting above the cover, with per-element font control wired for the [ebook-fonts](https://github.com/nicoverbruggen/ebook-fonts) collection out of the box. It draws once on suspend, so there is no E Ink refresh cost while you read. Honest about its lineage: a prettified fork of zenixlabs' community patch (which designed the Kobo banner and the random-highlight feature), credited in the source header and README; this fork contributes the floating-card design and the font wiring. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `2-` prefix so it loads after KOReader's widget system. The third of the KOReader companions, alongside Colophon and Dead Reckoning.

<p class="codex-link"><a href="https://github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified">github.com/VirInvictus/2-kobo-style-sleepscreen-banner-prettified →</a></p>
