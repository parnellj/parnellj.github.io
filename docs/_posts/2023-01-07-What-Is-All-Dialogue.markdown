---
layout: post
title: "What does 'all dialogue' mean?"
date: 2023-01-09 16:06:00 -0700
categories: Development Brainstorming
---
The word "script" is slightly ambiguous when discussing the dialogue in Earthbound. That is because the game text incorporates control codes for a scripting language, CCScript, which allows the text of the game to branch and change according to many factors, a few of which include:

- Event flags
- Party constitution
-- Who's joined
-- Who's alive/dead
- Inventory composition
-- Has key item
-- Is full

And so on. We might say Earthbound's script is also a script. Unsurprisingly this increases the degree of complexity of the "100% Dialogue Run" which I am developing this project to facilitate. Some initial questions to be answered include:

- What is "dialogue"?
-- NPC text
-- Descriptive and item text
-- Battle text
-- Environmental text (e.g., "Do you really think this looks like a pencil?" ($C68F74))
- What is "100%"?
-- Display all text in the script file
-- Display all text NPCs are capable of saying
--- Including/excluding mutually exclusive branches
- What is a "run"?
-- Is this a speedrun?
-- Is it a TAS?

Those are very basic questions that will be elaborated and changed as the project develops. For the moment, I'm going to use the following definition for this run in order to guide initial planning and brainstorming work:

