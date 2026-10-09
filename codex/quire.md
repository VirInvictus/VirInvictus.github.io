---
layout: codex
image: /assets/img/og-card.png
title: "Quire"
description: "A Soulver-style notepad calculator for Linux: prose and math share one plain-text sheet, and every expression answers on its own line in a results column."
permalink: /codex/quire/
---

<div class="codex-plate">
  <img src="{{ '/assets/img/quire-welcome.webp' | relative_url }}" alt="Quire's welcome sheet: the tour with live answers in a right-hand column" loading="lazy">
</div>

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> <span class="status">shipping · v1.5.2</span></p>

A Soulver-style notepad calculator for Linux: prose and math share one plain-text sheet, and every expression answers on its own line in a results column down the right edge. The sheet is the file. There is no project format underneath and nothing to save; the thing on screen is the thing on disk.

The evaluator is written for the way people actually scribble. Variables and bare references (`groceries` on its own line answers with its value), percentage forms that match how they are spoken (`200 + 15%` is 230, `15% of 200` is 30) including the reverse questions (`220 is 10% on what`), mixed lines where the words strip away and the math is left (`50 apples at 3 each` is 150) — and since 1.2, sentences with quantities answer too (`the stock solution measures 2 mol/L` answers `2 molar`). Functions compose with recursion and literal-pattern clauses (`fact(0) = 1`, `fact(n) = n * fact(n - 1)`), and line references resolve in *both directions*: a summary line at the top of a sheet can cite the derivation at the bottom, and the sheet re-evaluates until every reference settles. Tags group lines into sheet-wide views, checkboxes tick with Ctrl+click, and the caret's line carries a subtle band. Units ride an embedded [numbat](https://numbat.dev/) engine with dimension checks (`5 kg + 300 g`), and currency runs on an ECB reference-rate snapshot cached under `~/.cache/quire`, so conversions work offline forever after the first fetch. An error belongs to its line: the exact token that failed underlines in place, and no other line ever breaks.

The menu ships worked templates — a mortgage walkthrough whose summary cites its own derivation, a freelance invoice with discount and VAT, a budget with variance, a portfolio, a trip planner, a scientist's lab notebook — and `quire-cli` turns any sheet into its answers column as text or JSON for terminals and agents.

Two crates: `quire-eval`, the UI-free engine, behind `quire`, a plain GTK4 app with no libadwaita, styled by vir-gtk like the rest of the collection.

<p class="codex-link"><a href="https://github.com/VirInvictus/Quire">github.com/VirInvictus/Quire →</a></p>
