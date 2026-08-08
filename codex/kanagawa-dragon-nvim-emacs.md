---
layout: codex
title: "kanagawa-dragon-nvim-emacs"
codex_num: "No. 013"
description: "A faithful Emacs port of the Dragon variant from kanagawa.nvim."
permalink: /codex/kanagawa-dragon-nvim-emacs/
---

<p class="codex-meta">Emacs Lisp <span class="stack-sep">·</span> <span class="status status--wip">wip · v0.1.3</span></p>

A faithful Emacs port of the Dragon variant from [kanagawa.nvim](https://github.com/rebelot/kanagawa.nvim). Not a repackaging of the existing `kanagawa-themes` package; that one has the palette right but covers too few faces to hold up in practice. This one maps the full set: every Emacs 29+ tree-sitter `font-lock-*` face, all Doom-specific surfaces (`doom-modeline-*`, `solaire-mode`, `doom-dashboard-*`), org-mode faces, magit, company, corfu, and the rest of the usual zoo. Implemented as a vanilla `deftheme` with no `doom-themes` macro dependency, so it works in stock Emacs and in Doom alike.

An ERT test suite checks palette byte-for-byte parity against the upstream nvim theme and validates representative face attributes. The acceptance criterion is visual: `sample.java` in Doom at `treesit-font-lock-level 4` should match the same file in nvim with `:colorscheme kanagawa-dragon`.

<p class="codex-link">not yet public</p>
