# Step Counter

## Introduction
Sometimes, you might want to track how many steps a player takes and trigger something after reaching a certain number. You can achieve this using the following setup:

To activate the step counter, place the following code into an object, after an `execute()`.
```json
ev[stepcounter_active]=1 
```
This enables step tracking. Once active, each step taken will automatically increment: `ev[stepcounter]`

For example, after 5 steps, the value becomes: `ev[stepcounter]=5`

## Persistent Across Maps:
Step counting will continue even when the player moves between maps. 

If you want to stop counting, simply set/call the ev again: 
```json
ev[stepcounter_active]=0
```

!!! note "Safari Zone"

    This system is not the same as the one used in the Safari Zone.


!!! danger "Visual Inconsistencies"

    This can cause issues with step-based visual effects like footprints or sand trails. Because the step event constantly triggers, it repeatedly resets the trail effect—making it behave incorrectly. 

> 💡 **Credit**: The Move Relearner system was developed by **Skur**.