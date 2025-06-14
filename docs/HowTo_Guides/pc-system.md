# PC System

## Basic PC
A default PC object is available by navigating to:
**`Objects > Default > PC`**

This object uses the following simple script:

`msg(%player% booted up the PC.)&pc`

## Advanced PC
You can create a custom root object for a more dynamic PC experience. Below is an example used in Sinnoh:

```json
xy(0,-19)
%random%=animation(1995/sinnohpclightson,map+16,0,0,12,6,5,100,loop)
%random%.opacity(0)
xy()
msg(%player% booted up the PC!)&sfx=pc_on.ogg&!with=%random%&!opacity=100&with=%random%&opacity=0&pc
```
**What it does:**

1. **xy(0,-19) / xy()**
    * Temporarily offsets the visual layer to correctly place the animation.

2. **%random% = animation(...)**
    * Loads an animation `sinnohpclightson` at an offset layer `map+16` to simulate the PC screen lighting up.

3. **%random%.opacity(0)**
    * Starts the animation invisible.

4. **Main Command**
    * Displays the boot-up message.
    * Plays a sound effect (pc_on.ogg).
    * Fades the animation in (!with=%random% & !opacity=100).
    * Then fades it out (with=%random% & opacity=0).
    * Opens the PC interface.

## Kyledove’s Pory-PC

This is a **fun, decorative PC** you can place directly on any map as an NPC. It’s perfect for **seasonal events**, field areas, or anywhere you want players to access the PC without needing a building or Pokémon Center nearby. Feel free to convert this into your own root object.

```json
%random%=npc(00pxgufr,down)
%random%.msg(<name:Pory-PC,33,186,186> Bzzt! Want to access your PC?)&answers=Yes,No
Yes=%random%.answer(%player% booted up the PC.)&pc
```

## Box Link

Pokengine supports the **Box Link** item introduced in Gen 8, allowing players to access their **PC boxes from anywhere**, without needing to visit a Pokémon Center or interact with a PC terminal. All you have to do is give the item to players `&item=06vmnc0o`.

https://pokengine.org/items/06vmnc0o/Box+Link

### Box Link Guidelines

Box Link **fundamentally changes** the traditional Pokémon gameplay loop, so it should be used with care and intention.

🛑 **Why Use with Caution?**

- Removes one of the reasons to return to settlements, cutting out a key element of pacing.

- Reduces player exposure to wild encounters and potential risks on return trips.

- Undermines game economy loops (healing, buying/selling, party management at towns).

- May reduce the impact of resource management and route planning.

✅ **When It's Appropriate**

- Post-game convenience for experienced players.

- As a reward unlock, not something handed out at the start.

🚫 **Disabling Box Link in Key Areas**
When `Box Link` is enabled, it's **crucial to disable it temporarily** during specific parts of the game where its usage would break intended challenge or progression.

**Where to Disable It**
- Gyms

- Elite Four / Champion battles

- Trainer Gauntlets or Battle Towers

- Story segments with multi-trainer progression (e.g., caves, hideouts)

- Any area where healing opportunities are deliberately limited

**Why Disable It?**

If left enabled:

- Players can freely swap party members mid-challenge, bypassing strategic planning.

- It effectively allows unlimited healing by rotating fainted Pokémon to the PC.

- It removes the endurance element designed into multi-trainer routes or gauntlets.

This undermines both the tension and intended difficulty of major story and battle segments.

✅ **How to Disable It**

Use scripting to temporarily set:

`var[boxlink]=1`

!!! tip "Automatic Var"

    You can automate this by setting var[boxlink]=1 when entering an area or map, and restoring it upon leaving or after completion.

## Global PC
If your region has been **approved for Global PC** support, you'll need to use a different method to access the global PC system instead of the default one.

Ensure all your PCs use a **shared root object** (rather than coding each one individually).

!!! tip "User Experience"

    It’s a **bad user experience** if only a few PCs access the Global PC while others do not. Always keep user experience in mind!

**Example (Retro Kanto)**

```json
if champion
msg(%PLAYER% booted up the PC.)&pc=transfer
else
msg(%PLAYER% turned on the PC.)&pc
```

You can substitute `champion` with any appropriate event or variable condition, such as: `if ev[globalpc_unlocked]`

!!! note "User Experience"

    If your region hasn't been granted access to the Global PC, the game will fallback to regular PC behavior automatically, even if &pc=transfer is used.

