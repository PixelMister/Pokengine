# Step Counter

## Introduction
Sometimes, you might want to track how many steps a player takes and trigger something after reaching a certain number. You can achieve this using the following setup:

To activate the step counter, place the following code into an object, after an `execute()`.
```json
mapvar[stepcounter_active]=1 
```
This enables step tracking. Once active, each step taken will automatically increment: `mapvar[stepcounter]`

For example, after 5 steps, the value becomes: `mapvar[stepcounter]=5`

## Persistent Across Maps:
You can use the `var[stepcounter_active]` for steps to persist across maps for a single session. Alternatively, you can use `ev[stepcounter_active]` to persist indefinitely (even between logins).

If you want to stop counting, simply set/call the ev again: 
```json
ev[stepcounter_active]=0
```

!!! note "Safari Zone"

    This system is not the same as the one used in the Safari Zone.


!!! danger "Performance Issues"

    Having `ev/var/mapvar[stepcounter_active]` causes the entire map to update each step. For this reason, it's recommended that:
        1. You only use it on maps that do not have a lot of other events.
        2. You should use the `mapvar` version when possible so that the performance issues do not follow the player around (especially if they use Fly).

!!! danger "Visual Inconsistencies"

    This can cause issues with step-based visual effects like footprints or sand trails. Because the step event constantly triggers, it repeatedly resets the trail effect—making it behave incorrectly. 

> 💡 **Credit**: The Move Relearner system was developed by **Skur**.