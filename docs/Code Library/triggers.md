# Triggers
## Programming

### Pause
Pauses trigger execution for a given amount of time.
```json title="&pause" 
&pause=ms
```
**ms***(number)*
: Time in milliseconds to wait before preceding.

### With
Targets the following triggers on the given entity.
```json title="&with" 
&with=targetname
```
**targetname***(string)*
: New target name.
**Default**: Re-targets the player.

### Variable
Updates the variable.
```json title="&var" 
&var[name]=value
```
**name***(string)*
: **REQUIRED**: Name of the variable.

**value***(string)*
: New value of the variable.

### Map Variable
Updates the map variable.
```json title="&mapvar" 
&mapvar[name]=value
```
**name***(string)*
: **REQUIRED**: Name of the map variable.

**value***(string)*
: New value of the map variable.

### Event Variable
Updates the event variable.
```json title="&ev" 
&ev[name]=value
```
**name***(string)*
: **REQUIRED**: Name of the event variable.

**value***(string)*
: New value of the event variable.

## Entity Manipulation
### Freeze
Freezes the target and prevents player input.
```json title="&freeze" 
&freeze=target
```
**target***(string)*
: Target to freeze.
**Default**: Player

### Unfreeze
Unfreezes the target and allows player input.
```json title="&unfreeze" 
&unfreeze=target
```
**target***(string)*
: Target to unfreeze.
**Default**: Player

### Destroy
Unfreezes the target and allows player input.
```json title="&destroy" 
&destroy=target
```
**target***(string)*
: Target to destroy.
**Default**: The current target.

### Jump
Causes the target to jump.
```json title="&jump" 
&jump=height
```
**height***(number)*
: Number of pixels the target will jump by.
**Default**: 8 pixels.

### Direction
Causes the target to face the given direction.
```json title="&direction" 
&direction=u or &direction=up
&direction=d or &direction=down
&direction=l or &direction=left
&direction=r or &direction=right
```
**direction***(string)*
: The name of the direction the target will face.

### Path
Moves the target along the given path.
```json title="&path" 
&path=path
```
**path***(path)*
: Path for the target to follow.
**Default**: Unsets the current path.

### Speed
Sets the targets speed. Can be used on the player.
```json title="&speed" 
&speed=percentage
```
**percentage***(percentage)*
: Percentage of normal speed. Use `50` for half speed or `200` for double speed.
**Default**: 100

### Icon Bubbles
Places an animated icon bubble above the targets head. Can be used on the player.
```json title="&icon" 
&icon=id
```
**id***(number)*
: Icon ID to display.

**Default**: Removes any icon.

Icon Name | ID | Symbol
------------|-------------|-------------
Exclamation | 1 | ![alt text](image.png)
Ellipses | 2 | ![alt text](image-1.png)
Smiley Face | 3 | :)
Music Note | 4 |
Comma | 5 | ,
Joyful Face | 6 | ^_^
Heart | 7 | <3
Sad Face| 8 | :[
Smiling Face with Open Mouth | 9 | :D
Fish Icon | 10 | <><
Angry Face | 11 | >:(
Battle | 12 | Battle Icon
Haha | 13 | Ha Ha
No. 1 | 14 | 1
No. 2 | 15 | 2
No. 3 | 16 | 3
No. 4 | 17 | 4
No. 5 | 18 | 5
Poisoned | 19 | 
Surprised Face | 20 | o_o
Shaking Head | 21 |
Question Mark | 22 | ?
Asleep | 23 | Zzz
Sweat Drop | 24 | 
Skull (Dead) | 25 | 
Big Red Exclamation Mark | 26 |
Spectating Eye | 27 | Eye
Crying/Screaming | 28 | 
Egg | 29 | Egg
Flight Icon | 30 | White Wing on Blue Bg
Spanish Flag | 31 | Spanish Flag
Star No 1 | 32 | Number 1 with star on grey bg
Star No 2 | 33 | Number 2 with star on grey bg
Star No 3 | 34 | Number 3 with star on grey bg
Star No 4 | 35 | Number 4 with star on grey bg
Star No 5 | 36 | Number 5 with star on grey bg
Quest (Not Started) | 37 | Quest ?
Quest (In Progress) | 38 | Quest ...
Quest (Completed) | 39 | Quest !
Healer | 40 | + Symbol
Shop | 41 |
TM | 42 |
French Flag | 43 | French Flag
Gift | 44 | 
Quest Star | 45 | Quest Star

### XY Coordinates
Instantly warps the target to the specified coordinates on the current map.
```json title="&xy" 
&xy=x,y
```
**x***(number)*
: X-coordinate to warp to.

**y***(number)*
: Y-coordinate to warp to.

### Moveto Coordinates
Moves the target to the specified coordinates on the current map by taking the straight-line path.
```json title="&moveto" 
&moveto=x,y,direction
```
**x***(number)*
: X-coordinate to move to.

**y***(number)*
: Y-coordinate to move to.

**direction***(string)*
: Direction to face while moving.

**Default**: Current Direction

### Follow
Forces the current target to follow another target.
```json title="&follow" 
&follow=target
```
**target***(string)*
: Specify the target to follow.

**Default**: Unfollows.

### Behind Player
Puts the current target behind the player.
```json title="&behindplayer" 
&behindplayer
```
### Outfit
Sets the target’s skin.
```json title="&outfit" 
&outfit=skin
```
**skin***(skinid)*
: Specify the skin ID for the target to change to.

### Texture
Sets the target’s texture.
```json title="&texture" 
&texture=sprite
```
**texture***(sprite sheet)*
: Texture sprite to change to.

### Skin Color
Sets the target’s skin color.
```json title="&skincolor" 
&skincolor=id
```
**id***(number)*
: Skin color ID to change to.

**Default**: 0