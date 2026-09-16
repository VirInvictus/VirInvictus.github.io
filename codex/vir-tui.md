---
layout: codex
image: /assets/img/og-card.png
title: "vir-tui"
description: "The shared terminal-UI primitive library under CalibreQuarry, lattice-music, and bindery-cli: menus, pagers, prompts, and progress boxes that degrade to plain text."
permalink: /codex/vir-tui/
---

<p class="codex-meta">Python <span class="stack-sep">·</span> stdlib <span class="stack-sep">·</span> <span class="status">active · v2.5.0</span></p>

Every CLI in the collection shares one set of terminal manners, and this is where they live. vir-tui is the primitive library under [CalibreQuarry](/codex/calibrequarry/), [lattice-music](/codex/lattice/), and [bindery-cli](/codex/bindery/): a curses-based interactive menu with type-to-filter and mouse support, a scrollable results pager, boxed input prompt lifecycles, ANSI styling that honours `NO_COLOR` and stays off when stdout is piped, and a session-aware progress box. CalibreQuarry and lattice-music run their full interactive sessions through it; bindery-cli takes the formatters and the `tqdm` re-export.

The degradation is the design constraint everything else serves: every widget falls back to plain text when there is no curses or no TTY. Menus become numbered typed lists, the pager prints, prompts read stdin, and progress goes silent, so the same tool works as a full-screen session or inside a script without forking the code. There are no dependencies: when `tqdm` is installed it is re-exported, otherwise a minimal stub stands in. Python 3.14 and up, fully type-annotated, ships a `py.typed` marker.

<p class="codex-link"><a href="https://github.com/VirInvictus/vir-tui">github.com/VirInvictus/vir-tui →</a></p>
