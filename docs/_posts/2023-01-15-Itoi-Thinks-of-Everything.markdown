---
layout: post
title: "DevTeam thinks of everything"
date: 2023-01-15 13:57:00 -0700
categories: Development Brainstorming
---

A popular saying about the game NetHack (1987) is that "the DevTeam thinks of everything", in reference to the large number of improbable and obscure interactions and circumstances that the game code handles. The cockatrice monster is a canonical example: it can petrify players or monsters if it touches bare skin. There are many exceptions and counter-exceptions to this rule (e.g., gloves allow you to safely wield a cockatrice corpse as a weapon, but if you fall down the stairs while doing so you'll be petrified, because the corpse touches another part of your body during the fall). (read more on the [NetHack Wiki entry for Cockatrice](https://nethackwiki.com/wiki/Cockatrice#Ways_to_be_petrified_by_a_cockatrice)).

We might make a similar claim about Earthbound, something along the lines of "Itoi thinks of everything". As alluded to in earlier posts, the game features a large amount of conditional dialog to cover circumstances a typical player is unlikely to ever encounter. Many of these are practical, error-checking dialogues: near the beginning of the game Buzz Buzz attempts to give you the Sound Stone, a key item. If your inventory is full, he says he will leave it with your sister Tracy, who then says something different when you speak to her afterwards.

Onett, the first area of the game and the segment I am routing a full dialogue run for, contains an unusually high number of these conditional dialogs. Routing has been a challenge for this reason. However, I've made great progress on the helper script I'm developing ([GitHub repo](https://github.com/parnellj/earthbound-dialogue-tools)) and have begun the initial routing of the fairly self-contained "meteor scene" with which the game opens.