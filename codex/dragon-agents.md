---
layout: codex
image: /assets/img/og-card.png
title: "dragon-agents"
description: "A local ZCode plugin of sixteen read-only research subagents: they gather and report, the main thread decides and edits."
permalink: /codex/dragon-agents/
---

<p class="codex-meta">Markdown <span class="stack-sep">·</span> Python (stdlib) <span class="stack-sep">·</span> <span class="status">active · v0.2.1</span></p>

The research half of the agent workflow, packaged. dragon-agents is a local plugin for the ZCode agent client: sixteen subagents, each restricted to Read and Bash, each forbidden from writing files, committing, or spawning subagents of its own. They gather and report; the main thread decides and edits. The point is keeping the writing where it can be watched while the reading scales.

- **repo-cartographer**: a structured repo map (layout, stack, conventions, tests, risk areas) before planning sessions.
- **doc-drift-auditor**: standard-layout docs versus code reality: VERSION sync, roadmap boxes, spec claims, patchnotes hygiene.
- **cascade-checker**: a downstream call-site inventory for a changed shared-library API, with per-repo breakage risk.
- **spec-compliance-reviewer**: a diff against the `spec.md` contract; violations and unaddressed claims with `path:line` evidence.
- **ci-triage**: a failed CI run reduced to root cause, decisive log lines, and fix direction.
- **slop-reader**: a fresh-eyes AI-prose pass on commissioned docs; it flags quotes and never rewrites.

The v0.2.0 wave added ten more: **release-auditor** (pre-tag readiness checks and post-tag sweeps), **workspace-sentinel** (a one-dispatch status sweep across every repo in the workspace), **ci-posture-auditor** (workflows graded against the house-hardened CI shape), **debt-census** (TODO/FIXME markers dated by blame into a cleanup worklist), **code-reviewer** (bug-hunting over a diff), **git-archaeologist** (regression windows and provenance from history), **claim-verifier** (independent re-verification of a findings list), **dependency-auditor** (declared versus imported dependencies, version floors versus the APIs actually used), **test-gap-analyst** (static test-coverage maps), and **duplication-scout** (cross-repo duplicate candidates feeding library-graduation decisions).

A stdlib-only structure validator (both manifests plus every agent charter: frontmatter fields, `tools: [Read, Bash]` only, the read-only and no-subagent charter lines, and the sixteen-agent roster) runs in CI on every push, and the repo documents the proven plugin refresh procedure end to end. Built for personal use; installed through a directory marketplace.

<p class="codex-link"><a href="https://github.com/VirInvictus/dragon-agents">github.com/VirInvictus/dragon-agents →</a></p>
