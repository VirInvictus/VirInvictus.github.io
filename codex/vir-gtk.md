---
layout: codex
image: /assets/img/og-card.png
title: "vir-gtk"
description: "A standalone Rust library extracting the shared GTK4 styling and D-Bus portal interaction layer for the VirInvictus desktop suite."
permalink: /codex/vir-gtk/
---

<p class="codex-meta">Rust <span class="stack-sep">·</span> GTK4 <span class="stack-sep">·</span> gio <span class="stack-sep">·</span> <span class="status status--complete">complete · v1.4.3</span></p>

A standalone Rust library extracting the shared GTK4 styling and D-Bus portal interaction layer for the VirInvictus desktop suite.

The collection's GTK4 apps share one visual identity, and this is the library that carries it: the shared Kanagawa Dragon stylesheet and desktop-portal plumbing behind **[Atrium](/codex/atrium/)**, **[Conservatory](/codex/conservatory/)**, **[Viaduct](/codex/viaduct/)**, and **[Quire](/codex/quire/)**, with `libadwaita` removed in favour of a flat Kanagawa theme the library itself owns.

Portal interaction is the other half: `vir-gtk` resolves `org.freedesktop.portal.Settings` over D-Bus so applications follow the system's dark/light preference, and it ships the Kanagawa Dragon and Lotus palettes as token-replacement CSS and GTK 4.16+ custom property blocks inside the applications that consume it.

<p class="codex-link"><a href="https://github.com/VirInvictus/vir-gtk">github.com/VirInvictus/vir-gtk →</a></p>
