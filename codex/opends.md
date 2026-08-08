---
layout: codex
title: "opends"
codex_num: "No. 012"
description: "An open community toolkit and bugfix-patch project for SSI's Dark Sun CRPGs, Shattered Lands (1993) and Wake of the Ravager (1994)."
permalink: /codex/opends/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> Python <span class="stack-sep">·</span> Reverse engineering <span class="stack-sep">·</span> DOSBox <span class="stack-sep">·</span> <span class="status">active</span></p>

An open community toolkit and bugfix-patch project for SSI's *Dark Sun* CRPGs, *Shattered Lands* (1993) and *Wake of the Ravager* (1994). Tools first, patches second: a GFF container reader/writer, a GPL bytecode disassembler and byte-exact reassembler, a dialog extractor, a save inspector, and a region renderer, each a standalone MIT-licensed tool with its own README and version. Twelve ship today, working and tested (142 passing tests across a six-crate Rust workspace, with stdlib-Python companions). Nothing here redistributes a byte of the game: you bring your own GOG copy, and the toolkit reads and patches it through an overlay mount that never touches the original install. The *darkfix* patches the tools exist to produce are the next milestone, not yet shipped.

The hard problem is the engine's embedded scripting language, a GPL bytecode VM with no public spec; two decades of full-reimplementation attempts have all stalled there. OpenDS goes at it sideways, shipping the artifacts built on the way to an engine (disassemblers, chunk editors, format docs) as standalone tools, each useful on its own. The disassembler carries the full 129-entry opcode catalogue, and the reassembler round-trips the games' bytecode chunks byte-for-byte. It stands on the deepest prior reverse-engineering work (paulofthewest and the dsoageofheroes org for the GFF layout and that opcode catalogue) and keeps a per-feature manifest mapping each tool to the upstream file it came from.

<p class="codex-link"><a href="https://github.com/VirInvictus/opends">github.com/VirInvictus/opends →</a></p>
