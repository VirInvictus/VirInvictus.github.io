---
layout: codex
title: "Foyer"
codex_num: "No. 029"
description: "The shared front door to Hearth (No. 017) and Haveli (No. 018): a small launcher and networked LAN lobby."
permalink: /codex/foyer/
---

<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> ENet <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.0</span></p>

The shared front door to Hearth (No. 017) and Haveli (No. 018): a small launcher and networked LAN lobby. Pick a game, find the other player on the network, agree the setup, lock in, and Foyer relaunches each side with the right arguments and steps out of the way.

What it is *not* is the design. It is not an engine and holds no game rules: each game keeps its own engine, its own ENet transport, and its own hidden-information handling, and Foyer coordinates only the choice and the handshake. That boundary buys something concrete. Hearth and Haveli are private because they carry a faithful transcription of a copyrighted board game; Foyer carries none of it, so it is original code that can stand on its own. It also keeps the registry of games it knows about (tracked) separate from where they live on your disk (untracked), so a checkout stays portable and nobody's home directory ends up in the repository. Phase 1 ships the launcher, which lists its games, greys out the ones it cannot locate, and starts either one locally; the networked half is Phase 2, and until then each game keeps its own in-app lobby.

<p class="codex-link">in development</p>
