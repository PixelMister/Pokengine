## Object Functions
If you are unsure how to use these object functions, check out the objects tab.

Any object function ending with `&triggers` may have an optional string of game triggers appended to them to execute alongside the function. See Triggers for more information.

## Basic Functions

---
### XY
Offsets the display of the object.

```json 
xy(x,y)
```
**x (number)**
: Set the horizontal offset in pixels. Can be positive or negative values.

**y (number)**
: Set the horizontal offset in pixels. Can be positive or negative values.

**xy(x,y) (number)**
    : Setting the horizontal and vertical offset together in pixels. Can be positive or negative values.

---

### Solid
Makes the tile solid. Give a specific direction to customize which edge of the tile is solid. Can be stacked in the same object, to provide two or more directional solids.

```json
solid(type)
```
**type (direction)**
: Allows you to specify which edge direction of the tile is solid.
**Default**: All directions are solid.
**Options**: up, down, left, right, all, race, 0

---

### Non Player Characters (NPCs)
Spawns an NPC on the tile.

```json
name=npc(skin,direction,path)
```
**name (string)**
: Name of the NPC to refer to it elsewhere. It is heavily recommended to use `%random%`, rather than a custom name as much as possible.

**skin (skin)**
: Skin ID number, which is the NPCs overworld sprite.

**direction (direction)**
: The NPC's starting direction

**path (area)**
: The NPCs path boundary. The NPC will wander around this area randomly..

---

### Messages
Displays a textbox message after interacting with the tile.

```json
name.msg(text)&triggers
```
**name (string)**
: If a name is given with a dot separator like name`.`msg, this object function oerates like a property attached to an entity. Omit the dot separator, if not using an NPC.

**text (string)**
: Contains the content of the message.
**Default**: Empty textbox.

---

### Answers
Defines the response to specified answers. Use this code after specifying answer options with the &answers trigger.

```json
answername=answer(text)
```
```json
answername=answer(text)
```
```
answername=name.answer()
```
**answername (string)**
: Answer given by the player, such as "Yes" or "No". If multiple answers have the same name, you can differentiate them using a number `#n`.

**#n (number)**
: If multiple answers have the same name, you may differentiate them using a number.

**text (string)**
: Textbox response to the player's answer.
**Default**: Empty textbox.

---

### Dynamic Answers (add section)
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

### Footprints
Draws a sprite footprint, when the player walks offtile.

