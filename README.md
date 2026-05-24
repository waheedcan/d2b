# The Curse of the Crimson Dungeon

A point-and-click fantasy adventure built with Phaser 3 for CMPM 120-01, Spring 2026.

## How to Play

Open `index.html` in a browser (or visit the GitHub Pages link).  
Click on objects to interact. Hover to see descriptions. Build up your inventory and make the right choice at the altar.

**Good path:** Village Square → Dark Forest (get Herb + Hermit Clue) → Dark Forest (get Iron Key) → Dungeon Entrance (get Scroll Hint + Blessing) → Dungeon Chamber → Curse Altar (break the curse).

---

## Code Requirements

### 4+ AdventureScene subclasses (`game.js`)
| Class | Scene Key |
|---|---|
| `VillageSquare` | `'VillageSquare'` |
| `DarkForest` | `'DarkForest'` |
| `DungeonEntrance` | `'DungeonEntrance'` |
| `DungeonChamber` | `'DungeonChamber'` |
| `CurseAltar` | `'CurseAltar'` |

### 2+ non-AdventureScene scenes (`game.js`)
| Class | Scene Key | Purpose |
|---|---|---|
| `Intro` | `'Intro'` | Animated title card with typewriter lore |
| `BadEnding` | `'BadEnding'` | Crimson flash, falling rubble, greed punished |
| `GoodEnding` | `'GoodEnding'` | Dawn light, sparkle particles, curse broken |

All three extend `Phaser.Scene` directly.

### 2+ engine methods added to `adventure.js`

**`describe(obj, msg)`** — Attaches a `pointerover` listener that calls `showMessage()` and dims the object. Removes ~3 lines of boilerplate per interactive object; used on every object in the game.

**`shake(obj)`** — Runs a quick ±8 px left-right tween (5 cycles, 55 ms each) signalling an invalid interaction. Used on locked doors, sealed items, and wrong approaches.

**`placeItem(emoji, label, x, y, itemKey, hoverMsg)`** — Creates a text object, wires `describe()` for hover, and on click: adds to inventory, shows a message, and tweens the object upward until it disappears. Replaces ~12 lines of repeated pickup code per collectible.

### Data assets

No external image or audio files are used. All visuals are procedurally generated using Phaser's `Graphics` API (rectangles, circles, lines) and emoji rendered as text objects. No third-party assets require attribution.

---

## Experience Requirements

| Requirement | Satisfied by |
|---|---|
| 4+ world locations | 5 AdventureScene locations |
| 2+ interactive objects per scene | 4–5 per scene, all clickable |
| Many pointerover messages | Every object uses `describe()` |
| Many pointerdown effects | Inventory changes, scene transitions, tweens |
| Animated objects | `shake()` on locked items; tween on pickups; pulsing gem; flickering torches; firefly particles |

---

## Process Requirements

This repository is forked from [rndmcnlly/AdventurePrototype](https://github.com/rndmcnlly/AdventurePrototype), preserving Adam Smith's original commit history. Development commits proceed from engine scaffold → world traversal → interactive objects → engine enhancements → polish.
