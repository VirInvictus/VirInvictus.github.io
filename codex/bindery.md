---
layout: codex
title: "Bindery"
codex_num: "No. 014"
description: "A command-line surgeon for malformed EPUBs. The fixes are deliberately boring: self-close the void elements, convert named entities to numeric"
permalink: /codex/bindery/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.10.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/bindery-sweep.webp' | relative_url }}" alt="Bindery's dry-run library sweep: per-book epubcheck results above a summary table ending in 'no files written'" loading="lazy">
</div>

A command-line surgeon for malformed EPUBs. The fixes are deliberately boring: self-close the void elements, convert named entities to numeric, sync the NCX `uid` with the OPF, put the `mimetype` entry first in the zip. Each one is deterministic, and each one lands only if [epubcheck](https://github.com/w3c/epubcheck) confirms the patient actually improved. epubcheck stays an external oracle, never a Python dependency; the package itself is stdlib only. Dry-run is the default mode, and `--apply` backs up before it touches anything.

Built to operate inside a Calibre library without breaking it: a repair atomically replaces only the `.epub`, leaving `metadata.opf`, `cover.jpg`, and the database for Calibre's own Quality Check to re-sync. An opt-in lossy mode (`--strip-pagination`) goes further, removing the baked-in page-number furniture that PDF and OCR conversions leave behind, behind its own safety guards. Sibling to oceanstrip; the two share the epubcheck no-regression gate.

<p class="codex-link"><a href="https://github.com/VirInvictus/Bindery">github.com/VirInvictus/Bindery →</a></p>