```json
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

### Ledge
Creates a ledge that can be hopped over in one direction.

```json
ledge(direction,jump_height,distance)
```
**direction (direction)**
: Direction to jump.

**jump_height (number)**
: Height to jump in pixels.

**distance (number)**
: Distance to jump in pixels. Should be increments of 16.

**fade (number)**
: Time for the animation to fade in milliseconds (ms).

---

### Item
Spawns an overworld item or Pokémon. If a Pokémon is spawned, it will be given to the player, not battled.

```json
item(id,amount,sprite)
```
**id (id)**
: ID of the object to spawn. This can be an item ID number or a Pokemon Generation String.

**amount (number)**
: Number of items to give.

**sprite (sprite sheet | `hidden`)**
: Item sprite sheet. Use `hidden` to make this item invisible.
**Default**: Region Sprite.

---

## Map Transfers and Movement

---
### Spawn
Creates a spawn point. Use on entrances, exits or other spawn points.

```json
spawn(id,direction,move)
```
```json
spawn(heal)
```
```json
spawn(cave)
```
```json
spawn(safari)
```
```json
spawn(fly)
```
**id (number)**
: A spawn ID number that is unique to the map. This ID can be used to warp players to this spawn point.
**Options**: heal, cave, safari, fly

**direction (direction)**
: Direction the player faces when spawning here.

**move (0/1) [Can be omitted]**
: Move one tile in the aforementioned direction.

**fade (number)**
: Time for the animation to fade in milliseconds (ms).

---
### Warp
Warps the player to a spawn point.

```json
warp(map,spawn)&triggers
```
**map (ID)**
: The Map ID to warp to.

**spawn (number)**
: Spawn point number to warp to.

---

### Door
Creates a door object, that animates when the user walks through it.

```json
door(sprite,map,spawn)&triggers
```
**sprite (sprite sheet)**
: Spawn point number to warp to.

**map (ID)**
: The Map ID to warp to.

**spawn (number)**
: Spawn point number to warp to.

---

### Moveto
Moves the player to the given coordinates by taking the straight-line path.

```json
moveto(x,y,direction)
```
**x (number)**
: X-coordinate of the tile to move to.

**y (number)**
: Y-coordinate of the tile to move to.

**direction (direction)**
: The direction the player should face while moving.
**Default**: The dirction the player entered the tile facing.

---

## Terrain Actions 

---

### Cut
Creates a tree with an image that can be cut down with the move “Cut”.

```json
cut(encounter_list,sprite)[&triggers]
```
**encounter_list (string)**
: Encounter list to use when player cuts down the object. See encounters code.

**sprite (sprite sheet)**
: Sprite that displays as the object to be cut.
**Default**: Region sprite.

---

### Rock Smash
Creates a rock or object with an image that can be cut down with the move “Rock Smash”.

```json
rocksmash(encounter_list,sprite)[&triggers]
```
**encounter_list (string)**
: Encounter list to use when player smashes the rock or object. See encounters code.

**sprite (sprite sheet)**
: Sprite that displays as the rock or object to be smashed.
**Default**: Region sprite.

---

### Surf
Allows the player to begin surfing across the specified tile area, using the move "Surf".

```json
surf(direction)
```
**direction (direction)**
: Direction to begin surfing in. Replace 'direction' with direction name.
**Default**: Surf from any direction.

---

### Strength
Creates a heavy object that can be pushed with the move “Strength.”

```json
strength(sprite,slide)[&triggers]
```
**sprite (sprite sheet)**
: Sprite that displays as the object to be pushed.
**Default**: Region Sprite.

**slide (0/1)**
: Slide in one direction on touch?
**Default**: 0

---

## Overworld Actions or Effects

---

### Glow
Creates a circular glow effect around the tile.

```json
name=glow(radius,color,flicker)
```
**name (string)**
: Name of the glow to refer to it elsewhere. Can be `%random%`.

**radius (number)**
: Radius of the glow in pixels.

**color (rgba)**
: Colour of the glow, in red, green, blue and alpha channels.

**flicker (unit interval)**
: Strength of the flicker, where `0` is no flicker and `1` is full flicker.

---

### Slide
Causes the player to slide in the direction indicated until they hit a solid wall or warp.

```json
slide(direction)
```
**direction (direction | stop)**
: Direction to slide the player in. Use `stop` to use this tile to stop a player if they are sliding.
**Default**: Player will slide in the direction they were facing.

---

### Spin
Causes the player to spin in the direction indicated until they hit a solid wall or warp.

```json
spin(direction)
```
**direction (direction | stop)**
: Direction to spin the player in. Use `stop` to use this tile to stop a player if they are sliding.
**Default**: Player will spin in the direction they were facing.

---

### Height
Creates an invisible wall with the specified height. If short enough, the wall can be jumped over.

```json
height(height)
```
**height (number)**
: Height in pixels the player must jump to cross the tile.

---

## Encounter Effects

---

### Encounters
Allows encounters of the given type to pop up on this tile. Encounters are created and named for each map.

```json
encounter(type)
```
**type (string)**
: The name of the encounter list, the encounter tile will link to.

---

### Grass
Creates an animation and overlay over the player while they are on the tile.

```json
grass(image,frames,speed,overlay_sprite,loop)&triggers
```
**image (sprite sheet)**
: Sprite sheet with overlay animation. Frames should be evenly spaced horizontally.

**frames (number)**
: Number of frames in the animation sprite sheet.

**speed (number)**
: Speed of the animation in frames per second. (s)

**overlay_sprite (sprite sheet)**
: Single static sprite to overlay over player.

**loop (`loop`)**
: Use `loop` to loop the animation indefinitely.

---

### Ripple
Creates an animation and overlay over the player while they are on the tile.

```json
ripple(animation,frames,speed,overlay_sprite,loop)&triggers
```
**animation (sprite sheet)**
: Sprite sheet with overlay animation. Frames should be evenly spaced horizontally.

**frames (number)**
: Number of frames in the animation sprite sheet.

**speed (number)**
: Speed of the animation in frames per second. (s)

**loop (`loop`)**
: Use `loop` to loop the animation indefinitely.

---

## Additional Functions

---

### Execute
Executes game triggers immediately when the map loads. To make the triggers tile specific, use `if ontile` before this code. See `ontile`.

See the Triggers reference list for a list of triggers to use.

```json
execute(triggers)
```
```json
execute(triggers)&triggers
```
```json
&triggers
```
**triggers (string)**
: String of triggers to execute. The first trigger should not start with an ampersand, but all chained triggers should.

---

### Heal
Heals the player’s party and creates a healing animation like the one used in a Pokémon Center.

```json
heal(sprite,ball_width,ball_height,ball_offset_x,ball_offset_y,ball_margin_x,ball_margin_y)
```
**sprite (sprite sheet)**
: Healing sprite sheet. Poké Balls must be in the lower left-hand corner. Machine must be in the upper left-hand corner.

**ball_width (number)**
: Width of the individual ball sprite in pixels.

**ball_height (number)**
: Height of the individual ball sprite in pixels.

**ball_offset_x (number)**
: Number of pixels to displace the drawing of the Poké Ball sprites in the x-direction.
**Default**: 0

**ball_offset_y (number)**
: Number of pixels to displace the drawing of the Poké Ball sprites in the y-direction.
**Default**: 0

**ball_margin_x (number)**
: The number of pixels to draw between the Poké Balls in the x-direction.
**Default**: 0 (touching)

**ball_margin_y (number)**
: The number of pixels to draw between the Poké Balls in the y-direction.
**Default**: 0 (touching)
