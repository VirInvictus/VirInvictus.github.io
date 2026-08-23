---
layout: codex
title: "audit_epub"
codex_num: "No. 028"
description: "A standard-library-only command-line tool that audits EPUB text for OCR damage, empty content, and wrong-language tags without a full decompression."
permalink: /codex/audit_epub/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.1.0</span></p>

`audit_epub` is a standalone, purely Python standard library (stdlib-only) command-line tool. It reads the raw HTML body text of `.epub` files without rendering them to flag content problems that metadata scanners and structural linters (like epubcheck) cannot catch.

It operates purely read-only. It never modifies the files it reads and never writes back to any database.

The tool is built around a single decompression pass model. Since reading and decompressing the zip archive of an EPUB is the most expensive operation, `audit_epub` is designed to decompress each file exactly once, cache the visible text, and pipe it through up to four analyzers.

### The Four Analyzers
1. **content:** Detects if an EPUB is in a foreign language despite being tagged English (`eng`), by running stopword ratios. Also flags injected pirate/ad signatures.
2. **pagenumbers:** Detects print page numbers (or running headers) baked literally into the prose flow by bad PDF-to-EPUB OCR conversions. It flags only when numbers interrupt a continuous sentence (e.g., lowercase continuation).
3. **emptytext:** Catches "Bookmate" style exports which are valid EPUBs structurally but only contain cover images and a tiny HTML placeholder. It flags files with less than 2,000 characters as EMPTY, and <20,000 characters as THIN (advisory).
4. **ocr:** Identifies OCR-damaged prose by looking for mid-sentence paragraph splits (a paragraph ending without terminal punctuation, followed by a lowercase paragraph). It uses a function-word fraction to differentiate OCR damage from stylized literary prose.

### Dual Modes
- **Directory Mode:** Recursively scans a directory of `.epub` files (e.g., `~/Downloads`). Ideal for pre-import vetting.
- **Library Mode:** If a `metadata.db` (Calibre database) is present in the current working directory, it reads the database (`mode=ro`) to find EPUB paths and only scans those. 

<p class="codex-link"><a href="https://github.com/VirInvictus/audit_epub">github.com/VirInvictus/audit_epub →</a></p>
