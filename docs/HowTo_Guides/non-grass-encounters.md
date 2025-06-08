# Non-Grass Encounters

Experiment with ways to find wild Pokémon beyond just grass encounters.

This section covers unique methods to encounter Pokémon, helping to diversify your players’ experience and keep exploration fresh and exciting.

---

## Static Encounters

```json
if !ev[mewtwo]
%random%=npc(01ze5yny,down)
%random%.msg(Mew!)&battle=00xchwcw;level 70;moves 07zsg76n,07r9zhe8,07lv53s6,075bpbpu;scene 42
if ontile=mewtwo and caught=00xchwcw
execute(ev[mewtwo]=1)
```

To place a pokemon in the overworld that you can interact with to start a battle, see the example above.

!!! danger
    Static encounters should be reserved only for Legendaries or key story moments. We do not allow static encounters for non-Legendary Nintendo Pokémon, as this would severely undermine the integrity of shiny hunting and disrupt the global balance of the MMO. Static encounters can be abused to guarantee shinies with minimal effort - even by scripted bots. While such automation is against the rules, it’s nearly impossible to detect or prove abuse, so use caution.


---

## Cave Encounters (Map-Wide)

[insert image here]

Create an encounter list and assign its name here to have the entire map treated as a potential wild encounter area. Although this is labeled “Cave,” it can be used for forests, deserts, or any environment you choose.

!!! tip "Kyledove's Tip"
    Use code to disable encounters on specific tiles to create “safe zones” within the map while using this system!

---

## Surf Encounters

Likewise, create an encounter list for surf and assign its name here to have surf encounters generate whenever the player is surfing.

[insert image]

---

## Rock Smash

```
rocksmash(rocksmash)
```

Simply create an encounter list named “rocksmash,” and the game will have a chance to generate a wild battle when a player uses Rock Smash.

---

## Beach Shoreline Encounters

```json
if random[3]=1
encounter(waves)
```

This simple setup creates the feel of shoreline encounters, like in Summer Island or Rica.  

With a 1-in-3 chance, wild Pokémon appear while walking near the ocean.

---

## Terrain-Based Surprise Attacks

```json
if ontile and random[6]=1
msg(Something attacked you from the spiderweb!)&!icon=1&!cry=00pnxi7j&battle=00pnxi7j;level 30;scene 51
```

In this example from Borovia, crossing spiderwebs triggers a chance that a spider will leap out and attack you. Combining this with a message, a notification, and the Pokémon’s cry helps create a more immersive and exciting encounter.

---

## Item Mimics

```json
if !ev[mimicFound]
sprite(1995/itemsprite)
msg(What's this?)&cry=00yko4ks&battle=00yko4ks;level 15;scene 1&ev[mimicFound]=1
```

In this example, it generates what seemingly looks like a regular item (make sure it matches your region) but when you interact, it triggers a battle. Once fought, the item is gone forever.

---

## One-Time Daily Interactions

In this example from Fall Festival, interacting with a specific object triggers a one-time Pokémon encounter. To prevent infinite repeats, the encounter resets only once per in-game day.

**Example Code**
```json
solid()
if ev[confectious]=2 and night
execute(ev[confectious]=1&ev[confectiousencountered]=0)
if ev[confectious]=1 and day
execute(ev[confectious]=0)
if ev[confectious]=0 and !ev[confectiousencountered]
msg(What's this?#There's something in the trash can!)&ev[confectiousencountered]=1&cry=00bu1mf8&battle=00bu1mf8;level 7;scene 51
if ev[confectious]!=0
msg(Looks empty... For now.)
```
---
