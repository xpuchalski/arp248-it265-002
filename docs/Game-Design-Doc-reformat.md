Zombopoly

Updated Game Design Document


---

1. Introduction

1.1 Scope of the Document

This document functions as both a Game Design Document (GDD) and a technical handoff reference for future developers and AI agents assisting with development.

The document defines:

Core gameplay systems

Combat structure

Multiplayer rules

Dungeon persistence

Item systems

Turn logic

User interface intentions

Technical implementation goals

Art and presentation direction


The game is currently being developed in Godot using GDScript.


---

1.2 Elevator Pitch

Zombopoly is a multiplayer zombie survival strategy RPG inspired by board games and roguelikes. Players move through a persistent overworld, enter dangerous dungeons, fight zombies and bosses in turn-based encounters, collect permanent items that dramatically alter builds, and attempt either to outlive the other players or cooperate long enough to defeat all bosses and escape.

The game combines:

Board game structure

Persistent overworld exploration

Tactical turn-based combat

Roguelike item progression

Shared multiplayer risk management

Dungeon persistence

Encounter aggregation systems

PvP and zombified-player combat



---

2. Game Overview

2.1 Game Concept

Players take turns moving around a shared overworld map. During exploration they:

Collect items

Gain money

Enter dungeons

Fight zombies

Encounter bosses

Heal in safe zones

Trade in the Warehouse

Attempt to survive longer than opponents


The game supports both:

Competitive gameplay (last player alive)

Cooperative completion (kill all bosses and return to Warehouse)


The game is designed around strategic positioning, movement planning, risk management, and permanent item progression.


---

2.2 Audience

Target audience:

Fans of zombie survival games

Fans of board games

Roguelike players

Multiplayer strategy players

Turn-based RPG players


Inspirational overlap includes:

Mario Party

Left 4 Dead

Roguelikes

Tactical RPGs

Dungeon crawlers



---

2.3 Genre

Primary genres:

Multiplayer Turn-Based Strategy

Roguelike RPG

Zombie Survival

Dungeon Crawler


Secondary genres:

Board Game Inspired

Party Game



---

2.4 Setting

The game takes place on the outskirts of a zombie-infested modern city.

The tone is stylized rather than realistic.

The world contains:

Safe zones

Zombie-infested streets

Dungeon entrances

Boss arenas

Loot locations

Healing zones

Warehouse trading hub



---

2.5 World Structure

The game uses a persistent overworld.

Players move around a shared map and may:

Enter dungeons

Encounter zombies dynamically

Explore for loot

Heal in safe zones

Travel between objectives


Dungeons are instanced but persistent.

Critical rule:

The overworld never unloads.


This allows:

Other players to continue turns

Persistent world state

Persistent dungeon state

Simultaneous progression tracking



---

2.6 Player Structure

Supports:

1–4 players

Pass-and-play multiplayer


Players select from 9 preset characters.

Rules:

No duplicate characters

Each character has:

Basic attack

Unique special ability

AP resource system

Unique stats

Different scaling potential with items



Characters are intended to feel mechanically distinct.


---

2.7 Core Gameplay Loop

Core gameplay loop:

1. Start turn


2. Display movement radius


3. Move within radius


4. Interact with world


5. Trigger encounters if necessary


6. Collect items and money


7. Enter dungeons if desired


8. Use attacks/specials


9. End turn


10. Trigger enemy responses


11. Advance to next player



Long-term loop:

Gain stronger items

Build synergies

Defeat bosses

Survive encounters

Outlast opponents



---

2.8 Look & Feel

Visual direction:

Stylized 2D presentation

Chibi overworld characters

Portrait-driven combat UI

Modern-city outskirts environment

Bright but dangerous atmosphere


Feel goals:

Strategic tension

Constant threat management

Rewarding progression

Chaotic multiplayer situations

High replayability


UI inspirations:

Visual novel dialogue systems

Tactical RPG combat interfaces

Board game readability



---

3. Gameplay

3.1 Objectives

Primary objectives:

Survive

Defeat bosses

Acquire powerful items


Victory conditions:

1. Last player alive


2. Cooperative victory by defeating all bosses and returning all surviving players to the Warehouse



Secondary objectives:

Create powerful builds

Acquire legendary items

Explore optional dungeons

Trade strategically



---

3.2 Progression

Progression is item-based.

Players become stronger through:

Permanent item acquisition

Better combat positioning

Strategic AP management

Dungeon completion

Synergistic item combinations


There are no traditional RPG levels.

Progression pacing is driven by:

Risk-taking

Dungeon access

Item rarity

Boss rewards



---

3.2.1 Difficulty Curve

Difficulty scales through:

Increased zombie density

Stronger zombie variants

Harder bosses

Resource pressure

More dangerous encounters

Reduced cooperation as players die or become zombified



---

3.3 Play Flow

Early Game

Explore safely

Gather money

Obtain starter items

Avoid dangerous encounters


Mid Game

Enter dungeons

Build item combinations

Fight stronger enemies

Begin player conflict


Late Game

Boss encounters

