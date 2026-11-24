---
layout: codex
image: /assets/img/og-card.png
title: "Commonplace"
description: "A Rust/GTK4 port of the Notational Velocity line: one search field finds notes and becomes them, over a plain folder of files. No database, no cloud."
permalink: /codex/commonplace/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> comrak <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.6.1</span></p>

The Notational Velocity line is where "search becomes creation" comes from: one field, always focused, that finds the note you are looking for and, when nothing matches, becomes a new note titled with what you typed. Commonplace ports that line to Linux, with NV by Zachary Schneirov, nvALT by Brett Terpstra, and nvUltra's public surface as the behavioral targets, over a plain folder of text files: no database, no cloud, nothing to sync.

The headless engine is a zero-dependency crate carrying upstream's exact semantics: nvALT folder admission, title and filename rules, tag words plus nvUltra's boolean operators, case and diacritic folding, and incremental filtering with no inverted index by design, which keeps a 10,000-note collection answering every keystroke in microseconds (property-tested and benchmarked at that scale). Writes are atomic with upstream's rename and collision rules; the MultiMarkdown-style metadata header feeds the Title override; a folded tag store and the wiki-link graph ride along, and renaming a note rewrites the links that point at it. The render boundary (a dependency-free `Renderer` trait with a plain-text stub as the fixed test oracle) and the export core complete the engine: feature-complete, headless. comrak is pinned at the CLI where the export pipeline consumes it; the engine itself stays at zero crates.

The arcs shipped in one week. The CLI drives the whole engine with twelve verbs (`search`, `list`, `open`, `new`, `append`, `export`, `tags`, `cat`, `render`, `config`, plus `completions` and `scheme`). The GTK4 shell carries the defining UX ported 1:1: the two-pane NV layout, the sort picker with upstream's date-modified-reversed default, file watching that reconciles external edits against the store, and the search field's full state machine (title-prefix completion with the remainder selected, Return to edit the selection or create, Escape to clear, the arrow keys walking the list with the typed text kept selected, Tab completing and refocusing). Styling is [vir-gtk](/codex/vir-gtk/), the house layer, with the Kanagawa palettes following the system's dark/light setting. Three crates: the engine, the app, the cli. GPLv3, and the lineage makes that the natural license: nv went GPLv3 in 2011, the nvALT fork tree is BSD-3, and both trees are port sources.

<p class="codex-link"><a href="https://github.com/VirInvictus/Commonplace">github.com/VirInvictus/Commonplace →</a></p>
