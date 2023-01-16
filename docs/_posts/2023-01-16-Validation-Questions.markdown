---
layout: post
title: "The problem of validation"
date: 2023-01-16 12:52:00 -0700
categories: Development Brainstorming
---

First of all, a newly-revised definition for the "All dialog Run":

> A full dialog run of Earthbound is a run which accesses all game text that can be reached by the player in the course of normal (glitchless) play by use of the "Talk", "Check", "Use", and "Help!" commands. This requirement includes branching dialog, including exclusive branches that may require restarts or multiple saves, but excludes unreachable dialog and battle text.
>
> NB: For simplicity I will refer to all overworld entities which respond to "Talk", "Check", and/or "Use" as "NPCs" as they are all defined in the same configuration file and can be treated uniformly for the purpose of this run.

This definition sadly excludes some very funny writing which appears only in battle (e.g., "Jeff used the Protractor! Now, he can fairly easily figure out the angle of various things"), but is a necessary exclusion due to the large amount of variable and conditional text that can occur in battle.

I began routing the "Roadblock%" run with a pretty naive approach:

> Begin a new game. As you encounter each NPC look up their dialog options and attempt to reach them all.

The problems with this approach surface almost immediately. Tracy and Mom have the most complex behavior of any NPCs in the game; each have large amounts of dialog that can only be accessed at later points in the game. This illustrates the need for a smarter approach.

Consider that Earthbound has a timeline demarcated not by seconds but rather by a series of game states (discrete combinations of event flags, party composition, and inventory composition). As the player takes actions in the game, the game state changes such that certain NPCs and dialog become accessible or inaccessible.

For example, at the start of a new game, the game state is such that the dozen or so NPCs present in upper Onett at nighttime are accessible. By day break, the flags will have been updated such that:

- Some NPCs become inaccessible (e.g., the cops dotting the path up to the meteor)
- Some NPCs become accessible (e.g., the NPCs in downtown Onett)
- Some NPCs' dialog changes if they had branches dependent on any of the updated flags

Therefore, for any given game state, it is possible to:

- Construct a list of accessible NPCs and "Check"able objects
- Determine the travel distance from the player character (PC)
- Determine if the accessible NPCs have any dialog that is responsive to the current flag, party, and inventory state

From these premises we can derive an improved routing strategy. Specifically, this algorithm generates a descriptive sequence of player actions that will constitute the run ("the route"):

1. Begin a new game
2. Based on the current game state, compile a table of accessible NPCs and ALL possible dialog for each
3. For each NPC not yet documented, add one or more actions to the route sequence depending on conditional and branching dialog. Actions may include
	1. Travel to location
	2. Interact with NPC
	3. Choose a specific dialog option
	4. Alter party state
		1. Allow one or more characters to die
		2. Revive one or more characters at the hospital
		3. Inflict a status ailment on one or more characters
	5. Alter inventory composition
		1. Fill inventory to capacity
		2. Partially empty inventory
		3. Completely empty inventory
		4. Add or remove key items from inventory
	6. Advance the plot (set/unset certain flags through gameplay)
	7. Handle exclusive branches
		1. Save game, reset, and copy save
		2. Reset and load copied save
4. Execute the actions in the route sequence until the game state changes such that new NPCs become accessible, then go to step 2

The route generated in this way should be complete but may be highly inefficient. E.g., this route will prescribe filling one's inventory each time an NPC will give a party member an item, when it may be the case that several of these interactions could be grouped later in the game. The sequence of actions is also not dependent on distance or travel time (though one may apply some basic optimization on this front when developing the route). I hold with Donald Knuth that "premature optimization is the root of all evil" and will consider completion of the route to be my first goal.

PS -- the route file should include these fields:

- Step Number
- Required Flag
- Required Party State
- Required Inventory State
- Action
- Location
- NPC ID
- NPC Label
- Effect on Game State

This should be sufficient to describe a given action unambiguously, while the inclusion of flags and IDs should support more efficient and programmatic methods of route development and optimization in the future.