Heavy item synergy

High-risk combat

Cooperative or competitive endgame



---

3.4 Difficulty

Difficulty emerges through:

Turn order pressure

Positioning

Zombie aggro

Resource management

Item RNG

Encounter merging


Difficulty settings are not currently planned.


---

4. Mechanics

4.1 Rules

General rules:

Players move during their turn only

Zombies act only during combat or aggro states

Players always take priority in turn order

Multiple encounters can exist simultaneously

Encounters can merge

Players cannot be in multiple encounters simultaneously

Items are permanent

Trading only occurs in the Warehouse



---

4.2 Turn Structure

The game uses a global turn system.

Definition:

A global turn completes after all active players finish their turns.


Example:

P1 → P2 → P3 → P4 → End Global Turn

At end of global turn:

Zombie respawns trigger

Item respawns trigger

Boss timers update

Encounter aggro updates occur


Important rule:

Players always act before zombies.



---

4.3 Combat System

Combat begins when:

A player touches a zombie

A player ends movement near a zombie

A human player overlaps a zombified player at turn start


Combat rules:

Initiating unit acts first

Zombies only enter turn order during combat

Multiple encounters can merge

Zombies near an encounter may join at global turn boundaries

Players joining an encounter may act immediately


Humans cannot attack other humans.

PvP exists only between:

Human vs zombified player

Zombified player vs human



---

4.4 AP System

Players use Action Points (AP) for special abilities.

Current rules:

Default AP cap: 20

Specials consume AP

AP regenerates slowly over time

Basic attacks do not consume AP


Different characters scale differently with AP-related items.


---

4.5 Zombie AI

Zombie behaviors:

Roam outside combat

Aggro nearby players

Join nearby encounters at global turn boundaries

Attack during combat order


Zombie variants include:

Walker

Runner

Brute

Boss variants



---

4.6 Boss System

Bosses exist inside dungeons.

Boss rules:

Defeating bosses grants major rewards

Bosses count toward cooperative victory

Bosses respawn after approximately 10 global turns

If all players die during boss combat:

Boss resets to full HP

Boss resets after 2 global turns




---

4.7 Item System

Items are permanent upgrades.

Rarity tiers:

White = Common

Green = Uncommon

Purple = Rare

Red = Legendary


Current rarity weights:

Common: 50%

Uncommon: 30%

Rare: 15%

Legendary: 5%


Item effects may include:

Bonus attack

Bleed

Burn

Lifesteal

Crit chance

Damage reduction

AP bonuses

Special effect triggers


Items are drawn from weighted pools.

Items respawn globally every 5 turns.


---

4.8 Economy

Currency is used for:

Dungeon access

Trading

Strategic resource management


Players gain money through:

Exploration

Encounters

Loot

Dungeon completion



---

4.9 Healing System

Healing zones exist in the world.

Healing rules:

Heal approximately 35% HP per turn while inside the zone

Healing is location-based rather than consumable-based


The Warehouse also functions as a safe area.


---

4.10 Trading

Trading rules:

Trading only allowed inside Warehouse

Both players must be present in Warehouse

Trade offers are proposed through the trade UI

Trade offers can include:

Items

Money



Trading is asynchronous by turn order.


---

4.11 Running From Combat

Players may flee encounters.

Current behavior:

Move approximately 100 units away from encounter center

Place player opposite encounter direction



---

4.12 Respawn Timers

Current intended timers:

Zombies: every 3 turns

Items: every 5 turns

Bosses: every 10 turns


These occur on global turn boundaries.


---

4.13 Zombification System

When a player dies:

They become zombified

Humans may fight them

They may fight humans

They can no longer function as normal survivors


This system is partially implemented.


---

4.14 Character Movement

Movement uses a radius-based system.

At turn start:

A movement radius is displayed

Players may move only inside radius


Important implementation rule:

The movement limit remains fixed during the turn.


Radius drawing is handled directly by the overworld system.


---

4.15 Dungeon Persistence

Dungeons persist after entry.

Current implementation goals:

Dungeon remains active after leaving

Player exits near entrance

Dungeon state remains saved

Boss state persists

Loot state persists


The overworld remains loaded simultaneously.


---

4.16 Saving

Intended save behavior:

Preserve overworld state

Preserve dungeon state

Preserve player progression

Preserve inventories

Preserve encounter state


Exact save architecture is still evolving.


---

4.17 Menus

Current/planned menus:

Main menu

Character select

Lore screen

How-to-play screen

Inventory UI

Trade UI


Options menu is currently not planned.


---

5. Graphics and Audio

5.1 Visual System

Visual style:

Stylized 2D

Chibi overworld sprites

Portrait-driven combat presentation

Clean readable UI


Animations prioritize readability over realism.


---

5.1.1 Camera System

Current camera goals:

Camera follows active player

Scroll-wheel zoom

Smooth turn transitions

Combat focus behavior



---

5.1.2 Environment Design

Environment goals:

Readable overworld

Modern city outskirts atmosphere

Distinct dungeons

Clear combat spaces

Strong contrast between safe and dangerous areas



