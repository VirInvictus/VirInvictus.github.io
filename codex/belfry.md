---
layout: codex
title: "Belfry"
codex_num: "No. 008"
description: "A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can ls."
permalink: /codex/belfry/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> libmpv <span class="stack-sep">·</span> SQLite <span class="stack-sep">·</span> <span class="status status--retired">retired → Conservatory</span></p>

A native GNOME 50 podcast client: Overcast's audio engine and Castro's triage model on a filesystem you can `ls`. Smart Speed and Voice Boost are ffmpeg filter chains (`silenceremove`, `acompressor`, `loudnorm`, `rubberband`) calibrated against Overcast; the Castro **Inbox → Queue → Played** flow was the daily metaphor. The same single-writer SQLite worker that Viaduct and Atrium use fed four concurrent producers here, with Calibre's library-as-database UX (filter grammar, sortable columns, bulk actions, saved Perspectives) layered over the triage states.

Retired June 2026 and absorbed into Conservatory (No. 009). The podcast fetch/parse/triage subsystem, the libmpv Smart Speed / Voice Boost engine, and the sleep timer all moved across whole, joining a music and audiobook library on one unified queue; the one design change is that Conservatory owns and moves the files (database-canonical) rather than reading a filesystem-canonical tree. The repo is frozen and archived at the parity release, kept public as reference. Belfry got as far as the SQLite worker, read pool, and fixtures before the merge.

<p class="codex-link"><a href="https://github.com/VirInvictus/Belfry">github.com/VirInvictus/Belfry →</a></p>
