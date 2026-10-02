---
layout: post
image: /assets/img/og-card.png
title: "The Homestead"
date: 2026-10-02
description: Off the American cloud. Google Drive to a Hetzner Storage Box, the AI subscriptions to GLM, and the household media stack to a home server.
---

<div markdown="1" class="dropcap">
The push that started all of this was a backup that kept failing. My offsite borg repository syncs through rclone, and against Google Drive the sync kept tripping per-request quotas: a ceiling on how many times a program may touch the thing it pays to store, enforced by a company whose product was never storage. The line still sits in the script that does the push, comparing Drive's quotas to the Hetzner Storage Box that replaced it, a box with no such ceiling because its whole business is the bytes. A backup that fails on a stranger's arithmetic is not an offsite copy. It is a lease on my own history, revocable. This post is the accounting of a summer spent cancelling leases.
</div>

## I. The Teachers
{: #the-teachers}

I came to the exit slowly, and two shutdowns did the teaching. Mint's death taught the first lesson, and [What I Use](/2026/07/23/what-i-use.html) already records it: never build a decade of records on top of a free product with a roadmap. The second lesson was colder. Claude Fable was the tier above everything, the best model I could reach, and the United States government leaned on Anthropic until access to it closed; I dropped back a tier to Opus and wrote the sequence down in that post's §X at the time. I paid for the frontier and the frontier was moved.

That is the whole ideology, such as it is. Not privacy paranoia, not prepping, not politics as identity. Dependency accounting: list what the household leans on, ask who can change the terms, and move the load-bearing ones. What follows is the list, and the moves.

<p class="ornament ornament--fleuron">❦</p>

## II. The Storage
{: #the-storage}

Google Drive's replacement is a Hetzner Storage Box in Falkenstein, the cheapest honest product in this whole story: a German company sells a slab of storage on German iron, and the relationship begins and ends at the invoice. No app layer riding on it and no terms that reorganize themselves. The borg repository mirrors there through rclone, and the per-request ceiling that killed the Drive sync simply does not exist, because bytes on a Storage Box are the product rather than the bait.

The books ride the same box. The library's binaries mirror to a Books directory beside the repository, versioned nowhere and duplicated deliberately: borg carries the metadata with everything else, and the book files ride a plain mirror instead, which is the right split for gigabytes that never change. Local disk, then Falkenstein, and no advertising business anywhere in the chain.

<p class="ornament ornament--fleuron">❦</p>

## III. The Home Box
{: #the-home-box}

The services came home. A box on the house network, *rinpc* by hostname, now runs the household's small fleet: **Immich** for photographs, **paperless-ngx** for documents and paper, **komga** for comics and serialized books, **Jellyfin** for film and television, **audiobookshelf** for audiobooks and podcasts. None of it lives on the laptop. The laptop keeps its day job, and its whole involvement is client-side: the Jellyfin desktop, an mpv shim, a browser tab where a tab is honest.

The pattern repeats five times over. A category of family data that used to imply a cloud account now implies a directory on a machine whose failure mode is a hardware order, not a policy change. Immich takes the photographs: an app on the phone, the archive on the box, the timeline in between. paperless-ngx takes the paper: scan it once, OCR it, file it by correspondent and tag, and the filing cabinet becomes a search box. komga takes the comics and the serialized shelves, and it speaks OPDS, the protocol KOReader on the Kindle already understands, so the shelf is browsable from the reader itself. Jellyfin takes the film and plays it wherever a screen is, without asking anyone's account server for permission. audiobookshelf takes the audiobooks and podcasts and keeps the listening position synced to whatever is in hand, and the music stays with Conservatory, my own.

The fleet is boring on purpose. Five ordinary open-source projects doing exactly what their home pages promise, on one ordinary machine, backed up to the box in Falkenstein with everything else.

<p class="ornament ornament--fleuron">❦</p>

## IV. The Ledger
{: #the-ledger}

The AI line item moved for the same reason the storage did, on a different axis. My working stack is GLM end to end: the ZCode client on this machine, GLM models behind it, nothing else subscribed and nothing else installed. I want to be precise about the judgment underneath, because it is not that the American frontier fell off. Fable and Opus are still, in my estimation, the best models being made. The arithmetic changed instead: GLM's price-to-quality crossed the line where paying a premium for the name stops being defensible, and a household that keeps its books in hledger does not carry a line item out of brand loyalty. What I Use's postscripts carry the client switch; this carries the reason.

The phone is the footnote. The dock slot that held Claude holds Gemini today, riding a student Pro account that lapses in November; when it does, the plan is probably ChatGPT, chosen for the way it chats. The pocket model is a consumer purchase, rotated on price and temperament, and it owes the household nothing. The working stack is the dependency, and the dependency now has exactly one supplier, held to the same arithmetic as everything else in this post. The previous entry on this site is the same ledger from the other side, [what I will not sell](/2026/10/02/the-arithmetic-of-enough.html); this one is what I will not rent.

<p class="ornament ornament--asterism">⁂</p>

What still rents: the laptop runs Fedora, an American distribution; the phone is Apple's; the code lives on GitHub, and this page is served by GitHub Pages, which means a post about leaving the American cloud is being delivered by it, an irony I can live with because I have priced it. Purity was never the goal. The goal was that the load-bearing things, the books, the photographs, the paper, the backups, the model I work beside all day, sit on iron I control or on iron rented from companies whose product is iron. The homestead is partial and will stay partial. It is also, for the first time in years, mine where it counts.
