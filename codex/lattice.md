---
layout: codex
title: "Lattice"
codex_num: "No. 004"
description: "Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre."
permalink: /codex/lattice/
---

<p class="codex-meta">Python <span class="stack-sep">·</span> mutagen <span class="stack-sep">·</span> ffmpeg <span class="stack-sep">·</span> <span class="status status--complete">complete · v4.10.2</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/lattice-tui.webp' | relative_url }}" alt="Lattice's curses TUI: a bordered menu grouped into Library, Integrity, Artwork, Metadata, and Settings sections" loading="lazy">
</div>

Tooling for music collectors who keep the filesystem as the source of truth. Library-tree visualization across artist / album / track / rating / genre. Parallel FLAC / MP3 / Opus / WAV / WMA integrity verification (shelling out to `flac -t` and `ffmpeg`), embedded cover-art extraction with format-priority ranking, an art-quality audit against a configurable resolution floor, and tag, bitrate, and duplicate audits. Smart `.m3u` generation from dynamic rules (`rating >= 4 and genre == 'Jazz'`), per-genre **wings** (one library file per genre, like Calibre virtual libraries for music), and a token-efficient `--ai-library` export sized to fit a 4,000-album collection inside an LLM context window. The directory layout is configurable, so the tools never fight you about your shelving. Bare `lattice` opens a full-screen curses TUI.

The package is read-only by design: it reads tags, decodes audio, writes reports. Seven destructive companions live in `scripts/`, deliberately outside the package boundary so the read-only contract holds: `genre_tidy.py` applies a genre policy map library-wide, `rerate.py` reconciles MP3 POPM rating bytes with DeaDBeeF and foobar, `genre_foldermap.py` restructures the tree into Genre / Artist / Album, `replaygain.py` writes ReplayGain 2.0 tags through `rsgain`, and `apestrip.py` removes stray APEv2 tags. Two are worth spelling out. `retag.py` is the universal genre rewriter, abstracting the ID3 / Vorbis / iTunes-atom multi-genre chaos for safe bulk retagging. `cleaner.py` consolidates fragmented album folders: it finds sibling directories whose names normalize to the same key (curly→straight quotes, dash variants→ASCII hyphen, NFKC, lowercase) and merges them via `shutil.move`, touching no audio bytes. Size-differing collisions keep both copies under a `.from-fragment` suffix; `--dry-run` previews every move and the operation is idempotent on re-run.

<p class="codex-link"><a href="https://github.com/VirInvictus/Lattice">github.com/VirInvictus/Lattice →</a></p>
