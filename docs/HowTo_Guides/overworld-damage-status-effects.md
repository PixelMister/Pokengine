# Overworld Damage & Status Effects

## Introduction

Sometimes, your Pokémon may take damage or be afflicted by a status condition while exploring the overworld, outside of battle. This can be used to add environmental hazards, scripted events, or immersive cutscenes.

## Overworld Damage Trigger
To apply damage, use the following trigger:
```json
&damage=damageNumber,target
```

```json title="Code Examples"
damage=25%,first - Deals 25% damage to the first Pokémon in the party.
damage=10,3 - Deals 10 HP to the Pokémon in slot 3.
damage=500,all - Deals 500 HP to every Pokémon.
damage=50%,last - Deals 50% damage to the last party member.
damage=100% - Deals 100% damage to the first Pokémon by default.
damage=-50%,random - Heals 50% HP to a random party Pokémon (negative values heal).
Parameters
damageAmount can be a raw number (e.g. 20) or a percentage (e.g. 25%).
target (optional):
first - First available Pokémon.
last - Last Pokémon in the party.
all - All party Pokémon.
1 to 6 – Specific slot
random - A random party Pokémon.
If omitted, it defaults to first.
```

!!! tips "Healing"

    Healing: Use a negative damage value to heal Pokémon. This works for both flat numbers and percentages, and will even revive fainted Pokémon.

> 💡 **Credit**: The Move Relearner system was developed by **Skur**.


## Status Affliction Trigger
You can inflict status conditions on a player’s Pokémon using the status trigger, often in conjunction with a scripted environment hazard.

```json title="Electric Shock System Example (Borovia Lab)"
if ontile and mapvar[teslaon]=3
msg(The electricity sent a shock through you and your Mons!)
execute(flash&icon=1&status=paralyzed)
```

This will:

- Display a flash effect.

- Show the default status icon.

- Apply the Paralyzed status to your entire party of Pokémon.

- You can swap paralyzed with any valid status condition:
    * poisoned
    * burned
    * frozen
    * asleep

!!! warning "Status Coverage"

    Status is currently applied to the entire party, and it’s unclear if support exists for:
    Targeting individual Pokémon.
    Applying advanced statuses like badly poisoned or fainted.