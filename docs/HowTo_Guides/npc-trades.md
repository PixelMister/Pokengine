# NPC Trades
## Introduction
The following How-To guide, will detail how to create a Pokemon trade within your region.

```json title="Trade Event from Sinnoh Region"
%random%=npc(01b8skxh,down,0x0)
if !ev[trademachop]
%random%.msg(Listen, listen. Do you have a Pokemon called Machop?|Would you be willing to trade your Machop for my Abra?)&answers=Yes,No
Yes=%random%.answer()&trade[0067l3yb]=007afz55;l same
No=%random%.answer(Oh, OK...#Well, I can't make you trade me.|But if you change your mind, I'll be right here waiting!)
if traded and ontile=%random%
msg(Be nice to my Abra!|I'll be sure to look after your Machop in return!)&ev[trademachop]=1
if ev[trademachop]=1
%random%.msg(Thanks to Pokemon, I got to be friends with you!)
```
This event uses the keyword `same` to ensure that the Pokémon received in the trade matches the level of the one traded away.

While you can add a check to confirm the player has a specific Pokémon in their party, the trade screen accesses the entire PC, making it a better user experience to avoid that restriction. (There’s currently no way via jCoad to check for a Pokémon is stored in the PC.)

!!! danger "Default Behaviour Flaw"

    There is a significant flaw with this system due to default engine behavior:
    
    If a player opens the trade screen but cancels the trade, the game will still treat the trade as if it succeeded. This means the player can permanently miss out on receiving the intended Pokémon. There is an open bug report raised for this.