# Entity Properties

If you are unsure how use these object functions, please refer to other site references (reference link here.)

Any entry propert that ends with `&triggers`, may have an optional string of game triggers appened to them to execute alongside the function. See [text](triggers.md) for more information.

### Path
Defines a path for the entity to follow.
```json
name.path(path)
```
**path***(path)*
: Entity's path.
**Default**: None

### Speed
Defines the entity's walking speed.
```json
name.speed(number)
```
**speed***(number)*
: Percentage value for entity speed. Use `50` for 1/2 speed or `200` for 2x speed.
**Default**: `100`

### Shadow
Sets whether the entity has a shadow or not.
```json
name.shadow([state])
```
**state***(0/1)*
: Should the entity have a shadow?
**Default**: 0 for sprites, 1 for NPCs

### Solid
Sets whether the entity is solid or not.
```json
name.solid([state])
```
**state***(0/1)*
: Should the entity be solid?
**Default**: 0 for sprites, 1 for NPCs

### Ignore
Sets whether the entity is solid or not.
```json
name.ignore()
```

### Float
Sets the entity’s floating height.
```json
name.float([height])
```
**height***(number)*
: Floating height in pixels.
**Default**: 0

### Color
Sets the entity’s color.
```json
name.color([color])
```
**color***(rgb)*
: The color to mask the entity with.
**Default**: Entity completely ignores lighting effects

### Nametag
Gives the entity a nametag.
```json
name.nametag()
```

### Print
Creates a fading trail behind the target.
```json
name.print(type)
```
**type***(string)*
: Type of trail to draw.
**Default**: No trail.

### Outline
Draws a colored outline around the target.
```json
name.outline([color])
```
**color***(rgb)*
: Color of outline.
**Default**: Removes outline

### Ally
Sets the target’s allies, or following entities.
```json
name.ally(ally1 [ally2 [ally3...]])
```
**ally***(skin)*
: Overworld skin of following ally. For multiple allies, separate with spaces.

### Skin Color
Sets the target’s skin color.
```json
name.skincolor(id)
```
**ally***(skin)*
: Skin color ID to change to.
**Default**: 0

### Persistent
By default, entities are destroyed when the player leaves the map or reloads the map. Persistent entities will persist.
```json
name.persistent()
```

### Spot
Allows the entity to spot the player and initiate an interaction.
```json
name.spot(tiles,change_path,spot_through_walls,move_to_spotted)
```
**tiles***(number)*
: Radius, in all directions, the player must be in to be spotted.

**change_path***(0/1)*
: Should the NPC stop their path after spotting the player? If not, the entity will keep moving after spotting the player.
**Default**: 1

**spot_through_walls***(0/1)*
: Can the entity spot the player through walls?
**Default**: 0

**move_to_spotted***(0/1)*
: Should the entity move to the player after spotting?
**Default**: 1

### Opacity
Sets the entity’s opacity.
```json
name.opacity(opacity)
```
**opacity***(percentage)*
: The opacity as a percentage. Use `100` for 100%, or use `50` for 50%.
**Default**: 0

### XY
Offsets the display position of the object.

```json 
name.xy(x,y)
```
**x (number)**
: Set the horizontal offset in pixels. Can be positive or negative values.

**y (number)**
: Set the horizontal offset in pixels. Can be positive or negative values.

**xy(x,y) (number)**
    : Setting the horizontal and vertical offset together in pixels. Can be positive or negative values.

### Depth
Sets the relative depth of the entity.

```json 
name.depth(depth)
```
**depth (number | depth name)**
: Depth of the sprite. If a number is given, it works like `depth+n`.

### Spin
Causes the object to spin.

```json 
name.spin()
```

