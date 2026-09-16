---
layout: codex
title: "AudiobookTools"
description: "One catalogue file is the source of truth for an entire audiobook shelf: retag writes the embedded metadata from it"
permalink: /codex/audiobooktools/
---

<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> <span class="status">active · v0.3.0</span></p>

One catalogue file is the source of truth for an entire audiobook shelf: `retag` writes the embedded metadata from it, `reorg` renders the on-disk folder tree from it, and the files and the shelf cannot drift apart because both are projections of the same data. The engine is generic and the catalogue is data; the two never mix.

The operational contract does the heavy lifting. Dry-run is the default for everything; every `--apply` writes a manifest that fully reverses it; a second dry-run after an apply must report zero changes. The tests enforce all three properties, which is what lets a bulk retag of irreplaceable audio feel routine instead of reckless.

<p class="codex-link"><a href="https://github.com/VirInvictus/AudiobookTools">github.com/VirInvictus/AudiobookTools →</a></p>
