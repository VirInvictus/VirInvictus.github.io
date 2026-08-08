---
layout: codex
title: "Coffer"
codex_num: "No. 024"
description: "Envelope budgeting over a plain-text hledger journal: Actual Budget's experience, hledger's data discipline, two-way."
permalink: /codex/coffer/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> hledger <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

Envelope budgeting over a plain-text [hledger](https://hledger.org/) journal: Actual Budget's experience, hledger's data discipline, two-way. Atrium's sibling, but for money, and with the polarity inverted: the journal *is* the database, any SQLite is a disposable read cache, and the app shells out to the `hledger` binary for its reports rather than reimplementing the ledger. The hard problem, and the reason the research phase is real, is a safe append-and-edit write-back path onto a file the user also edits by hand.

A coffer is both a strongbox for valuables and the recessed panel in a coffered ceiling; finance and architecture in one word, the same dual reading as Atrium. Phase 0: the design dossier is committed, the spec is not yet locked, no code exists.

<p class="codex-link"><a href="https://github.com/VirInvictus/Coffer">github.com/VirInvictus/Coffer →</a></p>
