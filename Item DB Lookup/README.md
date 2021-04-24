## Installation
Download .mpackage and drag/drop directly onto Mudlet main window, or drag [this link](https://github.com/yetanotherkevin/BlackMUDlet/raw/main/Item%20DB%20Lookup/Item%20DB%20Lookup.mpackage) directly.

## Item DB Lookup
A simple script that scrapes a text dump of an item database for exact matches. Requires a local text file where each entry is separated by a blank line.
  - An "item description" is any block of text between two blank lines
  - An item will match if it contains the queried string exactly as specified anywhere within the description
  - e.g. "/item silver bands" or "/item str by 3" will both work
  - Searches are case-insensitive
  - Only returns exact matches, so "/item dragon-shield" probably won't work as it would in game
  - The same function could be used on textfiles containing non-item information, as long as each entry is separated with a blank line

**Use the .mpackage to install to ensure itemdb.txt ends up in the correct location.**

Example:
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
