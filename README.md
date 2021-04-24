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

## Tick Timer
A simple event-based tick timer. Syncs a 60 second Mudlet GUI timer whenever a `newTickEvent` is triggered. 

  - Configurable warning behavior in onTickWarning() including delay
  - Includes a trigger to show the current tick timer value beside the prompt

## Numpad Navigation
A simple set of keybinds to allow the numpad to be used for movement.


## Forage Utilities
A set of triggers for forage related events. Includes a simple script to automatically annotate foraged food with its effects.
  - Triggers for each forage state are defined
  - Some forage messages are highlighted in relevant colors
  - A translation table and ratings table are defined

## Item DB Lookup
A simple script that scrapes a text dump of an item database for exact matches. Requires a local text file where each entry is separated by a blank line.
  - An "item description" is any block of text between two blank lines
  - An item will match if it contains the queried string exactly as specified anywhere within the description
  - e.g. "/item silver bands" or "/item str by 3" will both work
  - Searches are case-insensitive
  - Only returns exact matches, so "/item dragon-shield" probably won't work as it would in game
  - The same function could be used on textfiles containing non-item information, as long as each entry is separated with a blank line
