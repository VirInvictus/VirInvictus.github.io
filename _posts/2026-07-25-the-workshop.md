---
layout: post
title: "The Workshop: A Day at the Terminal"
date: 2026-07-25
description: Ghostty, zsh, Doom, LazyVim, Helix, the modern coreutils replacements, and the small scripts that bind them together.
---

<div markdown="1" class="dropcap">
A *What I Use* tells you what is on the desk. It does not tell you how the desk gets used. The terminal is where I spend the most consecutive minutes of any working day, more than the browser and more than either editor; that hour budget is what justifies the time spent shaping it. This is a walk through the shape: the Ghostty config and the zsh that follows, the three editors and the deliberate split between them, the daily binaries that replaced their POSIX ancestors, and the small scripts in `~/.local/bin/` that take a great deal of pressure off the rest of the system.
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

The last line is the one that matters. When you have three panes open and one is an editor and the others are a build log and a `watchexec`, having the inactive panes physically dim is the single biggest cognitive-load reduction a multiplexer can offer. tmux has no equivalent. I have stopped reaching for it inside Ghostty entirely; splits and tabs live on `Ctrl+Shift` with vim navigation (`{h,j,k,l}`), and `Ctrl+Shift+Z` zooms a pane to fullscreen and back. That, plus `copy-on-select = true` and middle-click paste, is the multiplexer I needed.

Font is **TX-02** at ten point, with **Symbols Nerd Font Mono** behind it for glyph fallback. Exactly two font features are on: `calt` for the programming ligatures and `ss01` for the slashed zero, which matters because TX-02's *default* zero is the dotted one.

That took an audit to get right. I had previously turned on a handful of stylistic sets on the strength of what their names implied, and when I finally checked by hashing the glyph outlines rather than trusting the feature tags, most of them turned out to be no-ops: `ss02` produced an outline byte-identical to the default zero, `ss04` "crossed seven" was already the default seven, `ss05` moved the `r` twenty units and changed nothing else. There is no single-story `a` or `g` in this font at all, which I had also believed for a while. The lesson generalises past typography: a feature that *remaps* something is not the same as a feature that *changes* something, and the only way to tell is to compare the artifacts.

<p class="ornament ornament--fleuron">❦</p>

