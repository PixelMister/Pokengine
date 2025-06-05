# Regional Variables (Region Vars)
## Introduction
Sometimes you’ll want to adjust global settings across your region without needing to inject code into every map - that’s what Region Vars are for.

Region Vars are loaded once, when the player first enters your region. They let you set default behaviors and mechanics for your maps and gameplay. Think of them as your region’s global ruleset.

## Available Variables

### Max Allies
How many allies can follow the player out of their Pokéballs (max. 6)
```json
var[max_allies]=1
```

### Max Mon Level / Level Cap
Level cap - can be changed later with JCoad as the player progresses.
```json
var[max_mon_level]=20
```
!!! danger "Level Scaling on Transfer"

    Any Pokémon transferred in above this level will be scaled *down* to the cap.

### Move Learner Context
Allows move relearning directly from the party menu.
```json
var[move_learner_context]=1
```

### Jump Height
How high the player can jump.
```json
var[jump_height]=8
```

### Trainer Spot Overlay Effect
Disables the "trainer spot" overlay effect.
```json
var[show_trainer_spot]=0
```

### Silent Icons
Silences the default SFX that plays on overworld icons (like !).
```json
var[silent_icons]=0
```

### No Shadow
Toggles whether overworld sprites have shadows.
```json
var[no_shadow]=0
```

### No Item Shadow
Whether pickup items cast shadows. If off, you can include custom shadows in the sprite.
```json
var[item_shadow]=1
```

### Regional Outfits
Only shows outfits in the bag that match the region you're in.
```json
var[regional_outfits]=0
```

### Can Run
Toggle ability to run.
```json
var[can_run]=1
```

### Follower Speed
Sets follower speed to match the player’s.
```json
var[follow_speed]=1
```

### Cycle on Water
Allows the player to cycle on water.
```json
var[can_cycle_on_water]=0
```

### Indoor Cycling
Allows the player to cycle indoors (useful for caves).
```json
var[can_cycle_indoors]=0
```

### Can Cycle
At map load, turns on or off depending on whether the map is an interior. You can change it with an `execute()`.
```json
var[can_cycle]=0
```

### Must Cycle
Prevents the player from dismounting. It's set to 0 at map load, but can also be toggled after.
```json
var[must_cycle]=0
```

### Dismounting Control for Bikes
Setting this var to 1 will prevent the player from dismounting their bicycle - Useful for cycling road areas!
```json
var[can_dismount_bike]=0
```

### Dismounting Control for Bikes
Sets level cap disobedience. See “Disobedience System” for more info.
```json
var[disobedience]={20: badge-1}
```

## Region Vars You Shouldn’t Touch
These vars exist but are core to balance, so avoid changing them unless approved by Kyle or Jext.

### Battle Experience
Base EXP gain rate.
```json
var[battle_exp]=100
```

### Battle Experience from Participation
EXP percentage for participants (when EXP All is active).
```json
var[battle_exp_participated]=75
```

### Battle Experience for Party
EXP percentage for non-participants (when EXP All is active).
```json
var[battle_exp_party]=33
```

### Maximum Dynamic Level
Upper limit for dynamic levels.
```json
var[max_dynamic_level]=65
```

### Minimum Dynamic Level
Lower limit for dynamic levels.
```json
var[min_dynamic_level]=1
```

### Ally Happiness Steps
Steps needed to trigger happiness gain.
```json
var[ally_happiness_steps]=128
```

### Ally Happiness Chance
Percentage chance to gain happiness.
```json
var[ally_happiness_chance]=50
```

### Egg Hatch Rate
Egg hatch rate modifier.
```json
var[egg_step_multiplier]=1
```

### Encounter Rate
Default encounter rate, 1 in 5
```json
var[encounter_chance]=5
```

### Cave Encounter Rate
Default encounter rate in caves, 1 in 30
```json
var[cave_encounter_chance]=30
```

### Surf Encounter Rate
Default encounter rate while surfing, 1 in 40
```json
var[surf_encounter_chance]=40
```

### Wild Encounter Step Counter 
Disable wild encounters the first 10 steps after a battle
```json
var[min_encounter_count]=10
```

## Priority Rules
If the same var is defined multiple times, this is the priority:

- `ev > mapvar > var`

## Other Notes
Region Vars are still vars: You can modify them anywhere with jcoad.

- ``Example: execute(var[max_mon_level]=30)``

## Persistent Changes

- Any change made in JCoad will be saved unless you reset it.

- For temporary or map-specific settings, use mapvar instead.

- If you want it to persist long-term and across maps, use an ev.

!!! warning "Coding Logic"

    Region Vars only support var and list – you can’t use full jcoad logic inside them.