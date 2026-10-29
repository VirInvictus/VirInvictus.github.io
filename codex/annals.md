---
layout: codex
image: /assets/img/og-card.png
title: "annals"
description: "The workspace work-record generator: every release and commit across the codex, rendered nightly into one reproducible ledger."
permalink: /codex/annals/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

Every release line in the codex is a claim, so the claims get an auditor of their own. annals walks the codex, reads each owned repo's patchnotes and git history, and renders one reproducible record: the totals and a per-repo dashboard, a month-by-month activity table, a newest-first timeline of exactly dated entries, and a coverage appendix that says where every date came from. Approximate dates are marked with ≈, never silently placed; entries the sources cannot date are listed in file order, not scattered across guessed months.

It is standard-library-only Python and read-only against every repo it watches: its writes are its own ledger and the two published site artifacts. The published copy is [the patchnotes]({{ '/patchnotes/' | relative_url }}), regenerated nightly by a script that commits only when the record changed, verifies the Pages build, and reverts on red. The front page's ledger line is spliced from the same run.

<p class="codex-link"><a href="{{ '/patchnotes/' | relative_url }}">the live record →</a></p>
