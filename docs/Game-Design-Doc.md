## engine : Godot
## version : 4.6,1

# Game Design Document
## Core Concept
### Theme
Zombies Undead
### Genre
Tycoon
### Mechanic
- Resource Management
- Turn-Based Combat
- Crafting System
### Objective
- Escape a Dangerous Environment
- Achieve a High Score
- Discover the Hidden Story
### Constraint
Limited Lives
### Perspective
2.5D Perspective
### Player Count
Local Co-Op 3-4 Players
### Art Style
Paper-CutOrigami Style

# deliverables :
 - this has to be a multiplayer game, but it also has to be played on one machine, pass and play. ideally, i would like to to have a player selection count at the beginning screen, from 1-4 players. so that one player can play alone if they wnat.
 - move around a large plane in turns, each turn every player gets a movement opportunity. based on a stat, they have a radius drawn around them that they can move anywhere within.
 - if the player ends a turn with en enemy inside of the radius, the enemy will attack the player and start a battle phase for that player.
 - in a battle phase, whatever entity is included in the battle phase will have a turn, once all these turns elapse, other players in their movement phase take their movement turn, then it will be the battle phase's turns agian.
 - other players can join into a battle by having the battle within their radius and interacting with it. 
 - enemies being defeated reward 10 credits. 
 - money can also be found around the map, 5 credits .
 - areas around the map can be interacted with and purachased if the player interacting with it has enough money. 
 - if the player returns to the savehouse, the area where all players initially spawn, they may craft.
 - new enemies spawn at the end of every full turn, outside of every player radius, with a maximum number of enemies on the board possible being something like 20.
 - a trade can occur when a player sends a trade request to another player and the other player accepts on their turn. in this menu, anything can be traded for anything. (money and items, nothing can also be traded)
 - when a player dies for the first time they respawn as a zombie with all their items, as a azombie they can attack other players by traversing to them and interacting with them while htey are in the same radi. they can be revived by an item or by a special character ability, but only once.
 - all enemy encounters can be ran from. regular enemies disappear when ran from, boss enemies have their health regened at the end of the global turn.
 - you can select between a choice of 9 characters at the beginning of the game, no duplicates.
 - status effects, burn, bleed, stun, necrosis

# to-do (basically a features list)

- (done) make the camera zoom in and out with scroll wheel
- (done) display turn order with a graphic at the bottom middle. (showing the portrait of each unit in the turn order, red if its in combat)
- (done) when you leave a dungeon it shouldn't reset everything, and when you come out you should be at the dungeon entrance. 
- (done) add dungeon functionality
- (done) instead of the player being able to attack multiple times a turn in a combat turn, the player should be able to attack once and then the zombie attacks and the turn goes to the next player's movement turn.
- (cancelled) if the player ends the turn with zombies in their radius they should attack the player
- (cancelled) multiple zombies should be able to attack one person if they're in radius at the end of turn
- (done) move the character selection buttons to the center of the screen 
- (done) when you select a player character on the selection screen it will show that characters portrait in the top left for player 1, top right for player 2, bottom left for player 3, bottom right for player 4.
- (done) during battle make the player portrait and zombie portrait render
- (done) when players take damage make them move left and right and modulate their color to fade in and out of red 
- (done) instead of the items being a set item they should pull from an item pool
- (done) add character spesific abilities, 3 per character (+ run) attack, special attack, block.
- (done) different zombies
- add zombie sprites
- (done) instead of respawn zombies every turn, respawn them every 3 turns. items 5 turns, bosses 10 turns.
- (done) change spawn area of zombies to reflect new walkable area.
- (done) spawn dungeons even farther away
- (done) when going to a dungeon, flash a loading screen for a second to hide the teleport and initialization
- (may not be do-able for me) allow multiple fights to happen at once
- (done) change running away from a fight to spitting you out 100 units away from the battle in the opposite direction instead of at the edge of the radius
- (done) change the in-battle pictures to use the portrait of the player not the sprite
- (done) increase the size of the battle portraits
- (done) instead of the player's base damage being in the actual attack, have it be a variable in the player
- (done) make the generated objects in the dungeons much larger, and fewer
- (done) prevent the objects generated in the dungeons from generating on or poking out of the boundaries
- (done) increase walking speed and tilting animation speed by 1.5x
- (done) change all combat participants are colored red on the turn-order-bar, not just zombies
- the size of the map is currently 5000x5000, center is 0,0. dungeons are 1500x1500. this may need to be changed...
- (done) add a confirm button at the bottom center of character select that becomes available once all the characters are selected. 
- make sprites for the world
- (cancelled) make a tutorial level maybe
- (done) make an actual fucking win condition
- (done) revert character values from debug values
- (done) when a player enters or exits a dungeon end their turn
- (done) add some functionality to the warehouse
- (done) add collision to the boxes in the dungeons
- (done)add a better way to heal 
- (done) instead of a diamond for the items i want to make it a particle, like sparkles. with different colors for different rarities
- (done) rework every character
- (done) rework every item
- (done) draw sprites for the zombies
- (done) add pvp back
- (cancelled) visual novel dialogue somewhere
- (done) add an inventory button where it displays what items you have and what they do
- (done) implement trade system. when in warehouse, can trade with other players in warehouse (with a button at the bottom left). click button, select player (players not in warehouse are grayed out, uses player portaits) sends a trade offer. next player can accept or deny it on their turn. then the player can propose which items or money to trade on their turn. 
- (done) add functionality of radius drawer back into overworld, remove radius drawer node, remove radius drawer script 
- (done) fix pvp
- (done) make the player be underneath something if its under its y axis value and above it if it is above it
- (done) change it so that obstacles and enemies cannot spawn in the bottom center of the dungeons
- (done) make zombies squash and stretch up and down a little bit like the players
- (cancelled) make a running animation for each of the players chibis
- (cancelled) make a hurt face for each of the players portaits for when they get hit
- make a "how to play" screen 
- add an about the game section on the main menu where you can view the board game and get a note from me
- add a lore button on the main menu where you can read the game's story
- (done) draw a title screen
- make an options screen

