---
layout: codex
image: /assets/img/og-card.png
title: "CalibreQuarry"
description: "Calibre power-user tooling built on cquarry: catalogs, statistics, integrity audits, and write-capable curation companions."
permalink: /codex/calibrequarry/
---

<p class="codex-meta">Python <span class="stack-sep">·</span> cquarry <span class="stack-sep">·</span> vir-tui <span class="stack-sep">·</span> <span class="status">active · v3.48.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/calibrequarry-stats.webp' | relative_url }}" alt="CalibreQuarry's --stats output: hierarchical dot-taxonomy tag counts, series with book totals, publishers, languages, and recent additions" loading="lazy">
</div>

Calibre power-user tooling built on **[cquarry](/codex/cquarry/)**, the same core powering **[Hermitage](/codex/hermitage/)** and **[bindery-cli](/codex/bindery/)**. Its recursive-descent parser hits **100% parity with Calibre's internal search-expression syntax**, validated by a test suite mapped against Calibre's own `SearchQueryParser`. The same engine resolves Virtual Library definitions out of the `preferences` table and powers the `--search` mode (author / `vl:` / boolean / parens / `=`-prefix exact match).

Author-grouped catalogs, with `--all-wings` emitting one per virtual library. Library statistics across format, rating, tag taxonomy, and top authors / tags. **Audit** modes for untagged, unrated, coverless, series-gap, duplicate, and low-resolution covers (parsing on-disk JPEGs with no external libraries); **analytics** modes for per-author breakdowns, added-per-month pace, hierarchical tag trees, and wing overlap. JSON / CSV / AI exports, custom-column extraction, and an automatic DB snapshot when Calibre holds a write lock. Installs from PyPI as `calibrequarry`. Tested on Fedora 44 against Calibre 9.7.

Alongside the package sits a `scripts/` shelf of write-capable companions, deliberately outside the read-only contract: `audit_drm.py` scans every format for encryption a metadata sweep would wave through, `reconcile_file_metadata.py` compares curated database values against the metadata embedded in each file (and can push the database back into the files), `validate_metadata.py` lints the `metadata.db` itself, `spot_check.py` samples random books for the corruption pattern sweeps miss, and `compress_pdf.py` shrinks the occasional 1 GB sourcebook through ghostscript.

The newest of them, `audit_isbns.py`, asks a question nothing else in the Calibre ecosystem does: not *is this ISBN well-formed* but *does it identify this book*. Calibre downloads metadata and never re-examines what it stored, so a wrong identifier stays invisible behind a passing checksum. A four-source sweep of a validator-clean 6,786-ISBN library found 51 pointing at a different book, the dominant shape being a same-publisher sibling; *Programming Clojure* carried *tmux 2*'s number, and *A Book on C* carried `9782147483649`, the 2147483649 integer-overflow constant dressed as an ISBN. The script verifies against the ISBN each book prints on its own copyright page, reading body text only and never the embedded metadata, because `reconcile_file_metadata.py` writes the database's values into those blocks and comparing against them would confirm every error the tool exists to find. Most of the work is not crying wolf: a bibliography printing 49 other ISBNs is classified as a citing work, a bundle reports `AMBIGUOUS` for a human, and a print-versus-ebook variant sharing the registrant prefix reports `VARIANT` rather than `SUSPECT`. There is deliberately no `--apply` and there will not be one, because single-source verdicts proved wrong often enough that an auto-fixer would have "corrected" four books that were already right.

<p class="codex-link"><a href="https://github.com/VirInvictus/CalibreQuarry">github.com/VirInvictus/CalibreQuarry →</a></p>
