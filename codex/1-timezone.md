---
layout: codex
image: /assets/img/og-card.png
title: "1-timezone"
description: "The tiniest fix in the collection, a KOReader patch that sets a real POSIX timezone on a jailbroken Kindle."
permalink: /codex/1-timezone/
---

<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status status--complete">complete</span></p>

The tiniest fix in the collection, born from a real annoyance: on a jailbroken Kindle that boots straight into KOReader, no framework hands the process a timezone, so the base system falls back to a bogus Local Mean Time offset and every clock in the app is wrong by an odd fraction of an hour. "Synchronize time" never helps, because it corrects the instant, not the offset. This patch sets a real POSIX `TZ` inside the process and calls `tzset()` early, before the first clock read, so the footer clock, time sync, and AutoWarmth all agree again, with daylight saving flipping on its own. It ships defaulting to Eastern Time; one labelled line retargets it to any zone. AGPL-3.0, matching KOReader. One Lua file; drop it in `koreader/patches/` and keep the `1-` prefix so it runs first. The fourth of the KOReader companions, alongside Colophon, Dead Reckoning, and the Sleepscreen Banner.

<p class="codex-link"><a href="https://github.com/VirInvictus/1-timezone">github.com/VirInvictus/1-timezone →</a></p>
