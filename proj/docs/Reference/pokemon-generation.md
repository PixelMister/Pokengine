# Pokemon Generation
Pokemon are complex creatures. There are dozens of ways in which they can be customised and configured for battling or spawning. 

Pokemon can be generated through the use of generation strings, which are a series of options separated by semicolons. 
For instance, 
```00bxxu0w,level 25;male``` would generate a Male, Level 25, Pikachu belonging to the the region, Nintendo. If given to the ```&battle``` trigger, a battle with this wild Pokemon would be initiated. If given to the &mon trigger, the Pokemon would be given directly to the player.

Pokemon Identification
The first option in the generation string should be an identification string. This string identifies the exact Pokemon, stored in one/multiple dexes on Pokengine. 

## Unique Identifier
Set the Pokemon’s unique identifier. This is found on their dex page.
```json title="uid | id" 
uid
id
```

## Dynamic Levelling
Allows the Pokemon's level to scale using dynamic levelling.
```json title="dynamic-level | d" 
dynamic-level
d level
```

## Level
Set the Pokemon’s level. Can be a single number, multiple comma-separated values, or a range of values. Use ```same``` if initiating a trade and you want the new Pokemon to be the same level as the traded Pokemon.
```json title="level | lv | l" 
level levels
lv levels
l levels
```
```json title="Level Example" 
00bxxu0w;level 5
00bxxu0w;level 5,10,15
00bxxu0w;level 5-15
00bxxu0w;level same
```
## Nickname
Set the Pokemon’s nickname.
```json title="nickname | nick | name | n" 
nickname name
nick name
name name
n name
```
## Genders
Set the Pokemon's gender to Male.
```json title="male | m" 
male
m
```

Set the Pokemon's gender to Female.
```json title="female | f" 
female
f
```

## Status Effects
Set the Pokemon’s status. A Pokemon's status is determined by stating the affliction, after the word 'status'.
```json title="status | q" 
status
q
```
```json title="Code Examples" 
status asleep
q asleep
status poisoned
q poisoned
status burned
q burned
status badly poisoned
q badly poisoned
status paralysed
q paralyzed
```
**Available Options**

[Frozen]( "Causes the generated Pokemon to be frozen."),
[Asleep]( "Causes the generated Pokemon to be asleep."),
[Poisoned]( "Causes the generated Pokemon to be poisoned."),
[Burned]( "Causes the generated Pokemon to be burned."),
[Badly Poisoned]( "Causes the generated Pokemon to be badly poisoned."),
[Paralyzed]( "Causes the generated Pokemon to be frozen.").

## Current HP
Set the Pokemon's current HP value. This is not Max HP or the HP stat.
```json title="hp | h" 
hp hp
h hp
```
```json title="Code Examples" 
hp 20
h 20
```
## Pokemon Ability
Set the Pokemon's Ability Slot. Omit code, for a random ability from the Pokemon's dex page.
```json title="ability | a" 
ability ability
a ability
```
```json title="Code Examples" 
ability 1
a 1
```
**Available Options**

- **Omitted** | Random Ability from their dex information.

- **1** | This will Pokemon will have the ability designated on their dex page as Ability 1.

- **2** | This will Pokemon will have the ability designated on their dex page as Ability 2.

- **HA** | This will Pokemon will have the ability designated on their dex page as Hidden Ability.

## Pokemon Nature
Set the Pokemon's Nature to one of twenty four possible options. Omit the code, for a random nature.
```json title="nature | p" 
nature nature
p nature
```
```json title="Code Examples" 
nature 1
p 1
```
**Available Options**

Nature | ID| Stat Increase | Stat Decrease
-------------|-------------|-------------|
Random | 0 | N/A | N/A
Hardy | 1 | Atk | Atk
Lonely | 2 | Atk | Def
Brave | 3 | Atk | Spd
Adamant | 4 | Atk | Sp.Atk
Naughty | 5 | Atk | Sp.Def
Bold | 6 | Def | Atk
Docile | 7 | Def | Def
Relaxed | 8 | Def | Spd
Impish | 9 | Def | Sp.Atk
Lax | 10 | Def | Sp.Def
Timid | 11 | Spd | Atk
Hasty | 12 | Spd | Def
Serious | 13 | Spd | Spd
Jolly | 14 | Spd | Sp.Atk
Naive | 15 | Spd | Sp.Def
Modest | 16 | Sp.Atk | Atk
Mild | 17 | Sp.Def | Def
Quiet | 18 | Spd | Spd
Bashful | 19 | Sp.Atk | Sp.Atk
Rash | 20 | Sp.Def | Sp.Def
Calm | 21 | Sp.Def | Atk
Gentle | 22 | Sp.Def | Def
Sassy | 23 | Sp.Def | Spd
Careful | 24 | Sp.Def | Sp.Atk
Quirky | 25 | Sp.Def | Sp.Def

