---
layout: post
title: "Exploring Earthbound's NPC and dialogue data"
date: 2023-01-08 11:52:00 -0700
categories: Development Brainstorming
---
I recently had the idea to conduct a "100% dialogue run" of the video game Earthbound (1994). This is a logistically challenging idea -- the game contains many NPCs with numerous branching and mutually exclusive dialogue options. The scope of such a project is quite large and I expect a run would take at least 20 hours, possibly more, even optimized for speed and routing.

This project supports some of my academic and intellectual ideas -- I'm interested in the game as a text, but the "text" as such is necessarily interactive, in movement, dependent on the user's inputs. I would move that this is one attempt to display the "complete text" of a video game, or part of it anyway -- the dialogue and writing.

Also, it's fun! So, where am I at? I'm playing with CoilSnake, EB Project Manager, and CataLatas [Earthbound Script Dumper](https://github.com/CataLatas/earthbound-script-dumper/). The decompiled ROM files contain a table of NPC initialization data (map location, flag, and pointers to sprite and text data) and the game script. Especially with the EB Script Dumper, I should be able to index 