---
layout: post
title: "Milestone Update: Onett Routed"
date: 2023-02-03 13:16:00 -0700
categories: Discussion
---
OVERVIEW

I've been hard at work on the route for my 100% Dialogue run of Earthbound. The thing I am thinking a lot about right now is validation. But, because I haven't written in a while, perhaps it's warranted to provide a general overview of how I'm creating this thing.

THE ROUTE

At this time, I'm building the route step-by-step in an Excel workbook (will be Google once I'm settled on the format).  The "Flags" tab is the meat of the run and includes the following fields:

* Spacer. Helper row for expanding/contracting the table
* Subsegment. Pretty arbitrary right now, just provides a general label for navigating through the steps.
* Type. The type of action to be taken. Values include
  * Talk. Talk to a human/animal/phone NPC.
  * Check. Check an inanimate NPC.
  * Route. Travel to the specified location.
  * Action. A special action not specified above.
  * Flag. Special field: these rows split the run into sections based on when a dialog-relevant event flag is set or unset.
* Description. A description of the action to be taken.
  * Check and Talk. The text label I've chosen for a given NPC sprite.
  * Route. The name of the destination to be routed to.
  * Action. A description of the action to be taken.
  * Flag. The name (courtesy CataLatas) of the event flag being set or unset.
* NPC ID. For actions referring to an NPC, this is the four-digit NPC ID specified in "npc_config_table" (CoilSnake 4.1). For other actions, this field is blank.

The rest of the fields are more-or-less unused due to laziness or lack of necessity.

* Tile X,Y. Currently unused due to laziness. This should specify the tile (the unit of distance EB Project Manager uses) of the target of the action.
* NPC Condition(s). Additional requirements that must be true of the target NPC for the sepcified action.
* Gamestate Condition(s). Additional requirements that must be true of the party, inventory, or other aspects of the game state besides flags.
* Flag Condition(s). Additional game flags that must be set or unset in order for the action to have the intended outcome.

A second table, "Gamestates", uses the same fields but instead collects actions that must be taken when a certain condition is true (e.g., "Ness is dead"). The intent would be to layer these into the main route in an optimized way once the latter is nominally complete.

SUPPORTING MATERIALS

I could stand to be more intentional about this, but I've begun creating a number of supporting materials and tools in addition to the "dialog flattener" Python script itself.

* InDesign spreads of towns. As you may know, the game world of "EarthBound" is stored as a single very large (XxYpx) map. Unfortunately, this means that inside spaces (buildings, caves, etc.) are often located at some distance from the overworld doors used to access them. To solve this problem, I have been using Photoshop and InDesign to slice up a screenshot of the game map with NPCs visible (EB Project Editor) and assemble those in a large InDesign spread. I have no idea if this is an efficient approach, but these are tools I know -- I'm quick with the Pen tool and InDesign supports the nested layering to keep the large format (XxYpx) design orderly and reference-able. Currently Onett is done and Twoson is under construction.

* Sprite names. Because the route is intended to be used in real time, I thought it was helpful to give the sprites names. This is rather arbitrary right now but I'd love to formalize a nomenclature, probably some combination of color, clothing, age, and/or gender.

METHODOLOGY

To construct the route, I am basically following the process laid out in my previous posts: play through the game "as normal" and route each NPC in the order they are encountered. Therefore, at this time all NPCs accessible prior to the setting of the "ROAD_TO_TWOSON_OPEN" flag have been completely routed.

This means they are routed for the initial encounter in Onett, as well as any future encounters that may be required. Efficiently arranging these visits in trips back and forth across the world will make up the bulk of the challenge of run optimization.

VALIDATION

It occurs to me that I should come up with a reproducible way of validating that all the dialog in the game is in fact visited in the course of the route as written. The best way I've found to do this is manual. But that is really bad. I wonder if it would be possible to write a Lua script that helps. perhaps:

* Write to a log file whenever a ROM address containing dialog is loaded into memory and subsequently read from RAM
* Intercept the characters being output on the screen and write them to a file for finding/matching against a complete dialog dump. Unmatched areas can be defined as omitted from the run requirements (unreachable dialog, etc.)

Clearly I have some learning to do about the SNES and EarthBound in order to make this a reality. I am going to keep plugging away at the route and trust that tracking the NPC IDs will be of basic service to me for this project in the future.

TODO

The Python script needs to be revised to more efficiently deal with infintely nested dialog: currently "dereference_all_dialog()" simply recurses until a specified "max_depth" level of function calls is reached. This both misses deep original dialog and incorporates a large amount of repetitive dialog for certain NPCs.



