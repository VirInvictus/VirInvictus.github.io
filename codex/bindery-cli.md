---
layout: codex
title: "bindery-cli"
codex_num: "No. 014"
description: "A command-line surgeon for malformed EPUBs. Evaluates thousands of books in minutes via a persistent Java daemon, safely unwrapping illegal HTML and cleanly installing repairs natively into Calibre."
permalink: /codex/bindery/
---

<p class="codex-meta">Python (tqdm) <span class="stack-sep">·</span> epubcheck <span class="stack-sep">·</span> <span class="status">active · v0.28.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/bindery-cli-sweep.webp' | relative_url }}" alt="bindery-cli's dry-run library sweep: per-book epubcheck results above a summary table ending in 'no files written'" loading="lazy">
</div>

A command-line surgeon for malformed EPUBs. The fixes are deterministic and cover everything from simple XML violations (self-closing void elements, numeric entity conversion, `id` colon replacements) to complex structural repairs (unwrapping illegal HTML tags, duplicate `playOrder` rewriting). Each fix lands only if [epubcheck](https://github.com/w3c/epubcheck) confirms the patient actually improved. epubcheck stays an external oracle, but bindery-cli invokes it through a persistent, transparent Java daemon that validates thousands of books in minutes without the JVM startup penalty.

Built to operate inside a Calibre library without breaking it, utilizing **[cquarry](/codex/cquarry/)** for database integration (the same engine powering **[CalibreQuarry](/codex/calibrequarry/)** and **[Hermitage](/codex/hermitage/)**): the `--install-to-calibre` mode atomically replaces the format using `calibredb`, preserving `metadata.opf`, `cover.jpg`, and the database records seamlessly. Opt-in lossy modes (`--strip-pagination`, `--strip-watermarks`, `--unwrap-illegal-tags`) go further, systematically removing baked-in page numbers, distributor stamps, and invalid HTML tags across an entire library, guarded by strict safety nets. It also includes comprehensive text auditing, replacing the former standalone `oceanstrip` and `audit_epub` tools.

<p class="codex-link"><a href="https://github.com/VirInvictus/bindery-cli">github.com/VirInvictus/bindery-cli →</a></p>
