---
layout: codex
title: "dragon-themer"
codex_num: "No. 030"
description: "Retheming a tiling desktop means hand-editing the same eight hex values into thirty files and finding the two you missed a week later."
permalink: /codex/dragon-themer/
---

<p class="codex-meta">Ruby (stdlib only) <span class="stack-sep">·</span> ERB <span class="stack-sep">·</span> <span class="status status--design">design</span></p>

Retheming a tiling desktop means hand-editing the same eight hex values into thirty files and finding the two you missed a week later. dragon-themer makes it one command: one palette as the source of truth, rendered through pure ERB templates into every colour-bearing config on the machine, with each group (desktop, terminal, editor, apps) able to move independently, because a terminal and a desktop do not have to agree.

The model is small enough to state in a sentence. A **theme** is fourteen named colour roles in a YAML file, a **target** declares where bytes go and how to check and reload them, and a **template** turns the palette into one tool's config syntax; the engine holds no knowledge of any specific tool, so hyprland and cava are data rather than code. Where a tool supports an include, dragon-themer owns only a small generated file and never touches the hand-written config, so switching themes leaves tracked dotfiles clean.

The safety design is the reason it exists as a project rather than a script. Rendering is all-or-nothing: nothing is written until every target has rendered and passed a syntax check, so a broken template fails the run while the desktop is still untouched. Targets that can cost you a graphical session, the hypr family above all, sit in a `critical` tier that adds a verify-after-reload step and an automatic restore when the check fails, because on a machine with no fallback session a bad render does not degrade the desktop, it drops you to a TTY. Ten themes, muted and warm-leaning by house preference rather than by popularity, with upstream base16 attribution carried in the theme files. Ruby stdlib, no gems, ever. The spec and an eleven-phase roadmap are committed; no code yet.

<p class="codex-link">in development</p>
