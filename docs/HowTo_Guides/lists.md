# Lists in jCoad

## Introduction

Lists are a custom way to store and access repeating information in jCoad.

## General Purpose Use

The general formatting is
```json
list[name]=[data1,data2]
```
The names `data1` and `data2` do not matter (except in the case of `&item=` triggers). For example,
```json
list[trainers]=[id,name]
list[trainers][0]=[3500,Derrick]
list[trainers][1]=[3307,Ronda]
list[trainers][2]=[2469,Tasha]
```
To use the list, you can stringitize the call like:
```json
// Roll RNG from 0-2
if !mapvar[rng]
  execute(mapvar[rng]=%random[3]%-1)

// Fight Dude
if mapvar[rng]=0
  msg(You'll be facing %list[trainers][0].name%!)&battle=%list[trainers][0].id%
        
// Fight Kyle
if mapvar[rng]=1
  msg(You'll be facing %list[trainers][1].name%!)&battle=%list[trainers][1].id%

// Fight Jext
if mapvar[rng]=2
  msg(You'll be facing %list[trainers][2].name%!)&battle=%list[trainers][2].id%
```
Alternatively, you can loop over the list with `loop` and `n`:
```json
// Build trainer names list
list[trainer_names]=[rng,name]
list[trainer_names][0]=[0,Derrick]
list[trainer_names][1]=[1,Ronda]
list[trainer_names][2]=[2,Tasha]

// Build corresponding trainer battle IDs
list[battle_ids]=[rng,id]
list[battle_ids][0]=[0,3500]
list[battle_ids][1]=[1,3307]
list[battle_ids][2]=[2,2469]

// Roll RNG from 0-2
if !mapvar[rng]
  execute(mapvar[rng]=%random[3]%-1)

// Loop over names/battle IDs
loop x3
if mapvar[rng]=list[trainer_names][n].rng
  msg(You'll be facing %list[trainer_names][n].name%!)&battle=%list[battle_ids][n].id%
```
Here, `n` takes on the values of `0`, `1`, and `2` (in that order). This is especially useful for large lists (for example, a pool of 20 battlers).

## Giving Items

The [`&items=`](<https://pokengine.readthedocs.io/en/latest/Code_Library/triggers/#item>) trigger has a specially coded interaction with lists. Specifically, when the data are `[item,chance]`, the trigger automatically selects a random entry and respects its odds:
```json
list[berries]=[item,chance]

//Aspear Berry - 20% chance
list[berries][0]=[06ow9sqg,20]

//Cheri Berry - 20% chance
list[berries][1]=[06d0d6k6,20]

//Chesto Berry - 60% chance
list[berries][2]=[0646r0er,60]

// The berry woman hands out berries once per map visit
BerryWoman=npc(01grqmnb,down)
if mapvar[got_berries]
  BerryWoman.msg(No berries yet! Leave the area and come back soon.)
else
  BerryWoman.msg(Have some berries from me, on the house!)&item=list[berries]&mapvar[got_berries]=1
```
This always gives one item, but you can modify the call like `&item=list[berries],3` or `&item=list[berries],%random[5]%`.