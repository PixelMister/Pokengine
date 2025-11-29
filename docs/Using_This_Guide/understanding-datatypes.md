# Understanding Data Types
jCoad does not really have data types, but putting arguments into the proper format for object functions, properties, and triggers is absolutely necessary for your code to work properly. Use this guide to understand how to enter arguments into your jCoad.

## Binary Values (Numerical)
A binary digit, representing a boolean value. 1 represents “yes,” “on,” or “true,” while 0 represents “no,” “off,” or “false.”
```json title="(type) 0/1" 
0/1
```
## Binary Values (Written)
Two options representing a boolean choice:  `yes` or `no`
```json title="(type) 0/1" 
0/1
```
## Area
An area, represented by two integers separated by an “x.” Use the format `mxn`, where `m` and `n` are integers.
```json title="(type) area" 
area
mxn
```
## Depth
A depth string that indicates the depth of a sprite or animation drawn in the game. Depth strings consist of a base position and an optional offset.
```json title="(type) depth" 
depth=()
```

Value | Function
--------------|-------------
void | Depth offest is relatvive to the void, or the map background.
back | Depth offset is relative to just above the background, or always behind the player.
bottom | Depth offset is relative to the map but behind the shadows.
map | Depth offset is relative to the base position on the map. `n` is the number of pixels in front of the object the player needs to be to appear in front of it.
fore | Depth offset is relative to just abouve the foreground or always above the player.
hud | Depth offset is relative to above the weather. The hud canvas is actually separate from the game canvas: game < weather < hud < fadeout.

The pixel offsets (`+n` or `-n`)especially when working with a depth other than `map`, are primarily used to place objects relative to one another.

```json title="Code Examples" 
map+16
void+5
fore-5
bottom+293
fore
back
```
## Hex Codes
A hexadecimal color in the format  `#[0-F]{6}
```json title="(type) hex" 
#000000 => Black
#FFFFFF => White
#F75D5D => Red
#13A10E => Green
```
## RGB Colour Values 
A color given in RGB (red-green-blue) format. Three RGB values separated by commas.
```json title="(type) rgb" 
255,0,0 => Red
232,66,255 => Pink
```
## RGBA Colour Values 
A color given in RGBA (red-green-blue-alpha) format. The format is `0-255,0-255,0-255,0-1`. Only the final number can be a floating-point value.
```json title="(type) rgb" 
255,0,0,1 => Red, 100% opacity
255,0,0,0.5 => Red, 50% opacity
```
## Numbers
A string of numeric digits, such as `256` or `-3`.
```json title="(type) number" 
1
```
## Object Direction
A direction the object can face.
```json title="(type) direction" 
direction=up
direction=down
direction=left
direction=right
```
## Short Direction
Exactly like `direction`, but only using the first character.
```json title="(type) short direction" 
direction=u
direction=d
direction=l
direction=r
```
## Paths
A path string that represents a string of tile movements. In their simplest form, path strings specify the number of tiles to move followed by the direction to move in (represented as a single character). For example, `3d` represents moving 3 tiles down. Multiple moves can be strung together by separating them with commas. Add an asterisk on the end of the string to signify the path should repeat indefinitely. There are also a few special keywords that can be used as shortcuts for some common paths.
```json title="(type) path" 
1u,3l,3d,2r => 1 up, 3 left, 3 down, 2 right
3u,3d* => 3 up, 3 down, repeat indefinitely
circle => 1r, 1d, 1l, 1u*
spin => 0r,0d,0l,0r
twirl => spin once, ending on the direction it initiates with.
```
## Percentage
An integer representing a percentage.
```json title="(type) percentage" 
0 => 0%
50 => 50%
75 => 75%
100 => 100%
200 => 200%
```
## Unit Interval
A floating-point number between 0 and 1 (inclusive). Usually used for representing percentages.
```json title="(type) unit interval" 
0
0.125
0.783
1
```
## Pokémon
A Pokemon Generation String.
```json title="(type) pokémon" 
00bxxu0w,level 25;male
```
## Object Skin
A special type of parameter used to identify overworld skins. Use the ID of the desired skin.
```json title="(type) skin" 
johto youngster=01ih0r1l
```

## Player Outfit (needs completing)
A special type of parameter used to identify overworld outfits. Use the ID of the desired outfit.
```json title="(type) outfit" 
johto youngster=01ih0r1l
```
## Sprite Sheet
A link to an internal sprite sheet (uploaded to Pokéngine) that you or another user owns. The format is `user_id/sprite_sheet_name`. This is accompanied by either `.png` or `.webp` as its file type extension.
```json title="(type) sprite sheet" 
2654/sprites.png
1995/door.png
```
## Tileset Sheet (needs completing)
A tileset identification string, which takes the format of !n, where n is the tileset ID. Basically just a number with an exclamation point in front of it.
```json title="(type) sprite sheet" 
2654/sprites.png
1995/door.png
```

## String
A string of characters. Some characters may have special meaning for the function or trigger.