---

5.2 Interface

Important UI systems:

Turn order display

Combat panel

Character portraits

Inventory panel

Trade panel

Combat portraits

Movement radius visualization


Combat portraits:

Player portrait left

Enemy portrait right

Hurt portrait variants

Damage shake effects



---

5.3 Audio System

Audio goals:

Maintain tension

Reinforce danger

Support strategic pacing


Audio style is atmospheric rather than cinematic.


---

6. Story and Narrative

6.1 Backstory

The world has been overrun by infected entities.

Players are survivors attempting to navigate dangerous territory while searching for resources, defeating major infected threats, and escaping alive.

Narrative primarily supports gameplay systems.


---

6.2 Main Plot

The narrative structure revolves around:

Survival

Exploration

Dungeon clearing

Boss elimination

Escape


Narrative emphasis is secondary to gameplay.


---

6.3 Cutscenes

Cutscenes are minimal.

Storytelling methods:

Dialogue boxes

Environmental storytelling

Character flavor

Lore screens



---

7. Characters

7.1 Playable Characters

Current design:

9 selectable characters

Unique abilities

Unique stats

Distinct scaling profiles

Distinct visual identities


Each character supports different playstyles.


---

7.1.1 Character Personality Goals

Characters should feel:

Distinct

Memorable

Mechanically expressive


Heavy narrative depth is optional.


---

7.1.2 Character Appearance

Art goals:

Strong silhouettes

Readable portraits

Chibi overworld readability

Stylized identities


Portraits are heavily emphasized in UI.


---

7.1.3 Character Abilities

Each character contains:

Basic attack

Unique special

AP interactions

Different combat strengths

Different item scaling potential



---

7.2 Supporting Characters

Potential future additions:

NPC traders

Survivors

Story characters

Dungeon contacts



---

7.3 Enemies

Enemy types include:

Standard zombies

Fast zombies

Heavy zombies

Exploding zombies

Assassin-type zombies

Boss zombies


Enemy variety should encourage different combat approaches.


---

8. Game World

8.1 World Feel

The world should feel:

Dangerous

Loot-driven

Exploratory

Strategically hostile

Chaotic during multiplayer encounters



---

8.2 Major Locations

Major locations:

Warehouse

Overworld routes

Dungeon entrances

Boss arenas

Loot zones

Healing zones



---

8.2.1 Connection to Gameplay

Warehouse

Safe trading area

Strategic regrouping point

Cooperative victory endpoint


Dungeons

Risk/reward progression

Boss encounters


Overworld

Resource gathering

Exploration

Dynamic encounters



---

8.3 Levels

The game uses a persistent overworld rather than linear levels.


---

8.3.1 Tutorial Area

A dedicated tutorial is currently not planned.

Gameplay learning is expected to occur naturally through play.


---

8.3.2 Main Areas

Main areas include:

Persistent overworld

Dungeon interiors

Boss chambers

Warehouse



---

8.3.3 Optional Areas

Optional content may include:

High-risk dungeons

Secret bosses

Rare loot zones

Hidden encounters



---

9. Technical Notes For Future Developers / AI Agents

Engine

Godot Engine

GDScript

2D project



---

Important Existing Architecture

Known important systems:

Persistent overworld

ActiveDungeonHolder node

Encounter management

Combat state management

Turn manager

Character selection system

Portrait-based combat UI

Dynamic dungeon generation

Inventory system

Trade system



---

Critical Design Constraints

1. Overworld must never unload.


2. Dungeons must persist after creation.


3. Players always act before zombies.


4. Zombies only participate in turn order while in combat.


5. Multiple encounters can merge.


6. Movement radius visualization must match true movement rules.


7. Trading only occurs in Warehouse.


8. Humans cannot fight other humans.


9. Zombified players can fight humans.




---

Important Existing Scene/UI References

Known scene structures include:

CharacterSelect.tscn

Character buttons

Portrait containers

Info label

Back button


Overworld UI

HUD

TurnLabel

EndTurnButton

CombatPanel

AttackButton

RunButton

SpecialButton

BlockButton

TurnOrderBar

Inventory UI

Trade UI



---

Current Development Priorities

Most important remaining priorities:

UI polish

Enemy variety

Menu completion

Save system

Audio integration

Additional content

Encounter stability



---

Recommended Future Refactors

Potential future improvements:

Split monolithic overworld logic into subsystems

Separate combat manager

Separate dungeon manager

Centralized data definitions

Event-driven turn management



---

10. Final Notes

This document is intended to provide a strong foundational understanding of the game’s mechanics, architecture goals, and gameplay intentions.

Future developers or AI agents should prioritize:

Preserving system consistency

Maintaining persistent-world behavior

Preserving turn-order clarity

Avoiding feature bloat

Maintaining readable UI flow

Protecting multiplayer pacing


The project’s strongest design pillars are:

Persistent world state

Strategic turn management

Dungeon persistence

Permanent item progression

Emergent multiplayer interactions

Tactical zombie encounters

Chaotic build scaling

Cooperative/competitive endgame structure
