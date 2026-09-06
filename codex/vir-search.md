---
layout: codex
title: "vir-search"
codex_num: "No. 031"
description: "A domain-agnostic Rust library for parsing Calibre-style search expressions into a typed AST."
permalink: /codex/vir-search/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> <span class="status">active · v1.4.0</span></p>

A domain-agnostic Rust library for parsing Calibre-style search expressions into a typed Abstract Syntax Tree (AST).

Extracted from `atrium-search` and `conservatory-search`, `vir-search` provides the lexer, generic recursive-descent parser, ranking heuristics, and date-range resolvers that underpin the VirInvictus ecosystem. It directly powers **[Atrium](/codex/atrium/)**, **[Conservatory](/codex/conservatory/)**, and **[Viaduct](/codex/viaduct/)**.

By parameterizing the AST over the consumer's `Field`, `State`, and `SortKey` types, it avoids domain-coupling while maintaining a unified, powerful search grammar across the entire suite of desktop applications.

<p class="codex-link"><a href="https://github.com/VirInvictus/vir-search">github.com/VirInvictus/vir-search →</a></p>
