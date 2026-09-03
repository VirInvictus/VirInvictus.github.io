---
layout: codex
title: "raindrop-cli"
codex_num: "No. 025"
description: "Talks to the Raindrop.io bookmarking service with nothing from PyPI, built the way the other stdlib tools here are: urllib, json, argparse, tomllib."
permalink: /codex/raindrop-cli/
---

<p class="codex-meta">Python (stdlib only) <span class="stack-sep">·</span> <span class="status">active · v0.4.0</span></p>

<div class="codex-plate">
  <img src="{{ '/assets/img/raindrop-cli-list.webp' | relative_url }}" alt="raindrop-cli listing a collection: bookmark ids, titles, and URLs in designed ANSI colour, followed by account stats" loading="lazy">
</div>

Talks to the [Raindrop.io](https://raindrop.io/) bookmarking service with nothing from PyPI, built the way the other stdlib tools here are: `urllib`, `json`, `argparse`, `tomllib`. It covers the REST API a single user actually touches: raindrops, collections, tags, and highlights, plus the account endpoints (user, stats, filters, import-dedup, export, backups). Every command speaks two languages, designed ANSI for a human at a terminal and `--json` for scripts and agents, so the one binary is both a daily driver and an automation surface.

The whole client funnels through a single `_request` method: it attaches auth, applies a timeout, lowercases the boolean query params the API rejects otherwise, retries `429` and `5xx` with bounded backoff (honoring `Retry-After`), and maps every failure to a typed exception carrying the API's own message. The bulk verbs are grounded in an empirically verified quirk of Raindrop's batch endpoints, that they only touch raindrops actually in the path collection, so a naive id-based batch move silently no-ops; raindrop-cli loops the single-item endpoints for explicit id-lists and reserves the batch calls for `--from` collection scope, and a global `--dry-run` logs the method and payload of every write without making the call. A pytest suite drives the client against a fake `urllib` transport, so the tests need no network.

Since v0.2.0 it speaks a second service too: a `PinboardClient` sibling and an `rd pinboard` command group, honest to [Pinboard](https://pinboard.in)'s flat model (bookmarks keyed by URL, no collections, `toread`/`shared` flags, notes) with a paced client for Pinboard's strict rate limit. v0.3.0 adds `rd sync`, a two-way additive Raindrop and Pinboard sync that matches on a normalized URL (its dedup key), never deletes, and bridges the model gap reversibly in tags, with direction and collection/tag scoping so it converges what you choose rather than unioning everything by force.

v0.4.0 fixed the one place the safety story was thin. `--dry-run` only helps if you remember to type it first, so destructive operations now confirm, gated on blast radius rather than on every write: scope mode on `rm`, `mv`, and `tag --clear`, where `--from` can match any number of raindrops and the prompt counts them before naming the number; and the irreversible verbs, `rm --permanent`, `empty-trash`, `tags rm`, and deleting a collection, which takes its contents with it. Removing a single id to Trash is recoverable and is not prompted, because a guard that fires on everything is a guard people learn to click through. `-y` and `RD_ASSUME_YES=1` are there for cron. The release also adds `rd open`, which will fetch the archived permanent copy instead of the live link by asking for the `307` with redirects suppressed and reading `Location` rather than following it, reporting a missing archive plainly instead of opening the wrong thing.

<p class="codex-link"><a href="https://github.com/VirInvictus/raindrop-cli">github.com/VirInvictus/raindrop-cli →</a></p>
