## Installation
Download .xml and drag/drop directly onto Mudlet main window, or drag [this link](https://github.com/yetanotherkevin/BlackMUDlet/raw/main/Character%20Status%20Utils/Character%20Status%20Utils.xml) directly.

## Character Status Utils
A set of triggers to scrape and store character status for use in other triggers and scripts. Will need to send `score`, `level`, and `attributes` commands before things will work correctly.

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

Example:
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
