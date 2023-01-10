---
layout: post
title: "What does 'all dialogue' mean?"
date: 2023-01-10 14:13:00 -0700
categories: Development Brainstorming
---
The word "script" is slightly ambiguous when discussing the dialogue in Earthbound. That is because the game text incorporates control codes for a scripting language, CCScript, which allows the text of the game to branch and change according to many factors, a few of which include:

- Event flags
- Party constitution
	- Who's joined
	- Who's alive/dead
- Inventory composition
	- Has key item
	- Is full

And so on. We might say Earthbound's script is also a script. CCScript can also affect the game state by playing sounds, setting/unsetting event flags, teleporting the party, manipulating characters' inventories, and much else. The presence of branching and conditional dialogue is particularly important as it provides the primary complexity of the "100% Dialogue Run" which this project is intended to facilitate. The term "100% Dialogue Run" is ambiguous. Some initial questions to be answered include:

- What is "dialogue"?
	- NPC text
	- Descriptive and item text
	- Battle text
	- Environmental text (e.g., "Do you really think this looks like a pencil?" ($C68F74))
- What is "100%"?
	- Display all text in the script file
	- Display all text NPCs are capable of saying
		- Including/excluding mutually exclusive branches (e.g. the woman in Onett whose text changes after defeating Giygas based on whether the player spoke to her multiple times ($C76449))
		- Including/excluding unreachable dialogue ("Message of the broken SkyWalker" ($C8F748))
- What is a "run"?
	- Is this a speedrun?
	- Is it a TAS?

Those are very basic questions that will be elaborated and changed as the project develops. For the moment, I'm going to use the following definition for this run in order to guide initial planning and brainstorming work:

> A 100% dialogue run of Earthbound is a run in which all normally-accessible NPC dialogue is displayed in the course of the run. This requirement is inclusive of mutually exclusive branching dialogue but exclusive of unreachable dialogue, and dialogue from other sources (e.g. descriptive, item, battle, and environmental text). The debug menu may not be used.