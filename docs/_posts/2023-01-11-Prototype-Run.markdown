---
layout: post
title: "A hand-routed full dialogue run (Roadblock%)"
date: 2023-01-10 14:13:00 -0700
categories: Development Brainstorming
---

I thought a sample route for the town of Onett only would be a "significant example" that would help me to:

- Get a handle on degree of complexity for this run
- Better understand "what is to be done"
- Make a contribution that doesn't involve reading or coding

Returning to the (revised, as promised) definition from the previous post:

> A full dialogue run of Earthbound (100%) is a run which reaches all NPC dialogue normally accessible in the course of a glitchless run of the game. This requirement is inclusive of branching dialogue trees and includes NPC, descriptive, item, and environmental text. It is exclusive of unreachable dialogue and does not include battle text. The debug menu may not be used.

We can slightly modify it for a "Roadblock%" all-dialogue run

> A full dialogue run of Earthbound (Roadblock%) is a run which reaches all dialogue normally accessible up till the point when Captain Strong clears the roadblock from Onett to Twoson. This requirement is inclusive of branching dialogue trees and includes NPC, descriptive, item, and environmental text. It is exclusive of unreachable dialogue and does not include battle text. The debug menu may not be used.

I like this as a sample. It is substantive and begins to hint at the complexity of the full run, since there are a number of NPCs who change what they say many times even in the course of the initial section of this game, as well as one exclusive branch (whether you take King or not). A quirk of "Roadblock%" is the runner must purchase the house in Onett, but I may omit this requirement if it is tedious.

The strategy I will use to build this route is as follows:

- List all NPCs in the scope of the run (here, every NPC in Onett and its interiors)
- Using the decompiled script, annotate which NPCs change their dialogue and under which conditions to create a list of required "NPC encounters"
- Create a route for each NPC encounter based on distance and event flags
-- This is accomplished manually for the "Roadblock%" run but could doubtless be optimized by hand or programmatically.
- Certain NPCs have highly variable/branched text, and several of them are located in Onett. These will need to be routed especially carefully so as not to omit obscure dialogue.