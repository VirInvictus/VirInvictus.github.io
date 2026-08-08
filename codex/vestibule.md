---
layout: codex
title: "Vestibule"
codex_num: "No. 028"
description: "A one-directional converter that turns an Obsidian vault into org-mode files org-roam can index, then installs them into a live Doom setup."
permalink: /codex/vestibule/
---

<p class="codex-meta">Ruby <span class="stack-sep">·</span> pandoc <span class="stack-sep">·</span> Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.0</span></p>

A one-directional converter that turns an Obsidian vault into org-mode files org-roam can index, then installs them into a live Doom setup. Not a sync tool, and that is not a future phase. Half experiment, half write-up: *can you move an Obsidian vault into org-roam* gets asked often and answered in the abstract, usually stopping at "the links and frontmatter are easy, Dataview is impossible."

That answer is right about the first part and too pessimistic about the second, and the measurement is the point of the project. The vault it was designed against has **326 Dataview blocks**, which sounds disqualifying until you count distinct queries instead of instances: 85 are `LIST FROM [[]]`, which is org-roam's native backlinks buffer and gets deleted outright; roughly 200 are one templated `dataviewjs` block that a single org dynamic block replaces; about ten are real queries worth hand-porting. The most common Dataview query in the vault turned out to be a feature org-roam already ships for free. The replacement query layer runs on `org-roam.db`, the SQLite index org-roam maintains anyway, so nothing new gets installed; Dataview has to build that index itself.

Everything structural is hand-rolled (frontmatter to property drawers, wikilinks to `id:` links, nested tags to generated tag-group declarations) and only body markup goes through pandoc, behind a mask-convert-unmask cycle so pandoc never sees the constructs it would mangle. Two passes are mandatory because forward references exist: a note dated January can link to one written in June. `convert` and `install` are deliberately never one command; `convert` writes only inside the repo, and `install` is dry-run by default and tars the target first, because `~/org` is deliberately outside version control for privacy and that snapshot is the only undo. The index layer is built and tested; the converter body is the current work.

<p class="codex-link">private, in development</p>
