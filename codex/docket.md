---
layout: codex
image: /assets/img/og-card.png
title: "Docket"
description: "Plain-text task lists for Linux: a native GTK4 editor, clean-room faithful to the TaskPaper format."
permalink: /codex/docket/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> GtkSourceView <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v1.0.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/docket-dark.png' | relative_url }}" alt="Docket's start page: a working checklist, live searches, tags, and the sidebar" loading="lazy">
</div>

Plain-text task lists for Linux. Docket is a native GTK4 editor for the TaskPaper format: projects end with a colon, tasks start with a dash, notes are everything else, and `@tags` mark things up. Your files stay plain text that any editor can open; Docket makes them look, fold, and filter like an outliner without ever taking the text away from you. It sits beside [Atrium](/codex/atrium/) on purpose: an editor, never a task system.

The build is clean-room. The TaskPaper format is public, so the discipline is facts-only references: the author's published User's Guide (via Wayback snapshots) is the normative source for the format, the author's MIT-licensed birch-outline and aequery libraries are the semantics tier, and the restricted clones were mined for behavior facts only, never code, with no trademark use and a non-affiliation note in the README.

The engine is a [Quire](/codex/quire/)-pattern two-crate workspace: `docket-core`, GUI-free and dependency-free, holds the format engine (the complete document model with the reference's classification rules, the tag engine's boundary and escaping rules, and a lossless idempotent writer proven over a fixture corpus), the query language (comparison operators, a mini regex, seeded searches), the full date grammar (ISO fallback, TZif, `run_at`), and all eleven item-path axes with `run_scoped_at` focus anchoring. The `docket` app carries the GtkSourceView surface: autosave and external reload, syntax highlighting, a welcome buffer, recents, outline folding with the fold state persisted to a content-hash-keyed sidecar, tag completion, Archive Done, and a sidebar of projects, saved searches, and tags.

The v1.0.0 milestone is the outline: the fold command cluster (Expand and Collapse with their Completely variants and All By Level, the digit chords keyed to the hardware key so they survive Shift), item-only branch moves, Delete Items with hidden-descendant semantics, Select Branch, and Format As with the reference's text transformations. A Flatpak manifest targeting the GNOME 50 runtime ships in the repo. Post-1.0 candidates (command palette, stylesheets, a CLI) are sequenced in the roadmap.

<p class="codex-link"><a href="https://github.com/VirInvictus/Docket">github.com/VirInvictus/Docket →</a></p>
