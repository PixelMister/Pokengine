## Object Functions
If you are unsure how to use these object functions, check out the objects tab.

Any object function ending with `&triggers` may have an optional string of game triggers appended to them to execute alongside the function. See Triggers for more information.

## Overworld Actions

---

## Cut
Creates a tree with an image that can be cut down with the move “Cut”.

```json title="cut" 
cut(encounter_list,sprite)[&triggers]
```
**encounter_list (string)**
: Encounter list to use when player cuts down the object. See encounters code.

**sprite (sprite sheet)**
: Sprite that displays as the object to be cut.
Default: Region sprite.

---

## Rock Smash
Creates a rock or object with an image that can be cut down with the move “Rock Smash”.

```json title="rocksmash" 
rocksmash(encounter_list,sprite)[&triggers]
```
**encounter_list (string)**
: Encounter list to use when player smashes the rock or object. See encounters code.

**sprite (sprite sheet)**
: Sprite that displays as the rock or object to be smashed.
Default: Region sprite.

---

## Surf
Allows the player to begin surfing across the specified tile area, using the move "Surf".

```json title="surf" 
surf(direction)
```
**direction**
: Direction to begin surfing in. Replace 'direction' with direction name.
Default: Surf from any direction.
