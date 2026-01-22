# Game Studio Brainstorming Template

## Studio Name Ideas
- **Primary Ideas:**
  - Acid rain
  - Fire rain
  - Antacid rain (if acid rain is too close to acid rainworld)
    
- **Acid Rain**:
- **I really like risk of rain, so I wanted to pay homage to the IP with the _rain_ part and I was thinking about game mechanics revolving around a damaging acid rain, and the rain would be acid because I can imagine acid being orange and that's my favorite color**:
- **no idea what social medias with name available means**:
- **there's a game called "acid rainworld" that looks like an A rated game and a game called "acid rain" made on gamemaker**:

---

## Vision Statement
*What is the mission of your solo game studio? How does it align with creating and analyzing innovative game architectures?*

> I'm one person but I intend to draw assets, make pixel sprites for the game, animations, backgrounds, and story for it, as well as the programming obviously. 

---

## Core Values
*What principles guide your studio's approach to game design, architecture, and development?*

- the movement must feel crisp
- the gameplay should make you want to play again, even if you lose
- tackle one feature at a time, expand later
- get something working, then add more, get another feature working, add more, repeat

---

## Target Audience
*Who are your games designed for? Identify your primary audience based on your focus on card and board games.*

- **Demographic:** roguelike indie fans
- **Interests:** people who like roguelikes
- **Platforms:** pc only

---

## Genre Focus
*What types of games will your studio focus on?*  
*Consider your course's emphasis on depth, mechanics, and balance in card and board games.*

- Roguelike
- sci-fi stylized 

---

## Unique Selling Point (USP)
*What will make your games stand out from others, particularly in the indie/board game space?*

> the main selling point is that when lightning strikes enemies will spawn in dark spots, and that you have to adapt to that.

---

## Tools and Technology
*What tools and platforms will you use to develop, test, and publish your games?*

- **Game Engine(s):** godot probably
- **Art Tools:** pixel art and digital art
- **Audio Tools:** no clue
- **Version Control:** git
- **Publishing Platforms:** itch.io

---

## Branding and Aesthetics
black, white, gray, orange

- **Logo Style:** stylized
- **Tagline Ideas:** 
  - [Tagline 1: e.g., "Simple Games, Complex Stories."]
  - [Tagline 2: e.g., "Where Mechanics Meet Meaning."]
  - [Tagline 3: e.g., "Architects of Fun."]

-- **Sketches/Logo**:

---

## Additional Notes
inspiration : risk of rain 1 and 2, the binding of isaac, 

> Ideas that I have worked out:
> you can move around with wasd on a side-view 2d plane
> shadows cast by the background onto the foreground are non-interactable
> at set time intervals, the screen gets darker, lightning flashes, and enemies spawn in the shadow areas
> enemies are full black, which makes their spawn in the shadows hidden
> after lighting, the shadows aren't as dark, which makes the enemies much more visible
> you have a raincoat that serves as an armor bar, and a health bar underneath. when you're damaged beyond your raincoat bar, you take small passive DOT from the acid rain
> the enemy spawns are dictated by a "director" who has a budget, each enemy has a cost, which detracts from the budget.
> the director must spawn enemies until its budget is depleted every wave (budget increases over time, left-over money is preserved)
> director must spawn at least one enemy with an item every wave, that item drops, the player can pick it up (gives buffs to player and enemy)
> math : 10 common items, 7 uncommon items, 5 legendary items - director picks a number between 1-100, if number is 1-70, rng from 10 common items, if number is 71-95, rng from uncommon item pool, if 95-100, rng legend item pool. as time progresses, the numbes decrease/increase logarithmically and the odds flip
> at the far right of the stage, there's an XL shadow, where the director is given a lot more budget when is on screen, which allows it to pick from a boss pool.
> defeating a boss always gives a legendary or uncommon item
> once boss is defeated, progress to next stage (press e inside of the big shadow and the ground will break beneath you and you'll fall to the next stage)
> GUI
> timer on screen
> items visible
> pausing game stops ALL things
> boss healthbar when boss is spawned
> player healthbar (and raincoat _armor_ bar)
> list of animations needed : falling, walking/running, jumpsquat, attack (minimum 1 /or 2), death
> enemy animations needed : death, attack, movement
> sprites needed : backgrounds, foregrounds, items, player (animations), enemies (animations), lightning, weapons/projectiles, gui elements, visual-novel-esque images
