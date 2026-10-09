---
layout: codex
image: /assets/img/og-card.png
title: "saforums.koplugin"
description: "Read the Something Awful Forums on an e-ink reader: a KOReader plugin for lurkers, built on a screen-scraping contract and native widgets."
permalink: /codex/saforums/
---

<p class="codex-meta">Lua <span class="stack-sep">·</span> KOReader <span class="stack-sep">·</span> <span class="status">active · v0.2.0</span></p>

Read the Something Awful Forums on an e-ink reader. A KOReader plugin built for the lurker's loop: log in once with persisted session cookies (or import a desktop browser's), browse the forum index and a bookmark shelf with unread counts, and continue any bookmarked thread at the first unseen post. Holding a bookmark marks the thread unread again. Posting stays on the phone by design; this is a reading client, and nothing it does clutters the reading history.

Everything renders through KOReader's own widgets in the app: no HTML engine, no generated files, nothing to clean up. The look is a grayscale port of Awful.app's posts-view theme, translated for e-ink: bordered post cards, avatars cached per user, seen tinting where white means new, and the end-of-thread frog.

The site has no API, so the plugin screen-scrapes by contract. Endpoints, parameter names, and HTML structure are written down in `spec.md` as facts and covered by tests against synthetic fixtures, so no real forum content ever enters the repository. The scraper is read-only and polite: a session at human pace, threads marked read only when explicitly continued, and an honest User-Agent. Device-verified end to end on a Kindle Oasis and in the KOReader emulator. AGPL-3.0.

<p class="codex-link"><a href="https://github.com/VirInvictus/saforums.koplugin">github.com/VirInvictus/saforums.koplugin →</a></p>
