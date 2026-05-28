---
layout: post
title: "The Workshop: A Day at the Terminal"
date: 2026-05-16
description: Ghostty, zsh, Doom, LazyVim, the modern coreutils replacements, and the small scripts that bind them together.
---

<div markdown="1" class="dropcap">
A *What I Use* tells you what is on the desk. It does not tell you how the desk gets used. The terminal is where I spend the most consecutive minutes of any working day, more than the browser and more than either editor; that hour budget is what justifies the time spent shaping it. This is a walk through the shape: the Ghostty config and the zsh that follows, the two editors and the deliberate split between them, the daily binaries that replaced their POSIX ancestors, and the small scripts in `~/.local/bin/` that quietly take pressure off the rest of the system.
</div>

## I. The Terminal Itself
{: #the-terminal-itself}

[**Ghostty**](https://ghostty.org/) runs everything. The config is under seventy lines and most of them are keybindings. The ones that earn their keep:

```
window-decoration = false
background-opacity = 0.97
background-blur = 40
unfocused-split-opacity = 0.65
```

The last line is the one that matters. When you have three panes open and one is an editor and the others are a build log and a `watchexec`, having the inactive panes physically dim is the single biggest cognitive-load reduction a multiplexer can offer. tmux has nothing this honest. I have stopped reaching for it inside Ghostty entirely; splits and tabs live on `Ctrl+Shift` with vim navigation (`{h,j,k,l}`), and `Ctrl+Shift+Z` zooms a pane to fullscreen and back. That, plus `copy-on-select = true` and middle-click paste, is the multiplexer I needed.

Font is **TX-02** at thirteen point with the slashed-zero and single-story `a`/`g` feature flags on.

<p class="ornament ornament--fleuron">❦</p>

## II. The Shell
{: #the-shell}

zsh, with **starship** for the prompt and **atuin** for history.

**Transient prompt.** Starship paints a multi-line, branch-aware, status-coloured prompt at the current line. Every prompt above it collapses to a single bare arrow:

```zsh
function enable-transience() { PROMPT='➜ ' }
zstyle ':prompt:starship:transient' promotion enable-transience
```

The difference between a scrollback that reads like a chat log and a scrollback that reads like a transcript.

**Atuin replaces history outright.** `ATUIN_NOBIND=true` plus `bindkey '^r' atuin-search` means `Ctrl-R` opens a proper full-text shell-history search and nothing else does. The zsh history is still in place at a million lines deep, but the working surface is Atuin.

**fzf with `fd` behind it.** `FZF_CTRL_T_COMMAND` walks with `fd --hidden`, excluding `.git`, `.npm`, `.wine`, `.cache`, and `node_modules`. `Ctrl-T` becomes a navigation primitive instead of a curiosity.

**zoxide aliased over cd.** `eval "$(zoxide init --cmd cd zsh)"`. Muscle memory keeps working and the directory database learns underneath. After three weeks, `cd at` lands in `~/.gitrepos/Atrium` without the rest of the path. There is no other piece of CLI I would more strongly recommend to a friend.

**Two `git` configurations side by side.** `git` runs in the current repo. `config` runs against my dotfiles, which live as a bare repo at `~/.dotfiles/` with `~` as the work tree:

```zsh
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
```

No symlink farm, no chezmoi, no stow. The home directory is the work tree; the bare repo lives one directory down where `git status` won't see it.

The single funniest alias I have written is `zc`, which is `killall {% raw %}{{Z,z}oom,{D,d}iscord}{% endraw %}`. A one-line meeting eject.

<p class="ornament ornament--fleuron">❦</p>

## III. The Daily Binaries
{: #the-daily-binaries}

The household replacements: [**`eza`**](https://github.com/eza-community/eza) for `ls`, with `l`/`ll`/`lt` aliases for default, long, and modified-time sort; [**`bat`**](https://github.com/sharkdp/bat) for `cat`, themed `gruvbox-dark` (one day I'll port Kanagawa Dragon); [**`rg`**](https://github.com/BurntSushi/ripgrep) for `grep`, with `.gitignore` honoured by default (the entire pitch); [**`fd`**](https://github.com/sharkdp/fd) for `find`, with no `-exec` ceremony; [**`lazygit`**](https://github.com/jesseduffield/lazygit), the rare TUI I prefer to its underlying command; [**`delta`**](https://github.com/dandavison/delta) wired into the git pager so every diff arrives syntax-highlighted and side-by-side; [**`atuin`**](https://atuin.sh/), as above, carrying the history.

Less obvious:

* [**`hyperfine`**](https://github.com/sharkdp/hyperfine) when I have a hunch about whether a change made something faster and want the question answered in thirty seconds.
* [**`tokei`**](https://github.com/XAMPPRocky/tokei) for code stats. `tokei .` against the Atrium workspace is the most honest answer to *how big has this gotten*.
* [**`watchexec`**](https://github.com/watchexec/watchexec) for filesystem-driven loops. `watchexec -e rs cargo test` is half the Rust workflow.
* [**`just`**](https://github.com/casey/just) as a saner `make`. Recipes, simple dependencies, no significant whitespace.
* [**`navi`**](https://github.com/denisidoro/navi) for cheatsheets, on `Ctrl-G`.
* [**`gum`**](https://github.com/charmbracelet/gum) when a shell script needs a TUI and I do not want to write one.
* [**`dust`**](https://github.com/bootandy/dust) for `du`; [**`duf`**](https://github.com/muesli/duf) for `df`; [**`btop`**](https://github.com/aristocratos/btop) for `top`. On the AMD T14s, `amdgpu_top` joins the panel.

A small constellation of Python tools lives behind `uv tool`: [**`mitmproxy`**](https://mitmproxy.org/), [**`sqlmap`**](https://sqlmap.org/), [**`binwalk`**](https://github.com/ReFirmLabs/binwalk), [**`yt-dlp`**](https://github.com/yt-dlp/yt-dlp). The first three are for CTF and security study; the fourth is for the day a podcast feed quietly drops a back-catalogue episode and I want it on the disk. `pipx` was the previous answer; `uv tool` is the current one.

Finally, [`hledger`](https://hledger.org/) and the `hb` / `hr` / `his` / `hbs` aliases. Plaintext double-entry bookkeeping in the shell is one of the small civilizational gifts of the Free Software era.

<p class="ornament ornament--fleuron">❦</p>

## IV. Two Editors, On Purpose
{: #two-editors}

**LazyVim.** The configuration is, deliberately, almost nothing. `~/.config/nvim/lua/config/` has four files; three of them (`options.lua`, `keymaps.lua`, `autocmds.lua`) are under ten lines apiece, empty placeholders inheriting LazyVim's defaults; the fourth (`lazy.lua`) is the stock bootstrap. The only override that matters lives in `lua/plugins/colorscheme.lua`, twenty lines of `kanagawa.nvim` with `theme = "dragon"` and `transparent = true` so the terminal alpha bleeds through. LazyVim is good. I do not need to make it mine. The editor is for cutting, and the only customisation I want is the colour scheme matching the rest of the desk. LSPs come in via Mason: `rust-analyzer`, `pyright`, `jdtls`, `clangd`.

**Doom Emacs.** The exact opposite philosophy. `~/.config/doom/config.org` is twenty-six hundred lines of literate Org that tangles to `config.el` on every `doom sync`. I have phases the way the portfolio projects have phases: literate-config bootstrap; Org core; the GTD agenda; a student layer for Northern College course files; spaced repetition with `org-fc`; a typography pass with `mixed-pitch` and `org-modern` and `visual-fill-column`; the portfolio hub; a math layer with `cdlatex` and `org-fragtog` rendering LaTeX fragments in line at HiDPI; the Roam UX. Phase 13 is queued: GPG encryption on the per-month finance files. Phase 14 is `pdf-tools` and `org-noter`. The phases are deliberately not all shipped; the brain is permitted to grow when there is friction, and only then.

The typography is the part I would defend most strongly. TX-02 semi-light at 18pt for code; **Tiempos Text** at 20pt for prose; `mixed-pitch-mode` swaps the variable face into prose buffers while leaving code blocks, tables, and properties in monospace; `visual-fill-column` centers prose at ninety-five columns and toggles itself off when the window is too narrow; `org-appear` reveals emphasis markers only when the cursor is on them. The result, at full screen, is the closest a code editor has come to typesetting. I write the journal in this. I write course notes in this. I wrote this post in this.

Every helper in the Doom config is namespaced under `+bdkl/`. The `+` is the Doom convention for user functions; `bdkl/` makes them mine; the `--` double-dash on private helpers signals *not a public command*. This is the same naming hygiene I would impose on Rust modules. Elisp permits global names. The permission is not an obligation.

Custom keybindings live under `SPC X` as a personal leader. `SPC X R` is the *AI bundle builder*, a capture that gathers the current project's `spec.md`, `roadmap.md`, and a slice of the agenda into a clipboard-ready prompt. `SPC X H` opens the portfolio hub: an Org-rendered table of every project's version, tagline, last-commit, and language.

<p class="ornament ornament--fleuron">❦</p>

## V. The Scripts in `~/.local/bin/`
{: #scripts}

`~/.local/bin/` holds a small set of hand-written zsh utilities that have absorbed the parts of system maintenance I no longer want to think about.

**`sys_maintain`.** Full-system update with an *eighteen-hour cooldown*. One invocation talks to DNF5, Flatpak (system and user), `fwupdmgr`, `pipx`, `rustup`, `uv` (self-update *and* tool-upgrade), `gem`, `cargo install-update`, `claude update`, `doom upgrade && doom sync`, then `sys_snapshot`, then autoremove, a `journalctl` vacuum, a DNF consistency check, and reboot detection. A clean run writes a Unix timestamp to `~/.local/state/sys-maintain-timestamp`; the next run reads it, refuses to do anything within eighteen hours, and prints, in colour, the exact `HH:MM:SS on Weekday, Month Day` at which the lock expires. `--force`, `--reset`, `--dry-run`. A SIGINT trap unwinds the sudo keepalive without setting the stamp, so an interrupted run is safe to repeat. Failures get collected and reported; the stamp is not written unless everything succeeded.

The reason for the cooldown is restraint. Without one I would run system updates four times a day, because checking is irresistible. A laptop is not a build server. The script that prevents me from poking at it is more valuable than the script that pokes at it.

**`sys_snapshot`.** A content-aware snapshot of the laptop-specific bits that aren't in the dotfiles repo: `/etc/thinkfan.yaml`, `/etc/modprobe.d/thinkfan.conf`, a udev rule for power profiles, a systemd unit for battery-charge thresholds, `/etc/fstab`. Plus four generated manifests: DNF, Flatpak, `cargo install --list`, `uv tool list`. Each file copies to `~/.config/system-backup/` only if its content has changed; the previous version rotates to `.bak`. The whole directory is picked up by **borgmatic** in its hourly run.

This is the single most valuable script I have written for my own machine. A clean Fedora reinstall is now a one-evening exercise: clone the dotfiles bare repo, replay the four manifests, paste the snapshotted system files back, restore `~/org/` from borg. I learned to write this by getting it wrong twice.

**`update_calibre`, `update_hledger`, `update_gemini`.** Three version-aware updaters, one each for a tool that doesn't ship through DNF or Flatpak on Fedora. Same shape: read local version, hit the canonical API (GitHub releases, npm), compare with `sort -V`, refuse to downgrade, gate on a `[y/N]`, download, install, clean up. None of them are clever. They are the kind of script you write once and leave alone for the rest of the laptop's life.

**`doom-mode` (in `.zshrc`).** Yamagi Quake 2, Hammer of Thyrion's Hexen 2, dhewm3, Ironwail Quake, uzdoom. The function turns *touchpad-disable-while-typing* **off** before launching (dodging Cyberdemon fire with a dead touchpad is its own punishment), then back **on** when the game exits. Six lines of `gsettings` and a `case` block. The kind of small humane fix you never get from a vendor.

<p class="ornament ornament--fleuron">❦</p>

## VI. The Shape of `~`
{: #home-directory}

The home directory is laid out the way the library is laid out. Each top-level is a working surface; nothing escapes its surface.

```
~/.gitrepos/   ← workspace, parent of every project repo
~/docs/        ← Calibre Library + papers + catalogues + zines
~/org/         ← Doom's second brain (private, never tracked)
~/Tasks/       ← Atrium's Org-mode round-trip surface
~/school/      ← Northern College coursework
~/Games/       ← native game installs (Quake, Hexen, Doom ports)
~/Zotero/      ← academic library
~/Sync/        ← one Syncthing folder, named for what it is
~/.dotfiles/   ← bare git repo for the home work tree
```

`~/.gitrepos/` is the *workshop*: not a git repo itself, the parent directory of every project. A `CLAUDE.md` at its root maps which directories are portfolio code, which are exploratory, which belong to friends, and which are read-only by policy. Writing it forced me to draw the boundary between projects I'm shipping and projects I am, in the language of the file, *poking at curiously*.

`~/docs/` is one tree, two species. **`~/docs/Calibre Library/`** is the four-thousand-six-hundred-book SQLite library that anchors three of the portfolio projects. **`~/docs/papers/`** is a hand-organised archive in sixteen subtrees, by topic. `doc_inventory` in `.zshrc` walks them; `update_docs` regenerates the Calibre catalogues into `~/docs/catalogs/` and snapshots the paper directory alongside them.

`~/org/` is *deliberately* not git-tracked. The finance files contain enough information about my actual life that the encryption phase is queued; until then, the privacy budget is *don't sync it, don't track it, let borgmatic carry the encrypted offsite copy*. Inside: `inbox.org`, the GTD project files, `roam/` for daily journals and concept notes, `courses/` for BCS flashcard decks, `finance/YYYY-MM.org` for per-month ledgers, and `reviews.org`.

`~/Tasks/` is Atrium's Org-mode round-trip target. `atrium-cli export org ~/Tasks` writes the live SQLite store out to plain text with UUIDs, CLOCK drawers, and TODO state preserved; `atrium-cli import org ~/Tasks` reads it back. If the round-trip stops being identical, the round-trip is wrong; the script that proves it is two lines.

`~/.dotfiles/` is the bare repo described in §II. Cloning to a fresh machine is `git clone --bare repo ~/.dotfiles && config checkout`. No further ceremony.

<p class="ornament ornament--fleuron">❦</p>

## VII. The Languages
{: #the-languages}

In roughly the order it eats my week:

**Rust.** Atrium, Viaduct, and Belfry are all Rust. The reasons are the boring ones: compile-time invariants beat code review, sum types beat status enums, `Result<T, E>` beats throwing, `cargo` beats every other build tool I have used. The reason that doesn't get said often enough is that *the architectural conversation in Rust is honest*. You cannot hide a lifetime bug behind a runtime cast. The single-writer SQLite worker, the read-only connection pool, the `Send + Sync` boundary on a tokio handler: these are not conventions, they are load-bearing types. I am not as fast in Rust as I am in Python yet; I am closer than I was a year ago, and the work survives me in a way Python never will.

**C.** Framework is C, for the same reason `mupdf`, `cairo`, and `gtk4` are C: no FFI tax, no glue-language tax, the binding surface is the bare metal. K&R is the most important book I have read.

**Python.** Hermitage is Python because GTK4 via PyGObject is a perfectly serviceable native-desktop story. CalibreQuarry is Python, stdlib-only, because the constraint *forced* me to write a real recursive-descent parser instead of pulling in `lark` and waving. The constraint was the point. I love Python the way I would love a well-worn pair of work boots: type hints throughout, `from __future__ import annotations`, `dataclasses` over namedtuples, `pathlib` over string paths, `argparse` over `click` until `click` is justified. The standard library is enormous, and most people writing Python never finish reading it.

**Ruby.** A language I keep trying to graduate from *liking* to *using*. `rbenv` is installed; 3.4.8 is the current version. Sandi Metz's *Practical Object-Oriented Design* is the book of hers I most often re-shelve at the front. I am waiting for the project that wants to be Ruby: a small Sinatra service, a Thor CLI, a static-site engine. The thirst is real.

**C++.** I write more C++ than I admit. The version that wants my attention is the one Scott Meyers writes about: C++17 with `-Wall -Wpedantic`, not C++26.

**Java.** School. The Computer Engineering Technician program at Northern College is Java-first; `jdtls` in LazyVim and the `(java +lsp +dap)` layer in Doom carry the coursework. Java is a more honest language than its 2000s reputation gives it credit for, and the JVM is, separately, a remarkable piece of engineering. I will not be writing Atrium in it. I am also no longer rolling my eyes when someone else reaches for it.

Languages I am studying deeper into:

* **Zig.** A smaller language than Rust, no hidden allocations, `comptime` as a first-class metaprogramming surface, and the most readable system-language standard library I have ever browsed. The 1.0 release is not here yet; the language is real now anyway.
* **Go.** Fast compilation, honest concurrency primitives, a standard library that does almost everything anyone would ask of it. The language I would write a small backend service in if I had one to write.
* **OCaml.** Probably the one I am most curious about. The MirageOS work, the Jane Street functional-programming tradition, the type system that quietly handles what Haskell handles loudly. If I ever sit down with the compilers project I have been mentally drafting since the Calibre search parser, the front end is going to be OCaml.
* **Common Lisp.** For the same reason a chef should be able to butcher a chicken. I am not going to write production CL; I would like to be able to *read* it, including SBCL itself.
* **Erlang/Elixir.** The most beautiful concurrency story in the field and one I have never lived inside. Armstrong's thesis is on the shelf.

None of these are on the list for hiring. They are on the list because the field has more good ideas in it than any one career can absorb, and the only reasonable response is to keep absorbing.

<p class="ornament ornament--fleuron">❦</p>

## VIII. What the History Shows
{: #atuin-confessional}

Atuin keeps everything. Eight-and-a-half thousand commands in the local index, ranked by recency, fully searchable. The interesting question a year of full history can answer, more honestly than a wishful inventory, is *which tools actually do the work?*

Strip the navigation noise (`ls`, `cd`, `exit`, `v` for `nvim`) and the most-typed program prefix is `cat`, at four hundred and twenty-eight invocations. The runner-up is `rm`. I am not, it turns out, the curated minimalist I sometimes pretend to be on the internet; I am a person who copies-and-deletes-and-cats a great deal of files.

In third place, with two hundred and one entries, is `nano`. Both Neovim and Doom Emacs are recent additions to my life, and I am not yet fluent enough in either to make them the *fastest* tool for a fifteen-second edit of a system file. `nano` is, on its own merits, a good piece of software. It does one thing, it tells you how to do that thing at the bottom of the screen, and it does not impose a mode model on a config change that doesn't deserve one. `gedit` shows up for the same reason. There is a real category of edit (`/etc/thinkfan.yaml`, a fresh shell script, one line in a borgmatic config) for which the right tool is the simple tool. The vim and Emacs fluency will catch up.

The artifact I am most pleased by is a one-off test file dated 2026-05-14: `echo "phase 13" > /tmp/test.txt`, followed by a successful `gpg --encrypt`. The first end-to-end rehearsal of the Doom finance-encryption phase. The phase still isn't shipped. That is how the *brain* changes shape: a queued idea, a one-evening proof, and then a wait until the moment is right to roll the rest of the work in behind it.

<p class="ornament ornament--asterism">⁂</p>

The point is not the configs. The point is that there is a small, stable surface of tools and conventions that I iterate against, and the iteration is most of the value. A `.zshrc` that grows by one alias a quarter and shrinks by one a quarter is a healthier `.zshrc` than one that gets longer forever. A `~/.local/bin/` with five scripts in it is a healthier folder than one with fifty.

The workshop should be a small room with the right tools at hand, not a museum. That is the version I am trying to keep.