## II. The Shell
{: #the-shell}

zsh, with **starship** for the prompt and **atuin** for history.

**Transient prompt.** Starship paints a multi-line, branch-aware, status-coloured prompt at the current line. Every prompt above it collapses to a single bare arrow:

```zsh
function enable-transience() { PROMPT='➜ ' }
zstyle ':prompt:starship:transient' promotion enable-transience
```

It turns the scrollback from a chat log into a transcript.

**Atuin replaces history outright.** `ATUIN_NOBIND=true` plus `bindkey '^r' atuin-search` means `Ctrl-R` opens a proper full-text shell-history search and nothing else does. The zsh history is still in place at a million lines deep, but the working surface is Atuin.

**fzf with `fd` behind it.** `FZF_CTRL_T_COMMAND` walks with `fd --hidden`, excluding `.git`, `.npm`, `.wine`, `.cache`, and `node_modules`. `Ctrl-T` becomes a navigation primitive instead of a curiosity.

**zoxide aliased over cd.** `eval "$(zoxide init --cmd cd zsh)"`. Muscle memory keeps working and the directory database learns underneath. After three weeks, `cd at` lands in `~/.gitrepos/Atrium` without the rest of the path. There is no other piece of CLI I would more strongly recommend to a friend.

**Two `git` configurations side by side.** `git` runs in the current repo. `config` runs against my dotfiles, which live as a bare repo at `~/.dotfiles/` with `~` as the work tree:

```zsh
alias config='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
```

No symlink farm, no chezmoi, no stow. The home directory is the work tree; the bare repo lives one directory down where `git status` won't see it.

The single funniest alias I have written is `zc`, which is `killall {% raw %}{{Z,z}oom,{D,d}iscord}{% endraw %}`, a one-line meeting eject.

<p class="ornament ornament--fleuron">❦</p>

## III. The Daily Binaries
{: #the-daily-binaries}

The household replacements: [**`eza`**](https://github.com/eza-community/eza) for `ls`, with `l`/`ll`/`lt` aliases for default, long, and modified-time sort; [**`bat`**](https://github.com/sharkdp/bat) for `cat`, themed `gruvbox-dark` (one day I'll port Kanagawa Dragon); [**`rg`**](https://github.com/BurntSushi/ripgrep) for `grep`, with `.gitignore` honoured by default (which is why I switched); [**`fd`**](https://github.com/sharkdp/fd) for `find`, with no `-exec` ceremony; [**`lazygit`**](https://github.com/jesseduffield/lazygit), the rare TUI I prefer to its underlying command; [**`delta`**](https://github.com/dandavison/delta) wired into the git pager so every diff arrives syntax-highlighted and side-by-side; [**`atuin`**](https://atuin.sh/), as above, carrying the history.

Less obvious:

* [**`hyperfine`**](https://github.com/sharkdp/hyperfine) when I have a hunch about whether a change made something faster and want the question answered in thirty seconds.
* [**`tokei`**](https://github.com/XAMPPRocky/tokei) for code stats. `tokei .` against the Atrium workspace is the fastest answer to *how big has this gotten*.
* [**`watchexec`**](https://github.com/watchexec/watchexec) for filesystem-driven loops. `watchexec -e rs cargo test` is half the Rust workflow.
* [**`just`**](https://github.com/casey/just) as a saner `make`. Recipes, simple dependencies, no significant whitespace.
* [**`navi`**](https://github.com/denisidoro/navi) for cheatsheets, on `Ctrl-G`.
* [**`gum`**](https://github.com/charmbracelet/gum) when a shell script needs a TUI and I do not want to write one.
* [**`dust`**](https://github.com/bootandy/dust) for `du`; [**`duf`**](https://github.com/muesli/duf) for `df`; [**`btop`**](https://github.com/aristocratos/btop) for `top`; [**`procs`**](https://github.com/dalance/procs) for `ps`. On the AMD T14s, `amdgpu_top` joins the panel.
* [**`sd`**](https://github.com/chmln/sd) for the find-and-replace half of `sed`, where the regex dialect is the one I already know instead of the one `sed` insists on.
* [**`ast-grep`**](https://ast-grep.github.io/) for the searches `rg` structurally cannot do, when the pattern is a shape in the syntax tree rather than a string.
* [**`difftastic`**](https://difftastic.wilfred.me.uk/) when `delta`'s line view is not enough and I need the diff to understand the grammar it is diffing.
* [**`yazi`**](https://github.com/sxyazi/yazi) for the times a file manager genuinely beats a shell, and [**`trippy`**](https://github.com/fujiapple852/trippy) when the network is the suspect.

A small constellation of Python tools lives behind `uv tool`: [**`mitmproxy`**](https://mitmproxy.org/), [**`sqlmap`**](https://sqlmap.org/), [**`binwalk`**](https://github.com/ReFirmLabs/binwalk), [**`yt-dlp`**](https://github.com/yt-dlp/yt-dlp). The first three are for CTF and security study; the fourth is for the day a podcast feed quietly drops a back-catalogue episode and I want it on the disk. `pipx` was the previous answer; `uv tool` is the current one.

Finally, [`hledger`](https://hledger.org/) and the `hb` / `hr` / `his` / `hbs` aliases. Plaintext double-entry bookkeeping in the shell is one of the more underrated gifts of the Free Software era.

<p class="ornament ornament--fleuron">❦</p>

## IV. Three Editors, On Purpose
{: #two-editors}

**LazyVim.** The configuration is, deliberately, almost nothing. `~/.config/nvim/lua/config/` has four files; three of them (`options.lua`, `keymaps.lua`, `autocmds.lua`) are under ten lines apiece, empty placeholders inheriting LazyVim's defaults; the fourth (`lazy.lua`) is the stock bootstrap. The only override that matters lives in `lua/plugins/colorscheme.lua`, twenty lines of `kanagawa.nvim` with `theme = "dragon"` and `transparent = true` so the terminal alpha bleeds through. LazyVim is good. I do not need to make it mine. The editor is for cutting, and the only customisation I want is the colour scheme matching the rest of the desk. LSPs come in via Mason: `pyright`, `jdtls`, `clangd`, `gopls`, `lua-language-server`, `ruby-lsp`. `rust-analyzer` is the exception, since it ships with the rustup toolchain and Mason never sees it.

**Doom Emacs.** The exact opposite philosophy. `~/.config/doom/config.org` is twenty-six hundred lines of literate Org that tangles to `config.el` on every `doom sync`. I have phases the way the portfolio projects have phases: literate-config bootstrap; Org core; the GTD agenda; a student layer for Northern College course files; spaced repetition with `org-fc`; a typography pass with `mixed-pitch` and `org-modern` and `visual-fill-column`; the portfolio hub; a math layer with `cdlatex` and `org-fragtog` rendering LaTeX fragments in line at HiDPI; the Roam UX. Phase 13 is queued: GPG encryption on the per-month finance files. Phase 14 is `pdf-tools` and `org-noter`. The phases are deliberately not all shipped; the brain is permitted to grow when there is friction, and only then.

The typography is the part I would defend most strongly. TX-02 semi-light at 18pt for code; **Tiempos Text** at 20pt for prose; `mixed-pitch-mode` swaps the variable face into prose buffers while leaving code blocks, tables, and properties in monospace; `visual-fill-column` centers prose at ninety-five columns and toggles itself off when the window is too narrow; `org-appear` reveals emphasis markers only when the cursor is on them. The result, at full screen, is the closest a code editor has come to typesetting. The journal, the course notes, and this post were all written in it.

Every helper in the Doom config is namespaced under `+bdkl/`. The `+` is the Doom convention for user functions; `bdkl/` makes them mine; the `--` double-dash on private helpers signals *not a public command*. This is the same naming hygiene I would impose on Rust modules. Elisp permits global names; I would rather not take it up on the offer.

Custom keybindings live under `SPC X` as a personal leader. `SPC X R` is the *AI bundle builder*, a capture that gathers the current project's `spec.md`, `roadmap.md`, and a slice of the agenda into a clipboard-ready prompt. `SPC X H` opens the portfolio hub: an Org-rendered table of every project's version, tagline, last-commit, and language.

**Helix.** The third one, and the one I did not plan on. `hx` is what I reach for when the edit is fifteen seconds long and loading either of the other two is the expensive part: one line in a systemd unit, a typo in a config, a quick look at a file I do not intend to change. It needs no configuration to be useful, its selection-then-verb model is backwards from vim in a way that stops mattering after an afternoon, and it ships its own language-server wiring so there is no plugin layer to maintain. Having a deliberately disposable editor turned out to protect the other two: LazyVim stays uncustomised and Doom stays serious, because neither is being asked to also be the fast path.

<p class="ornament ornament--fleuron">❦</p>

## V. The Scripts in `~/.local/bin/`
{: #scripts}

`~/.local/bin/` holds a small set of hand-written zsh utilities that have absorbed the parts of system maintenance I no longer want to think about.

**`sys_maintain`.** Full-system update with an *eighteen-hour cooldown*. One invocation talks to DNF5, Flatpak (system and user), `fwupdmgr`, `pipx`, `rustup`, `uv` (self-update *and* tool-upgrade), `gem`, `cargo install-update`, `claude update`, `doom upgrade && doom sync`, then `sys_snapshot`, then autoremove, a `journalctl` vacuum, a DNF consistency check, and reboot detection. A clean run writes a Unix timestamp to `~/.local/state/sys-maintain-timestamp`; the next run reads it, refuses to do anything within eighteen hours, and prints, in colour, the exact `HH:MM:SS on Weekday, Month Day` at which the lock expires. `--force`, `--reset`, `--dry-run`. A SIGINT trap unwinds the sudo keepalive without setting the stamp, so an interrupted run is safe to repeat. Failures get collected and reported; the stamp is not written unless everything succeeded.

The reason for the cooldown is restraint. Without one I would run system updates four times a day, because checking is irresistible and a laptop gains nothing from it. The lockout is the part of the script I actually needed.

**`sys_snapshot`.** A content-aware snapshot of the laptop-specific bits that aren't in the dotfiles repo: `/etc/thinkfan.yaml`, `/etc/modprobe.d/thinkfan.conf`, a udev rule for power profiles, a systemd unit for battery-charge thresholds, `/etc/fstab`. Plus four generated manifests: DNF, Flatpak, `cargo install --list`, `uv tool list`. Each file copies to `~/.config/system-backup/` only if its content has changed; the previous version rotates to `.bak`. The whole directory is picked up by **borgmatic** in its hourly run.

This is the single most valuable script I have written for my own machine. A clean Fedora reinstall is now a one-evening exercise: clone the dotfiles bare repo, replay the four manifests, paste the snapshotted system files back, restore `~/org/` from borg. I learned to write this by getting it wrong twice.

**`update_calibre`, `update_hledger`, `update_gemini`, `update_zlib`, `update_bitwarden`.** Version-aware updaters, one each for a tool that doesn't ship through DNF or Flatpak on Fedora. Same shape every time: read local version, hit the canonical API (GitHub releases, npm), compare with `sort -V`, refuse to downgrade, gate on a `[y/N]`, download, install, clean up. None of them are clever. They are the kind of script you write once and leave alone for the rest of the laptop's life.

**`dotfile-sync`, `btrfs_health`, `borg-offsite`.** The maintenance tail. `dotfile-sync` commits tracked drift in the bare dotfiles repo and pointedly never adds untracked files, so a new config is always a deliberate `config add` rather than something that wandered in. `btrfs_health` checks the filesystem I chose partly for snapshots and would otherwise never think about again. `borg-offsite` pushes the encrypted repository somewhere that is not this laptop, which is the only part of a backup strategy that actually counts.

**`doom-mode` (in `.zshrc`).** Yamagi Quake 2, Hammer of Thyrion's Hexen 2, dhewm3, Ironwail Quake, uzdoom. The function turns *touchpad-disable-while-typing* **off** before launching (dodging Cyberdemon fire with a dead touchpad is its own punishment), then back **on** when the game exits. Six lines and a `case` block, and currently due a rewrite: the toggle still goes through `gsettings`, which Hyprland does not read, so the fix has been ceremonial since the move off GNOME.

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

`~/docs/` is one tree, three species. **`~/docs/Calibre Library/`** is the four-thousand-six-hundred-book SQLite library that anchors four of the portfolio projects. **`~/docs/papers/`** is a hand-organised archive in sixteen subtrees, by topic. **`~/docs/bdkl/`** is the Obsidian vault, which is the scratch journal rather than the second brain; the distinction is that anything in it which survives contact with a second week eventually gets promoted into `~/org/`. `doc_inventory` in `.zshrc` walks them; `update_docs` regenerates the Calibre catalogues into `~/docs/catalogs/` and snapshots the paper directory alongside them, and at 211 invocations it is the fourth-most-run command on this machine.

`~/org/` is *deliberately* not git-tracked. The finance files contain enough information about my actual life that the encryption phase is queued; until then, the privacy budget is *don't sync it, don't track it, let borgmatic carry the encrypted offsite copy*. Inside: `inbox.org`, the GTD project files, `roam/` for daily journals and concept notes, `courses/` for BCS flashcard decks, `finance/YYYY-MM.org` for per-month ledgers, and `reviews.org`.

`~/Tasks/` is Atrium's Org-mode round-trip target. `atrium-cli export org ~/Tasks` writes the live SQLite store out to plain text with UUIDs, CLOCK drawers, and TODO state preserved; `atrium-cli import org ~/Tasks` reads it back. If the round-trip stops being identical, the round-trip is wrong; the script that proves it is two lines.

`~/.dotfiles/` is the bare repo described in §II. Cloning to a fresh machine is `git clone --bare repo ~/.dotfiles && config checkout`, and nothing else.

<p class="ornament ornament--fleuron">❦</p>

## VII. The Languages
{: #the-languages}

In roughly the order it eats my week:

**Rust.** Atrium, Viaduct, Conservatory, and Colophon are all Rust. The reasons are the boring ones: compile-time invariants beat code review, sum types beat status enums, `Result<T, E>` beats throwing, `cargo` beats every other build tool I have used. The reason that doesn't get said often enough is that Rust forces the architectural conversation to happen before the code does, and you cannot hide a lifetime bug behind a runtime cast. The single-writer SQLite worker, the read-only connection pool, the `Send + Sync` boundary on a tokio handler: these are not conventions, they are load-bearing types. I am not as fast in Rust as I am in Python yet, though I am closer than I was a year ago, and the compiler keeps catching a class of mistake Python would have let me ship.

**C.** Framework is C, for the same reason `mupdf`, `cairo`, and `gtk4` are C: no FFI tax, no glue-language tax, the binding surface is the bare metal. K&R is the most important book I have read.

**Python.** Hermitage is Python because GTK4 via PyGObject is a perfectly serviceable native-desktop story. CalibreQuarry is Python, stdlib-only, because the constraint *forced* me to write a real recursive-descent parser instead of pulling in `lark` and waving. I love Python the way I would love a well-worn pair of work boots: type hints throughout, `from __future__ import annotations`, `dataclasses` over namedtuples, `pathlib` over string paths, `argparse` over `click` until `click` is justified. The standard library is enormous, and most people writing Python never finish reading it.

**Ruby.** A language I keep trying to graduate from *liking* to *using*. `rbenv` is installed; 3.4.8 is the current version. Sandi Metz's *Practical Object-Oriented Design* is the book of hers I most often re-shelve at the front. I am still waiting for the project that wants to be Ruby: a small Sinatra service, a Thor CLI, a static-site engine.

**C++.** I write more C++ than I admit. The version that wants my attention is the one Scott Meyers writes about: C++17 with `-Wall -Wpedantic`, not C++26.

**Java.** School. The Computer Engineering Technician program at Northern College is Java-first; `jdtls` in LazyVim and the `(java +lsp +dap)` layer in Doom carry the coursework. Java is a more honest language than its 2000s reputation gives it credit for, and the JVM is, separately, a remarkable piece of engineering. I will not be writing Atrium in it. I am also no longer rolling my eyes when someone else reaches for it.

Languages I am studying deeper into:

* **Zig.** A smaller language than Rust, no hidden allocations, `comptime` as a first-class metaprogramming surface, and the most readable system-language standard library I have ever browsed. The 1.0 release is not here yet; the language is real now anyway.
* **Go.** Fast compilation, concurrency primitives that do what they say, a standard library that does almost everything anyone would ask of it. The language I would write a small backend service in if I had one to write.
* **OCaml.** Probably the one I am most curious about. The MirageOS work, the Jane Street functional-programming tradition, the type system that quietly handles what Haskell handles loudly. If I ever sit down with the compilers project I have been mentally drafting since the Calibre search parser, the front end is going to be OCaml.
* **Common Lisp.** For the same reason a chef should be able to butcher a chicken. I am not going to write production CL; I would like to be able to *read* it, including SBCL itself.
* **Erlang/Elixir.** The most beautiful concurrency story in the field and one I have never lived inside. Armstrong's thesis is on the shelf.

None of these are on the list for hiring. They are on the list because the field has more good ideas in it than one career can absorb.

<p class="ornament ornament--fleuron">❦</p>

## VIII. What the History Shows
{: #atuin-confessional}

Atuin keeps everything. Seventeen thousand two hundred and eight commands in the local index across three thousand six hundred and eighty-eight unique ones, ranked by recency, fully searchable. The interesting question a year of full history can answer, more usefully than a wishful inventory, is *which tools actually do the work?*

Strip the navigation noise (`ls` at 4,197, `cd` at 2,571, `exit` at 2,259, `v` for `nvim` at 510) and the most-typed program on this machine is `claude`, at eight hundred and ninety-two invocations. That is not the answer I expected to publish. It is roughly one and a half times `cat` and more than double `rm`, and it means the single thing I reach for most in a working day is the assistant described in the previous post's §X. I have decided to report that rather than quietly omit it, because a *What I Use* that launders its own history is worth nothing.

Behind those: `cat` at 583, `rm` at 389, then `nano` at 294. I am not, it turns out, the curated minimalist I sometimes pretend to be on the internet; I am a person who copies-and-deletes-and-cats a great deal of files.

`nano` surviving at 294 is the more interesting confession, because I now have Helix installed for exactly the fifteen-second edit `nano` was covering, and the muscle memory has not moved. `nano` is, on its own merits, a good piece of software. It does one thing, it tells you how to do that thing at the bottom of the screen, and it does not impose a mode model on a config change that doesn't deserve one. Installing a better tool does not uninstall a habit; that takes its own separate effort, and I have not made it yet.

Two of my own scripts crack the top ten: `update_docs` at 211 and `sys_maintain` at 197. A script that makes the top ten of your own shell history has justified itself and does not need defending again.

The artifact I am most pleased by is a one-off test file: `echo "phase 13" > /tmp/test.txt`, followed by a successful `gpg --encrypt`. The first end-to-end rehearsal of the Doom finance-encryption phase. The phase still isn't shipped. That is how the *brain* changes shape: a queued idea, a one-evening proof, and then a wait until the moment is right to roll the rest of the work in behind it.

<p class="ornament ornament--asterism">⁂</p>

None of this is really about the configs. There is a small, stable surface of tools and conventions here that I keep iterating against, and the iteration is where most of the value has been. My `.zshrc` gains about one alias a quarter and loses one a quarter, which feels like the right rate. `~/.local/bin/` has five scripts in it, and I would rather it never had fifty, because the day it does is the day I stop knowing what is in it.

That is the workshop I am trying to keep: a small room with the right tools at hand.
