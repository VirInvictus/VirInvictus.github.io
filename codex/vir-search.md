---
layout: codex
image: /assets/img/og-card.png
title: "vir-search"
description: "A domain-agnostic Rust library for parsing Calibre-style search expressions into a typed AST."
permalink: /codex/vir-search/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.4.3</span></p>

One search grammar serves three applications, and this is the library that parses it: Calibre-style search expressions in, a typed Abstract Syntax Tree (AST) out.

Extracted from `atrium-search` and `conservatory-search`, it carries the lexer, the generic recursive-descent parser, the ranking heuristics, and the date-range resolvers used by **[Atrium](/codex/atrium/)**, **[Conservatory](/codex/conservatory/)**, and **[Viaduct](/codex/viaduct/)**.

The AST is parameterized over each consumer's `Field`, `State`, and `SortKey` types, so the grammar stays shared while every application compiles it against its own domain: one parser, no domain coupling, and no second grammar to keep in parity.

<p class="codex-link"><a href="https://github.com/VirInvictus/vir-search">github.com/VirInvictus/vir-search →</a></p>
