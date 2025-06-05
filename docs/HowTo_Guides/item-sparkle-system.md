# Kyledove's Item Sparkle System

## Introduction

Since Pokengine is an MMO, players naturally spend much more time in-game than in a typical Pokémon title. To support this, I’ve developed a regenerating ground item system, inspired by the item spawns in Scarlet/Violet.

This system serves multiple important purposes:
- Rewards long-term play by providing players with small, randomized pickups across maps.

- Supports game economy in regions where repeat trainer battles aren’t available - players can sell what they find.

- Adds route variety – players can explore different paths, make unique discoveries in varying orders, and even revisit the same maps with fresh experiences.

- Limited time - Item sparkles only appear for a short period before disappearing and respawning elsewhere, adding a fun sense of urgency and a risk-reward element to exploring and cutting through grass.

This helps keep maps feeling fresh and encourages exploration, especially for returning players.

## Implementing the System

To use this system, create a root object with the following code;
```json
random[]

if var[%random%]<time-900
execute(var[%random%])

if day
if !var[%random%] and random[3]=1
xy(0,-1)
animation(1995/ground-sparkle,bottom,0,0,11,11,15,150,loop)
xy(0,0)
msg()&item=list[hidden_items]&var[%random%]=%time%

if night
if !var[%random%] and random[3]=1
xy(0,-1)
%random2%=animation(1995/ground-sparkle-night,bottom,0,0,11,11,15,150,loop)
xy(0,0)
msg()&item=list[hidden_items]&var[%random%]=%time%
%random2%.color(0)
```

!!! warning "Exploitation"

    Players can exploit this system by pressing F5 to force new sparkles to generate.

!!! note "Map Connections"

    Sparkles on sidemaps may disappear when crossing the boundary to the next map.


The following code will also need to be present in the region vars:
```json
list[hidden_items]=[item,chance]
// pecha berry
list[hidden_items][0]=[06jyr7j1,30]
// leppa berry
list[hidden_items][1]=[061u23fv,30]
// chesto berry
list[hidden_items][2]=[0646r0er,30]
// persim berry
list[hidden_items][3]=[06vbo5vd,30]
// oran berry
list[hidden_items][4]=[067mq2j9,30]
// rawst berry
list[hidden_items][5]=[06xm3w1d,30]
// cherri berry
list[hidden_items][6]=[06d0d6k6,30]
// clay fragment
list[hidden_items][7]=[068pws18,30]
// poke ball 
list[hidden_items][8]=[06xa6ohm,10]
// potion 
list[hidden_items][9]=[06a1u97i,10]
// tiny mushroom
list[hidden_items][10]=[06n02aq6,7]
// ether
list[hidden_items][11]=[06l14zew,5]
// revive
list[hidden_items][12]=[06nsq383,4]
// elixir
list[hidden_items][13]=[06c18pt1,3]
// rare candy
list[hidden_items][14]=[06a3mg8b,2]
// big mushroom
list[hidden_items][15]=[06tqdlf2,2]
```

This is my go-to setup, but feel free to customize it. You can even swap the sparkle animation for something different - for example, in Berry Forest, I use a generic berry sprite.

!!! warning "Item Pool"

    When changing the item pool, be careful not to upset game balance by including items that should remain rare, like nuggets or mints. Please reach out to an Admin to ensure you’re not violating any guidelines.


!!! tip "Additional Uses"

    Use this system on surf routes to break up the monotony and keep the journey engaging! I created a separate item list for this purpose, featuring items like Muscle Feather, Resist Feather, etc.
