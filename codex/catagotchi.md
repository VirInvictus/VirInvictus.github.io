---
layout: codex
title: "Catagotchi"
codex_num: "No. 026"
description: "A cozy cat tamagotchi wrapped around a Cookie-Clicker-scale idle empire, and the largest thing here that is not a desktop app."
permalink: /codex/catagotchi/
---

<p class="codex-meta">Godot 4.6 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v4.5.1</span></p>

A cozy cat tamagotchi wrapped around a Cookie-Clicker-scale idle empire, and the largest thing here that is not a desktop app. The two halves are welded together rather than stacked: five needs average into a *mood multiplier* running ×0.5 to ×2.0 that scales **all** gold income, so a neglected cat is not a guilt mechanic, it is a halved economy. Above that sit eight generators with endless ×2 and ×5 upgrade ladders, three skill trees, fourteen adventures, five story dungeons plus an infinite Endless Depths on seeded floor modifiers, a globally deterministic commodity exchange, and two layers of prestige. Six daily puzzle games (sudoku, crossword, jigsaw, memory, rhythm, and a hidden-object mode) rotate on a four-hour seed that is the same for every player, so a daily is a shared board rather than a private roll.

The engineering constraint is the interesting one: **everything on screen is generated in code.** Art, music, sound effects, and the procedurally painted story vignettes are all drawn or synthesized at runtime, and there are no asset files in the repo beyond a single icon. It targets the GL Compatibility renderer for the same reason, so the whole thing runs on an old integrated GPU. Verification is headless, because a tamagotchi is a bad thing to test by hand: a `CATAGOTCHI_SMOKE` suite runs the systems without a window, a `CATAGOTCHI_DRIVE` script runner drives the real UI from a text file and screenshots every screen it visits, and saves carry forward-compatible migrations so a save from an earlier phase still opens. Currently mid-way through two overlapping overhauls, a graphical pass and a gameplay pass aimed at a Steam-viable build.

<p class="codex-link">private, in development</p>
