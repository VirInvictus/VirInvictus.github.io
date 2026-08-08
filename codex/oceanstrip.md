---
layout: codex
title: "oceanstrip"
codex_num: "No. 015"
description: "Strips producer and redistributor watermarks out of EPUBs. What began as an OceanofPDF.com-only tool is now a small signature registry: OceanofPDF's..."
permalink: /codex/oceanstrip/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

Strips producer and redistributor watermarks out of EPUBs. What began as an OceanofPDF.com-only tool is now a small signature registry: OceanofPDF's injected link (and its stray marker file), and the ABC Amber LIT Converter stamp that old `.lit` conversions leave on nearly every page, each caught in both an anchored form (the stamp is a link) and an anchorless form (plain text, with no `<a>` to catch). Adding another producer is one table entry. The removal is balanced-element surgery rather than regex slicing: find the stamp, walk up to the outermost wrapper whose entire visible text is the watermark, and delete that whole well-formed element, so real prose that merely mentions the URL is never touched and a well-formed file stays well-formed. Works on a single file or sweeps an entire library, always writing new copies (originals are never modified), and every output is epubcheck-clean. Stdlib only, like its sibling Bindery.

<p class="codex-link"><a href="https://github.com/VirInvictus/Oceanstrip">github.com/VirInvictus/Oceanstrip →</a></p>