## Pokemon Moves
Set the Pokemon's moveset by referencing the move id.
```json title="moves | o" 
moves moveid1,moveid2,moveid3,moveid4
o moveid1,moveid2,moveid3,moveid4
```
```json title="Code Examples" 
moves 077lfqoy (This would place Absorb in Move Slot 1)
o 077lfqoy (This would place Absorb in Move Slot 1)
```

## Pokemon Held Item
Set the Pokemon’s held item, through referencing the Item Id.
```json title="item | b" 
item itemid
b itemid
```
```json title="Code Examples" 
item 06a1u97i (This would give the Pokemon a potion.)
b 06a1u97i (This would give the Pokemon a potion.)
```

## Pokemon Happiness/Friendship Value
Set the Pokemon’s happiness/friendship value. Should be between 0 and 255, inclusive.
```json title="happiness | friendship | w" 
happiness value
friendship value
w value
```
```json title="Code Examples" 
happiness 120 (This would set the happiness/friendship value at 120)
friendship 120 (This would set the happiness/friendship value at 120)
w 120 (This would set the happiness/friendship value at 120)
```
## Pokemon Eggs
Set the Pokemon as an egg with the given number of steps required to hatch. Each egg cycle, corresponds to 255 steps.

```json title="happiness | friendship | w" 
egg steps
y steps
```
```json title="Code Examples" 
egg 255 (This Pokemon will be generated as an egg and require 255 steps to hatch.)
y 255 (This Pokemon will be generated as an egg and require 255 steps to hatch.)
```

## Pokemon Individual Values (IVs)
Set the Pokemon’s IV Values, for each one of its six stats.

```json title="ivs | i" 
ivs iv_values
i iv_values
```
```json title="Code Examples" 
ivs 31,0,31,31,31,31 (This would give the Pokemon, 31 IVs in its HP, Def, Sp.Atk, Sp.Def and Spd stats.)
i 31,0,31,31,31,31 (This would give the Pokemon, 31 IVs in its HP, Def, Sp.Atk, Sp.Def and Spd stats.)
```

## Pokemon Effort Values (EVs)
Set the Pokemon’s EV Values. Each Pokemon is limited to 508 effort points in total. 252 are required to maximise a stat.

```json title="evs | e" 
evs ev_values
e ev_values
```
```json title="Code Examples" 
evs 252,0,0,0,4,252 (This would give the Pokemon, 252 EVs in its HP and Spd stats, as well as the four remaning in Sp.Def)
e 252,0,0,0,4,252 (This would give the Pokemon, 252 EVs in its HP and Spd stats, as well as the four remaning in Sp.Def)
```
## Shiny Pokemon
Set the Pokemon as shiny or not. Use ? for a random chance of shiny. Use no or 0 for shiny locked.

```json title="shiny | s" 
shiny value
s value
```
```json title="Code Examples" 
shiny 1 (Makes the Pokemon a Shiny Pokemon)
s 1 (Makes the Pokemon a Shiny Pokemon)
```
**Available Options**

Value| Function |
-------------|-------------|
0/No | The Pokemon is Shiny Locked.
1 | The Pokemon is now a Shiny Pokemon.
2 | The Pokemon is now a Golden Shiny Pokemon.
? | The Pokemon has a random chance of being a Shiny Pokemon.

## Pokemon Caught Data
Set the Pokemon’s caught data. Caught strings are another type of string that must be formatted. Every option must appear continuously.

```json title="caught | c" 
caught caught_string
c caught_string
```
```json title="Code Limiters" 
@[time] - Set the time when caught.
By[player_id] - Set the player who caught the Pokemon.
In[item_id] - Set the Poke Ball the Pokemon was caught in.
On[map_id] - Set where the Pokemon was caught.
Lv[level] - Set what level the Pokemon was caught at.
```









