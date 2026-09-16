---
layout: codex
title: "vir-gtk"
codex_num: "No. 030"
description: "A standalone Rust library extracting the shared GTK4 styling and D-Bus portal interaction layer for the VirInvictus desktop suite."
permalink: /codex/vir-gtk/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> gio <span class="stack-sep">·</span> <span class="status">active · v1.4.2</span></p>

A standalone Rust library extracting the shared GTK4 styling and D-Bus portal interaction layer for the VirInvictus desktop suite.

`vir-gtk` provides the foundational visual identity for **[Atrium](/codex/atrium/)**, **[Conservatory](/codex/conservatory/)**, and **[Viaduct](/codex/viaduct/)**. It replaces `libadwaita` with a bespoke flat Kanagawa-themed framework.

The library handles `org.freedesktop.portal.Settings` DBus resolution for system color schemes, providing dynamic dark mode integration. It also bakes in Kanagawa DRAGON and LOTUS hex palettes, injecting token-replacement CSS and GTK 4.16+ custom property blocks directly into consuming applications.

<p class="codex-link"><a href="https://github.com/VirInvictus/vir-gtk">github.com/VirInvictus/vir-gtk →</a></p>
