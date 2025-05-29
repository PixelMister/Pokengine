# Building Objects
The easiest place to start building is to make your own custom object(s)! An object is a single 16x16 tile that holds its own special properties to add functionality to the game. 

The most common objects are simple, such as; walls, ledges, or signs. Some objects can be more complicated such as doors, warps or stairs. A lot of objects are pre-built within Mapbuilder already, making your job as a developer even easier. 

However, you may want to be familiar with creating your own objects in case you need to.

To build your own object, you need to place an object block on the specific tile you want to work with. Many object blocks in the Mapbuilder editor have pre-existing code, so make sure the pre-existing code suits your situation. For example, the red solid object block code `solid()`, makes the entire tile solid. If you do not want the tile to be solid, do not use this block and use a normal object block instead.

To access the block editor, right click on the object when placed on the mapbuilder tilemap viewer, to open up the jCoad editor. We can now begin typing whatever code we want.

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
