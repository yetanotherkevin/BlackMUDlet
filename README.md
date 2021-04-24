# BlackMUDlet
Scripts and utilities for playing [BlackMUD](www.blackmud.com) with [Mudlet](www.mudlet.org).

Individual `.xml` files can be drag and dropped directly into the Mudlet main window to install individually.

## Character Status Utils
A set of triggers to scrape and store character status for use in other triggers and scripts.

For example: `if characterStatus["hungry"] then send("eat mushroom") end`

Currently tracks the following based on prompt, score, level, attributes, and other sources:
  - Player name, home, diety
  - Player race and class
  - Player title
  - Max HP, Mana, Move
  - Current HP, Mana, Move
  - Current EXP and next level EXP
  - Current ego
  - Hunger and thirst status
  - EXP and Gold gain (will echo new totals)

The `characterStatus` table stores all relevant information, and can be used to power GUI
elements such as health bars or info panels.

```
lua display(characterStatus)
{
  class = "Cleric",
  ["current hp"] = "378",
  ["current mana"] = "239",
  ["current move"] = "386",
  diety = "Minektur",
  ego = "snotty",
  exp = "77495033",
  gold = "33046",
  home = "Makilor",
  hungry = true,
  ["max hp"] = "378",
  ["max mana"] = "239",
  ["max move"] = "386",
  name = "Donal",
  race = "Dwarven",
  title = "the Dwarven Cleric"
}
```

## Tick Timer
A simple event-based tick timer. Syncs a 60 second Mudlet GUI timer whenever a `newTickEvent` is triggered. 

  - Configurable warning behavior in onTickWarning() including delay
  - Includes a trigger to show the current tick timer value beside the prompt

```
< 378 239 382 > (27)

You are now sober.

< 378 239 386 > (59)
cast 'true sight' me
Ok.
Your eyes glow silver.

< 378 179 386 > (21)
< 378 179 386 > (12)
                                                                      5 SECONDS UNTIL TICK
< 378 220 386 > (58)
```

## Numpad Navigation
A simple set of keybinds to allow the numpad to be used for movement.


## Forage Utilities
A set of triggers for forage related events. Includes a simple script to automatically annotate foraged food with its effects.
  - Triggers for each forage state are defined
  - Some forage messages are highlighted in relevant colors
  - A translation table and ratings table are defined

```
a medium blue bumpy pumpkin lies here. (travelling, cure light, blindness)
a tiny swirly pumpkin lies here.[2] (levitate, curse)
a medium healthy strawberry lies here.[2] (travelling, flamestrike)
a medium healthy bumpy strip of bark lies here. (travelling, flamestrike, blindness)
a medium healthy amber speckly pumpkin lies here. (travelling, flamestrike, cure blind, poison)
a tiny yellowish speckly strip of bark lies here. (levitate, spirit armor, poison)
a tiny amber swirly fruit lies here. (levitate, cure blind, curse)
a medium healthy speckly fruit lies here. (travelling, flamestrike, poison)
a tiny speckly pumpkin lies here.[3] (levitate, poison)
```

## Item DB Lookup
A simple script that scrapes a text dump of an item database for exact matches. Requires a local text file where each entry is separated by a blank line.
  - An "item description" is any block of text between two blank lines
  - An item will match if it contains the queried string exactly as specified anywhere within the description
  - e.g. "/item silver bands" or "/item str by 3" will both work
  - Searches are case-insensitive
  - Only returns exact matches, so "/item dragon-shield" probably won't work as it would in game
  - The same function could be used on textfiles containing non-item information, as long as each entry is separated with a blank line

```
/item silver armbands

Silver armbands - 'armbands arm silver' (found on Wep Chieftain) added by fast4you
	Type: armor - Worn: on arms - Weight: 5 - AC: 5 - Ego: teenie weenie
	Flags: GLOWING METAL MAGICAL
	Affects: DAMROLL By 2

Pair of silver armbands - 'armbands silver' (found on Osen) added by fast4you
	Type: armor - Worn: on arms - Weight: 6 - AC: 9 - Ego: itty bitty
	Flags: METAL
	Affects: BASH By 2

2 items found matching "silver armbands".
```