# elaborations on complex features
I'm going to build a 2d game in godot. when the player opens the game they will have a starting screen that has start game, options, and exit game on it. when the player selects start game, they will be prompted to select the number of players (from 1-4) and then the player will select from 9 preset characters for each player. while playing the game, during their turn the player will move around a 2d plane with areas that you can go inside if you have enough money. the player will have a circle drawn around them where they can go anywhere inside of that radius on their turn. there are zombies around the map, if a player touches them they will enter a fight with that zombie and go first. if the player ends their turn with the zombie in their radius, the zombie will attack them and it will have its turn before the player. on defeat, zombies drop money that is automatically added to the player(s) who killed it. when the player has enough money, they may purchase access to one of the many areas around the map that function as dungeons with a boss inside and other loot. there are items scattered around the map that can be picked up, they are replaced at their spots every 3 turns. zombies respawn at the end of every full turn, with a max of 20 on the map at once, they cannot spawn inside of a player's radius. combat functions as a turn-based system players have 2 attacks to choose from, which differ from character to character. once one combat turn has elapsed, it is the next player's turn for movement/combat.

elaborations : multiplayer type - pass and play. the players will be sitting next to each other and pass the computer to the next player to control them. or have multiple controllers connected that will control the characters on their turn, like mario party, if i can figure that out. people cannot pick the same character once a character has been picked the win condition is to survive. with a secondary objective of have all the bosses on the map defeated at once (bosses respawn every 5 turns) if this is done, the game will end. one "turn" is a player can do whatever they want on their "turn" and when they want to be done, they click an "end turn" button and pass the turn to the next player, or if they are in combat/a zombie is in their radius, that zombie will get a turn too. the global turn ends when the last player / zombie has taken their turn, this is when items/zombies/bosses/etc. will respawn, and "turn end" effects will proc. the movement circle is established around a character at the start of their turn, when they move, the circle does not move until the player ends their turn and their turn is back to them. during your turn, you can do anything you want within your circle, you can move as much as you want, interact with anything inside of your circle by moving your character into contact with it, and interact with anything in your inventory (there will be a trade system and alliance system, that i forgot to bring up) zombies do not move unless triggered. zombies only get a turn if a player ends their turn while a zombie is in their radius. zombies always go second in combat unless they interact with the player first or have an effect declaring otherwise. if multiple zombies are in the radius at the end of the turn, the player fights all of them at once. if multiple players have a zombie in their radius, they team up against them (necessary for boss fights) I have a document about hp and attacking values and attack abilities, that will be added once the skeleton of the game is down. base values, 10 hp for player, 10 hp for zombie, 10 damage for basic attack. for testing purposes ONLY when players die they are zombified, they are ignored by zombies, have a larger radius, retain all their items, have half health, can attack players, and death for them is final. though they can be revived to human status through several methods. money is not shared, it is player based. items are not visible before being interacted with, this simulates drawing a card from a deck. saying "every 3 turns" or "every turn" or "every 5 turns" is always refering to the global turn unless specified. there are no "spaces", but items and zombies would have collision boxes, so they could not occupy the same space. dungeons are separate scenes. the 9 preset characters have different abilities and appearances. the intention of the game is to be played on keyboard and mouse, but if controller is easy i will try to implement that.

all combat encounters in range would merge. a player cannot be in 2 encounters, all encounters in radius will merge a player who dies in their turn will immediately turn into a zombie and end their encounter with any zombie or boss (provided no other players are in that combat encounter) players CAN choose to fight zombies and act like a human still, but will be ignored by zombies moving around the map. zombified players can no longer pick up items or money, and cannot regenerate health by outside means (non-item/player effects). also, if all players in a boss encounter die, the boss will regen to full hp in 2 global turns. everything always uses the global turn unless specified. players can always run from combat, but the zombies in radius who are not defeated will still be in their radius, so they will eventually have to be dealt with. zombies cannot spawn inside a player radius, and players cannot move during combat, so a zombie will never join an ongoing player fight. bosses have special effects, but i havent ironed them out. zombified players can enter dungeons regardless of their money, their money is automatically set to zero revival can happen in combat or outside of it. it depends on the source of the revival. zombified players are just a chaotic fun-mode so that it doesn't suck to get eliminated. it's like, imagine a player who is REALLY OVERPOWERED dies to a random zombie, they are now a walking NUCLEAR BOMB that needs to be approached with extreme caution. which i find very fun and chaotic. alliances and trading are done through menus. trading and alliances can happen anytime not-in-combat, and all they require is the consent of both players to initiate. alliances can be disbanded at any time by any player with an equal or majority vote. alliances provide buffs increasing in value with how many players are in it. and any item/money can be traded for anything, (can also be gifted, traded for nothing)by default, players cannot attack each other. everyone gets full reward when loot is distributed. bosses drop items, zombies drop money, zombified players drop nothing. click to move within radius a player cannot touch multiple things at the same time. it will tick one thing before the other guaranteed. interactions have a collision radius. every object has a collision box zombies spawn fully randomly, cannot overlap with any collision box, and cannot be inside of a player's radius. dungeons are fixed on the map. items have set positions on the map, and they cannot spawn if a player is on top of where they would spawn) a player can end their turn at any time. combat will be an overlay on top of the map. players will see an upcoming turn order on the top of the map.
