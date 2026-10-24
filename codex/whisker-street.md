---
layout: codex
image: /assets/img/og-card.png
title: "whisker-street"
description: "A Discord stock market where the members are the stocks: presence-driven prices, a brokerage ledger, and a market built to be boring to exploit."
permalink: /codex/whisker-street/
---

<p class="codex-meta">Python <span class="stack-sep">·</span> discord.py <span class="stack-sep">·</span> aiosqlite <span class="stack-sep">·</span> <span class="status">active · v0.6.2</span></p>

A Discord stock market where the server members are the stocks. Every member gets a ticker and their price moves with real presence: time in voice channels and chat activity, not raw message spam. Everyone else buys and sells them, settling against a brokerage ledger that can be funded from an external economy bot's currency.

The genre exists: Empire Avenue ran "invest in your friends" from 2010 to 2024, and a handful of Discord bots do members-as-stocks today. Every prior implementation stops at flat IPO prices and one-way pricing math with no defense against pumping your own stock. Whisker Street exists for the parts nobody did: activity-anchored prices with slippage, a funded house market maker, and a brokerage edge that makes inflating the host economy mathematically impossible. The whole design bends to one rule: **the market must be boring to exploit.**

The market is a headless, tick-driven engine with no Discord in it at all: pure Python over an injectable clock, so the whole thing unit-tests and fast-forwards without a connection, and prices come from an expectations model over each member's daily usage series (observation-day aware) rather than a raw activity counter. The Discord shell wraps it with the full v1 command surface, runtime env validation, fail-fast database init, and soft-fail cog loading. For testing, accelerated time is a command: `/simulate advance` runs the live market's weeks in minutes on a scratch server, and `docs/ops.md` is the runbook.

v0.6.2 is the proof of concept, hardened for handoff: durable race-free trades, locked settlement sweeps, atomic migrations, and an own-review pass that ran four agents over the whole tree. Phases 4-7 (shorting, futures, the consent-gated gold bridge to the host economy, and the hardening tail) come after the proof of concept. Invariant property tests cover the brokerage math.

<p class="codex-link"><a href="https://github.com/VirInvictus/whisker-street">github.com/VirInvictus/whisker-street →</a></p>
