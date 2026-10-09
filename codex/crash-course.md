---
layout: codex
image: /assets/img/og-card.png
title: "crash-course"
description: "An arcade aircraft-crash damage-maximizer: line up a failing airliner on the densest target and turn one bad flight into the biggest damage total."
permalink: /codex/crash-course/
---

<p class="codex-meta">Godot 4.7 <span class="stack-sep">·</span> GDScript <span class="stack-sep">·</span> <span class="status">active · v0.18.0</span></p>

An arcade aircraft-crash damage-maximizer: line up a failing airliner on the densest target you can find, commit past the point of no return, and turn one bad flight into the biggest damage total you can. Buildings, traffic, parked planes, a whole city waiting at the end of the approach: Burnout's crash mode, rebuilt around aircraft.

The whole map is the target. The current testbed spans a full city: 1,500+ breakable buildings packed six to a block, seeded in position and rotation, heights from 13 m shops to 106 m supertalls, so a seed replays the same skyline and a new seed builds a new one. The fracture sets are authored offline by a deterministic BSP-slice export for headless Blender; at runtime damage progressively removes real mesh pieces under convex hulls, chunk-sized because Jolt rejects the near-degenerate hulls sliver fracture produces. Six mayday scenarios (the crash-cause directors) fly committed takes into the field.

Under it: a rate-targeted arcade flight model on Jolt, a category-scored combo engine, aftertouch and a crash-cam, traffic and crowds, an economy with the Hangar, a logbook of achievements and missions, and a humor layer that files every wreck as a Courier headline and an itemized insurance claim. Verification is headless: sixteen Godot suites and an autopilot fixture that flies and records the demo runs by itself. Fourteen of twenty-four phases are flown: through the airport, with the full-map city testbed under everything, and the fleet is in, seven airframes from the starter 747 to a paper-hulled aerobatic single, each flying on its own mass and handling data.

<p class="codex-link">private, in development</p>
