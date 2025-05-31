## Object Functions
If you are unsure how to use these object functions, check out the objects tab.

Any object function ending with `&triggers` may have an optional string of game triggers appended to them to execute alongside the function. See Triggers for more information.

## Basic Functions

---
## XY
Offsets the display of the object.

```json title="xy" 
xy(x,y)
```
**x (number)**
: Horizontal offset in pixels.

**y (number)**
: Vertical offset in pixels.

Syntax | Value Type | Description
------------|-------------|-------------
x | number | Horizontal offset in pixels.
y | number | Vertical offset in pixels.

---

## Solid
Makes the tile solid. Give a specific direction to customize which edge of the tile is solid. Can be stacked in the same object, to provide two or more directional solids.

```json title="solid" 
solid(type)
```
**type (direction)**
: Allows you to specify which edge direction of the tile is solid.
**Default**: All directions are solid.
**Options**: up, down, left, right, all, race, 0

---

## Messages
Displays a textbox message after interacting with the tile.

```json title="msg" 
name.msg(text)&triggers
```
**name (string)**
: If a name is given with a dot separator like name`.`msg, this object function oerates like a property attached to an entity. Omit the dot separator, if not using an NPC.

**text (string)**
: Contains the content of the message.
**Default**: Empty textbox.

---

## Answers
Defines the response to specified answers. Use this code after specifying answer options with the &answers trigger.

```json title="answer" 
answername=answer(text)
answer#n=answer(text)
answer.name=answer()
```
**answername (string)**
: Answer given by the player, such as "Yes" or "No". If multiple answers have the same name, you can differentiate them using a number `#n`.

**#n (number)**
: If multiple answers have the same name, you may differentiate them using a number.

**text (string)**
: Textbox response to the player's answer.
**Default**: Empty textbox.

---

## Dynamic Answers (add section)
Information

```json title="codename" 
answername=answer(text)
answer#n=answer(text)
answer.name=answer()
```
**answername (string)**
: Answer given by the player, such as "Yes" or "No". If multiple answers have the same name, you can differentiate them using a number `#n`.

**#n (number)**
: If multiple answers have the same name, you may differentiate them using a number.

**text (string)**
: Textbox response to the player's answer.
**Default**: Empty textbox.

---

## Footprints
Draws a sprite footprint, when the player walks offtile.

```json title="prints" 
prints(sprite,frames,speed,fade,directional)
```
**sprite (sprite sheet name)**
: Name of the footprint sprite sheet, uploaded to sprites in Mapbuilder.

**frames (number)**
: The number of frames in the sprite sheet.

**speed (string)**
: Speed of the animation.

**fade (number)**
: Time for the animation to fade in milliseconds (ms).

**directional (0/1)** 
: Based on direction?
**Options**: - 0 = No
1 = Yes

---
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
**Default**: Region sprite.

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
**Default**: Region sprite.

---

## Surf
Allows the player to begin surfing across the specified tile area, using the move "Surf".

```json title="surf" 
surf(direction)
```
**direction**
: Direction to begin surfing in. Replace 'direction' with direction name.
**Default**: Surf from any direction.
