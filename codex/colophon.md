---
layout: codex
title: "Colophon"
codex_num: "No. 019"
description: "A native Linux statistics viewer for KOReader. KOReader tracks a surprising amount about how you read (per-page timing, session history, running totals)"
permalink: /codex/colophon/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> Cairo <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--shipping">shipping · v2.6.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/colophon-per-book.webp' | relative_url }}" alt="Colophon's per-book view: a reading-stats table above the pace-through-the-book and reading-speed charts, all drawn in Cairo" loading="lazy">
</div>

A native Linux statistics viewer for [KOReader](https://koreader.rocks/). KOReader tracks a surprising amount about how you read (per-page timing, session history, running totals), and every existing way to look at that data is a web dashboard or a self-hosted Docker service. Colophon is neither: a local desktop app that imports a *copy* of `statistics.sqlite3` (staged, validated, never opened in place) and turns it into the analytics nobody else ships. A reading-speed trend across the library with a per-book overlay; a weekday-by-hour *when do I read* heatmap; session-length histograms and starts-by-hour patterns; a per-page activity strip that answers *did it drag in the middle*; inferred read-through detection with per-completion cards; a reading-personality card that reads traits (chronotype, session style, weekly rhythm) off your own behaviour; and the expected furniture (year heatmap, streaks, device-parity stat cards) done carefully. Per-book `.sdr` sidecars are strictly opt-in and user-provided: hand it one and the device's own finished verdict becomes authoritative over the position-based guess and your highlights land at their true place on the activity strip, but nothing on the device is ever scanned.

The spec pins a normative definition for every derived metric (what counts as a session, a streak, a page read) so the numbers reconcile with the device and with each other; progress is an interval union on the page axis, immune to re-reads and to pagination drift when font sizes change. A two-crate workspace splits the headless ingestion-and-metrics core from the GTK shell, the charts are hand-drawn cairo on `GtkDrawingArea` across eight switchable themes (Kanagawa Dragon/Wave/Lotus, Gruvbox, Nord, Rosé Pine, Solarized) that drive both the window chrome and the graphs (no charting crate, zero new dependencies), and the tests include a reconciliation run against the real device sample. It reached 1.0 on 2026-07-05, feature-complete against the spec with Meson and Flatpak packaging shipped; the 2.0 line then dropped libadwaita for a flat, hard-edged look powered by **[vir-gtk](/codex/vir-gtk/)**, generated from the same `Theme` that colours the charts, tiling-first and portal-aware. A colophon is the note printers placed at the end of a book, the book's own record of its production; this is that idea turned toward the reading.

<p class="codex-link"><a href="https://github.com/VirInvictus/Colophon">github.com/VirInvictus/Colophon →</a></p>
