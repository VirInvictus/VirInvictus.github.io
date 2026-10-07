---
layout: codex
image: /assets/img/og-card.png
title: "Quire"
description: "A Soulver-style notepad calculator for Linux: prose and math share one plain-text sheet, and every expression answers on its own line in a results column."
permalink: /codex/quire/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">active · v0.5.1</span></p>

A Soulver-style notepad calculator for Linux: prose and math share one plain-text sheet, and every expression answers on its own line in a results column down the right edge. The sheet is the file. There is no project format underneath and nothing to save; the thing on screen is the thing on disk.

The evaluator is written for the way people actually scribble. Variables and bare references (`groceries` on its own line answers with its value), percentage forms that match how they are spoken (`200 + 15%` is 230, `15% of 200` is 30), mixed lines where the words strip away and the math is left (`50 apples at 3 each` is 150), functions with literal-pattern clauses and recursion (`fact(0) = 1`, `fact(n) = n * fact(n - 1)`), line references (`&N` answers with line N's result), and tags that group lines into sheet-wide views. Units ride an embedded [numbat](https://numbat.dev/) engine with dimension checks (`5 kg + 300 g`), and currency runs on an ECB reference-rate snapshot cached under `~/.cache/quire`, so conversions work offline forever after the first fetch. An error belongs to its line: the exact token that failed underlines in place, and no other line ever breaks.

Two crates: `quire-eval`, the UI-free engine, behind `quire`, a plain GTK4 app with no libadwaita, styled by vir-gtk like the rest of the collection.

<p class="codex-link"><a href="https://github.com/VirInvictus/Quire">github.com/VirInvictus/Quire →</a></p>
