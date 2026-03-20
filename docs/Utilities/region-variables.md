# Region Vars

Sometimes you’ll want to adjust global settings across your region without needing to inject code into every map - that’s what **Region Vars** are for.

Region Vars are loaded once, when the player first enters your region. They let you set default behaviors and mechanics for your maps and gameplay. Think of them as your region’s global ruleset.

`var[max_allies]=1`  
How many allies can follow the player out of their Pokéballs (max. 6)

`var[max_mon_level]=20`  
Level cap - can be changed later with JCoad as the player progresses.

!!! Danger 

    Any Pokémon transferred in above this level will be scaled *down* to the cap. This means unhappy players.

`var[autoevolve_all]=mode`  
When [dynamic leveling](<https://pokengine.readthedocs.io/en/latest/Code_Library/pokemon-generation/#dynamic-levelling>) is active, sometimes it makes sense for the Pokémon to be automatically evolved already. This is great for situations where the player might otherwise encounter a level 25 Caterpie.

See also [Battle Properties - Automatic Evolution](<https://pokengine.readthedocs.io/en/latest/Code_Library/battle-properties/#automatic-evolution>).

`var[move_learner_context]=1`  
Allows move relearning directly from the party menu.

`var[jump_height]=8`  
How high the player can jump.

`var[show_trainer_spot]=0`  
Disables the "trainer spot" overlay effect.

`var[silent_icons]=0`  
Silences the default SFX that plays on overworld icons (like !).

`var[no_shadow]=0`  
Toggles whether overworld sprites have shadows.

`var[item_shadow]=1`  
Whether pickup items cast shadows. If off, you can include custom shadows in the sprite.

`var[regional_outfits]=0`  
Only shows outfits in the bag that match the region you're in.

`var[can_run]=1`  
Toggle ability to run.

`var[follow_speed]=1`  
Sets follower speed to match the player’s.

`var[can_cycle_on_water]=0`  
Allows the player to cycle on water.

`var[can_cycle_indoors]=0`  
Allows the player to cycle indoors (useful for caves).

`var[can_cycle]=0`  
At map load, turns on or off depending on whether the map is an interior. You can change it with an `execute()`.

`var[must_cycle]=0`  
Prevents the player from dismounting. It's set to 0 at map load, but can also be toggled after.

`var[can_dismount_bike]=0`  
Setting this var to 1 will prevent the player from dismounting their bicycle - Useful for cycling road areas!

`var[disobedience]={20: badge-1}`  
Sets level cap disobedience. See “Disobedience System” for more info.

## ⚠️ Region Vars You Shouldn’t Touch
These vars exist but are core to balance, so avoid changing them unless approved by Kyle.

`var[battle_exp]=100`  
Base EXP gain rate.

`var[battle_exp_participated]=75`  
EXP percentage for participants (when EXP All is active).

`var[battle_exp_party]=33`  
EXP percentage for non-participants (when EXP All is active).

`var[max_dynamic_level]=65`  
Upper limit for dynamic levels.

`var[min_dynamic_level]=1`  
Lower limit for dynamic levels.

`var[ally_happiness_steps]=128`  
Steps needed to trigger happiness gain.

`var[ally_happiness_chance]=50`  
Percentage chance to gain happiness.

`var[egg_step_multiplier]=1`  
Egg hatch rate modifier.

`var[encounter_chance]=5`  
Default encounter rate, 1 in 5

`var[cave_encounter_chance]=30`  
Default encounter rate in caves, 1 in 30

`var[surf_encounter_chance]=40`  
Default encounter rate while surfing, 1 in 40

`var[min_encounter_count]=10`  
Disable wild encounters the first 10 steps after a battle

## Priority Rules
If the same var is defined multiple times, this is the priority:

- `ev > mapvar > var`

## Other Notes
Region Vars are still vars: You can modify them anywhere with jcoad.

- ``Example: execute(var[max_mon_level]=30)``

## Persistent Changes

- Any change made in Jcoad will be saved unless you reset it.

- For temporary or map-specific settings, use mapvar instead.

- If you want it to persist long-term and across maps, use an ev.

!!! Warning

    Region Vars only support `var` and `list` – you can’t use full jcoad logic inside them.
