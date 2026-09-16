---
layout: codex
image: /assets/img/og-card.png
title: "Haveli"
description: "Two players, one LAN, no internet at any point: a digital build of a fast set-collection card game on a content-agnostic, deterministic engine."
permalink: /codex/haveli/
---

<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.2.0</span></p>

Two players, one LAN, no internet at any point: a digital build of a fast set-collection card game on a content-agnostic, deterministic engine. Sibling in shape to Hearth, but where Hearth's puzzle is the board, Haveli's is hidden information and reproducible randomness. It is a shuffled-deck game, so determinism is foundational: an `rng_seed` plus a draw cursor make every shuffle and every market refill replayable from the state alone, which is what lets the network layer stay honest.

Hidden hands force a host-authoritative, per-seat-**redacted** model: the host owns the truth, validates every move, and pushes each peer only the view its seat is allowed to see. There is no move relay, because relaying moves would leak the deck order. The client never applies a move itself, which makes desync structurally impossible rather than merely unlikely. The engine keeps the same `State` / `Rules` / `Scoring` / `Loader` split, with moves as serializable dictionaries; the ENet transport is in and verified live across two machines, disconnect and reconnect included.

It reached **1.0.0 on 2026-08-08**, the repo's first tag, and the milestone is explicitly *the engine*: rules-complete, verified end to end across sixteen headless suites including a rules-to-engine fidelity matrix, a full setup-to-final-seal match, and a 24-seed determinism batch. The dataset was checked against the rulebook with zero discrepancies and the token values read off the physical components. The interface that ships with it is deliberately functional rather than final, accessible colour chips and glyphs and one button per legal move; a real graphics and presentation pass is the road to 2.0. The faithful dataset stays git-ignored and never committed, so the repo stays private; the publishable asset is the engine plus an original-theme dataset, a deliberate post-1.0 extraction.

<p class="codex-link">private, shipped v1.2.0</p>
