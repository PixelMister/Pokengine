# Battle Properties
You can set various battle properties, when you call for it to start within an objects code. This applies to both wild battles and trainer battles. The properties are listed below.

# Battle Limiters
## No Running
You cannot run from this battle. This is the default setting for trainer battles, so you only need to specify it for wild battles.
```json title="norun" 
norun
```
## No Catching
You cannot catch the opposing Pokemon. This is the default setting for trainer battles, so you only need to specify it for wild battles.
```json title="nocatch" 
nocatch
```
## No Money
You will not earn money from this battle. This is the default setting for wild battles, so you only need to specify it for trainer battles.
```json title="nomoney" 
nomoney
```
## No Experience Points
Your Pokemon will not gain any experience points from this battle.
```json title="noexp" 
noexp
```
## No Item Use
You will not be able to use items from the bag widget during battle. For example, Poke Balls or Potions.
```json title="noitems" 
noitems
```
## Fixed Pokemon Level
Forces all Pokémon in battle to the specified level. Uses their true stats (IVs, EVs) but calculates the actual stat value (attack, etc) based on the new set level. This works identically to fixed level battles such as the Battle Tower in the mainline games.
```json title="fixedlevel" 
fixedlevel level
```
## Hidden Opposing Pokemon Level
Levels of the opposing Pokémon are hidden. Appears as ???.
```json title="hiddenlevel" 
hiddenlevel
```
# Battle Format
## Double Battles
The battle will be changed to the 'double' format of Pokemon battles. This can be applied to both wild and trainer battles.
```json title="double" 
double
```
## Triple Battles
The battle will be changed to the 'triple' format of Pokemon battles. This can be applied to both wild and trainer battles.
```json title="triple" 
triple
```
# Pokedex Registration
## Not Seen in Pokedex
The opposing Pokemon in this battle, will not be counted as seen in the Pokedex.
```json title="noseen" 
noseen
```
# Battle Scene Alterations
## Battle Environment (Scene)
Sets the battle scene (background image) to the one specified. Only necessary for wild battles, as trainer battles have a scene property set in advance. Additional scenes are added for battles, using the scene context menu in the Mapbuilder editor.
```json title="scene" 
scene id
```

## Battle Theme (needs updating)
Sets the music playing during battle. Currently hosting on Dropbox is supported only. The format is db: for host, then a modified URL which cuts out the https://www.dropbox.com/ part. theme db:s/fo7smcp2luvrikc/BattleTowerSWSHRemix.mp3 — Sets the theme according to this Dropbox shared URL.
```json title="theme" 
theme url
```

# Examples
## Wild Pokemon Boss
This first example is a boss battle against a wild Pokémon. You cannot run or catch it, and the level is hidden. The Pokémon’s name is also set to hide its species.
```json title="Code Example" 
msg(Groouuugoooough!!)&!cry=00bxxu0w&battle=00bxxu0w;level 80;name ???;scene 51;hiddenlevel;nomoney;nocatch;norun
```

## Battle Tower
Battle Tower This example is from the HUB Battle Tower. The dialogue in the `msg()` block and the trainer battle ID are both controlled by a list. The variable `var[noblackout]=1` is set so that the player will not teleport away if they lose the battle.

Similar to the mainline games’ Battle Tower, this battle gives no exp or money, but instead I manually give the player BP if they win (not shown). Items are not allowed, and all participating Pokémon are set to level 50 for the duration of the battle.
```json title="Code Example" 
msg(%list[trainers][n].speech%)&var[noblackout]=1&mapvar[battle]=3&battle=%list[trainers][n].battleid%;noexp;nomoney;noseen;noitems;fixedlevel 50;theme db:s/fo7smcp2luvrikc/BattleTowerSWSHRemix.mp3
```