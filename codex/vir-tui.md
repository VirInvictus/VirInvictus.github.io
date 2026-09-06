---
layout: page
title: vir-tui
permalink: /codex/vir-tui/
---

# vir-tui
<span class="page-meta">Python · stdlib · v2.3.0</span>

A lightweight, terminal UI primitive library for the VirInvictus CLI toolchain.

Provides a raw TTY event loop, a grid-based menu renderer, robust cross-platform ANSI colors, input prompt lifecycles, and a fallback progress bar wrapper for CLI applications that run headless but offer an interactive terminal interface.

Powers [CalibreQuarry]({{ '/codex/calibrequarry/' | relative_url }}), [lattice-music]({{ '/codex/lattice/' | relative_url }}), and [bindery-cli]({{ '/codex/bindery/' | relative_url }}).

## Features

- **GridMenu**: A 2D navigable menu system over `curses`, with mouse support and type-to-filter at 15+ items.
- **Formatters**: Consistent `success`, `info`, `warn`, `error` styling across apps.
- **Prompts**: Interactive inputs with input clearing (`ask_yn`, `prompt_int`, `prompt_out`).
- **Capture**: `run_with_capture` wrapper for redirecting stdout/stderr into a temporary scrolling buffer while a background task runs, rendering a header/footer on top.

[View on GitHub](https://github.com/VirInvictus/vir-tui)
