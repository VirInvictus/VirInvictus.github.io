---
layout: codex
title: "Hearth"
codex_num: "No. 017"
description: "A native, two-player, local-network, fully offline digital build of a worker-placement and polyomino-economy Eurogame"
permalink: /codex/hearth/
---

<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v0.13.56</span></p>

A native, two-player, local-network, fully offline digital build of a worker-placement and polyomino-economy Eurogame, riding on a content-agnostic engine built to outlive any one theme. The board, the goods, and the cards are data; the engine keeps a pure `State` / `Rules` / `Scoring` / `Loader` split so the same binary could host a different game with a sheet and a turn order. The distinctive subsystems are the home-board polyomino puzzle and a pure effect vocabulary the cards reuse: every action is a non-mutating transform over game state, which keeps the rules testable away from the renderer.

Hot-seat is the development default; the authoritative-host LAN layer lands late, once the economy and the full score are settled. The faithful ruleset is transcribed from the physical book, git-ignored, and never committed; the asset meant to ship is the engine plus an original-theme dataset, a deliberate post-1.0 extraction. Sibling in shape to Haveli.

<p class="codex-link">private, in development</p>
