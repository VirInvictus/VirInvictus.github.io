---
layout: page
title: vir-tui
permalink: /codex/vir-tui/
---

# vir-tui
<span class="page-meta">Python · stdlib</span>

A lightweight, terminal UI primitive library for the VirInvictus CLI toolchain.

Provides a raw TTY event loop, a grid-based menu renderer, robust cross-platform ANSI colors, input prompt lifecycles, and a fallback progress bar wrapper for CLI applications that run headless but offer an interactive terminal interface.

Powers [CalibreQuarry]({{ '/codex/calibrequarry/' | relative_url }}) and [Lattice]({{ '/codex/lattice/' | relative_url }}).

## Features

- **GridMenu**: A 2D navigable menu system that reads raw TTY keystrokes (no `curses` required).
- **Formatters**: Consistent `success`, `info`, `warn`, `error` styling across apps.
- **Prompts**: Interactive inputs with input clearing (`ask_yn`, `prompt_int`, `prompt_out`).
- **Capture**: `run_with_capture` wrapper for redirecting stdout/stderr into a temporary scrolling buffer while a background task runs, rendering a header/footer on top.

[View on GitHub](https://github.com/VirInvictus/vir-tui)
