---
layout: codex
image: /assets/img/og-card.png
title: "Hearthfall"
description: "A grimdark clan-survival game for the terminal: turn-based, season-timed, and fog-black."
permalink: /codex/hearthfall/
---

<p class="codex-meta">Python 3.14+ <span class="stack-sep">·</span> Textual <span class="stack-sep">·</span> <span class="status">active · v0.28.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/hearthfall-run.webp' | relative_url }}" alt="Hearthfall mid-run: the clan panel and fog-black map at left, the season log at right, and a story event offering two choices" loading="lazy">
</div>

A grimdark clan-survival game for the terminal: turn-based, season-timed, and fog-black. You start with a handful of villagers and a map you cannot see, send people out, and the world arrives tile by tile through scarcity, story, and violence. *A Dark Room* that grows a spine into *King of Dragon Pass*, rendered in glyphs. The design bet is that exploration and combat are the same loop rather than two: scouts reveal terrain **and** enemy composition, so a scout returning with *forty of them, mostly spears, no archers, holding the high ground* is worth more than a sword, and the game lives in assembling the counter-force rather than in the swing.

Time is seasonal, four turns to a year, and each season splits a finite clan between foraging (which returns nothing at all in winter, because there is nothing out there to find), exploring, and tending the store against a rot that can be slowed and never stopped. Children eat and cannot work; everyone eats regardless.

Three constraints are enforced by tests rather than by intention. `engine/` is stdlib-only pure logic with no I/O and no rendering that imports nothing from the frontend and nothing from PyPI, so a full game runs from a Python REPL with no terminal at all and the Textual skin is shed-able. Every random draw goes through one seeded, injectable RNG, so `--seed 42` replays a run exactly. And event effects are structured TOML tables (`food = -5`) rather than expression strings, so content can never smuggle in code. v0.1.1 added the season ledger: `turn.forecast` projects the food arithmetic for a set of orders while mutating nothing, and it deliberately stops at spoilage, because everything later in the tick consumes the RNG and a forecast that guessed at those would be lying about the one thing a forecast is for. Since that ledger, the violence arrived: sub-project 6 built the combat arc through v0.18.0, from single-draw battle resolution through raiders at the gates, with raid stakes paid in people. The skin is forbidden from computing numbers; if a number is on screen, the engine produced it.

<p class="codex-link"><a href="https://github.com/VirInvictus/Hearthfall">github.com/VirInvictus/Hearthfall →</a></p>
