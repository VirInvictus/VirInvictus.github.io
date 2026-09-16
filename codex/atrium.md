---
layout: codex
title: "Atrium"
codex_num: "No. 001"
description: "The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise."
permalink: /codex/atrium/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> tokio <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v0.76.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/atrium-today.webp' | relative_url }}" alt="Atrium's Today view: six canonical lists in the sidebar, coloured tag pills, and the Area › Project chip on each row" loading="lazy">
</div>

The native Linux task manager you grow into, not out of. An Org-mode app wearing a Things 3 / OmniFocus disguise: UUIDs on every node, plain-text round-trip, deadlines and schedules and contexts as first-class data, in a fast GTK4 surface styled by **[vir-gtk](/codex/vir-gtk/)** that never asks you to open Emacs. **Simple Mode** for *what am I doing right now* (six canonical lists, no defer dates, Things 3 calm); **Builder Mode** for the days the system has to do the work (Forecast, Agenda, Kanban, Calendar, Review with per-area cadences that cascade to the projects filed under an area, Perspectives, repeating and sequential projects, blocked-by task dependencies, time-based system reminders, a live Inspector). Same data, two surfaces, no migration: flipping modes is a UI re-render over an OmniFocus-superset schema that was there on day one.

Local-first SQLite in WAL mode, single-writer worker, read-only connection pool. FTS5 search through a **Calibre-style expression grammar** (`tag:work AND is:overdue sort:-due`, `due:2026-05-01..2026-05-31`, `tag:?wrok` for fuzzy match) powered by **[vir-search](/codex/vir-search/)**. A six-crate workspace; the extracted `atrium-inline` engine (`#tag`, `@today`, `!priority` with tab-completion) and the `atrium-org` round-trip layer are both tested headlessly, away from the UI. A thousand-test suite and 21 migrations, with a 1K-fixture smoke and cold-start check gating every push. Org is the two-way mirror, and importers bring the rest across: Todoist CSV, Taskwarrior `task export` JSON, todo.txt, and iCalendar VTODO (import and export). A Flatpak manifest ships alongside the native build.

<p class="codex-link"><a href="https://github.com/VirInvictus/Atrium">github.com/VirInvictus/Atrium →</a></p>
