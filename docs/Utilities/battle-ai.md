# Battle AI
## Introduction
Pokengine includes its own **Battle AI System**, which governs how battles play out. To streamline its use, we’ve created a set of default **battle skill levels/behaviours**, each with tailored routines that reflect different skill levels.

## Behaviours and their Routines

- **Noob**
    * Clueless and Inexperienced

    * Will only try a new move after the current one fails 3 times.

    * `damage, typing, failedMove-3, useitems, random-5`

- **Beginner**
    * Starting to grasp the basics

    * Uses STAB moves and switches tactics after a single failed move.

    * `damage, typing, stab, inflictStatus, failedMove-1, useitems, random-5`

- **Skilled**

    * Tactically aware and reactive.

    * Balances offense with strategy, status effects, and     field control

    * May switch out if necessary.

    * `damage, typing, stab, inflictStatus, accuracy, switchout-0.5, sethazards, setweathers, statboost, useitems, random-5`

- **Expert**

    * Highly strategic, competitive-level AI.

    * Same core as Skilled, but used for top-tier battles and bosses.

    * `damage, typing, stab, inflictStatus, accuracy, switchout-0.5, sethazards, setweathers, statboost, useitems, random-5`

All default Trainer Classes already come with preset AI levels - for example, Tubers use the Noob AI, while Ace Trainers use the Expert AI - so you generally won’t need to adjust these manually. 

The blank Gym Leader, Elite Four, and Champion classes are also set to Expert by default, so as long as you're using those templates, you're covered. 

The main exception to this might be custom rival characters, where you'll likely need to assign the AI routine yourself.

## All Routines
| Behaviour/Rule                  | Description |
|-------------------------------|-------------|
| `no`                          | Will not use routine, can also be used to remove behaviours. |
| `random-(maxScore)`           | Encourages random moves/targets with a score between 1 and maxScore. Avoids targeting allies unless affected by target range. |
| `damage`                      | Scores moves and targets based on move power, negatively against teammates. |
| `stab`                        | Adjusts damage scores to include STAB boost. |
| `typing`                      | Considers typing in scoring. |
| `hp`                          | Considers target's HP in scoring. |
| `inflictParalysis`           | Encourages paralysis moves if the target has no status, discourages if already statused. |
| `inflictSleep`               | Encourages sleep moves if the target has no status, discourages if already statused. |
| `inflictPoison`              | Encourages poison moves if the target has no status, discourages if already statused. |
| `inflictBurn`                | Encourages burn moves if the target has no status, discourages if already statused. |
| `inflictFreeze`              | Encourages freeze moves if the target has no status, discourages if already statused. |
| `inflictConfusion`           | Encourages confusion moves if the target is not confused, discourages if already confused. |
| `inflictInfatuation`         | Encourages infatuation moves if the target is not infatuated, discourages if already infatuated. |
| `accuracy`                   | Discourages lower accuracy moves; lower accuracy = more discouraged. |
| `failedMove-(numberOfTurns)` | Discourages moves that failed against a target for at least a certain number of turns. |
| `switchout-(penaltyMlt)`     | Compares scores of inactive Pokémon. If better, may switch in with a score multiplier (default 0.5). |
| `saveLastMon`                | Trainer will try to save the last Pokémon in the party for last. |
| `statusMoves-(score)`        | Encourages use of status moves by the given score. |
| `dmgMoves-(score)`           | Encourages all damaging moves by the given score. |
| `physicalDmgMoves-(score)`   | Encourages physical damage moves by the given score. |
| `specialDmgMoves-(score)`    | Encourages special damage moves by the given score. |
| `stealthrock`                | Encourages setting up Stealth Rock. |
| `spikes`                     | Encourages setting up Spikes; slightly discouraged after each layer. |
| `toxicspikes`                | Encourages setting up Toxic Spikes; more encouraged after the first layer. |
| `stickyweb`                  | Encourages setting up Sticky Web. |
| `rain`, `harshsunlight`, `sandstorm`, `snow`, `darkovercast`, `fog` | Encourages setting up weather; more encouraged if another weather is already active. |
| `useitems`                   | Uses available items if certain conditions are met. |
| `statboost`                  | Encourages use of stat-boosting moves on the first turn out. |

## Advanced Routines
In addition to the basic Noob, Beginner, Skilled, and Expert behaviors, we also offer several more advanced and specialized behaviors for greater tactical variety.

| Group           | Includes                                                                                      |
|----------------|-----------------------------------------------------------------------------------------------|
| `inflictStatus`| `inflictParalysis`, `inflictSleep`, `inflictPoison`, `inflictBurn`, `inflictFreeze`, `inflictConfusion`, `inflictInfatuation` |
| `sethazards`   | `stealthrock`, `spikes`, `toxicspikes`, `stickyweb`                                           |
| `setweathers`  | `rain`, `harshsunlight`, `sandstorm`, `snow`, `darkovercast`, `fog`                          |

## Customizing default Battle AI:
That’s not to say you have to stick strictly to the default behaviors — you can absolutely customize them for greater adaptability.

For example, say you have a Youngster who’s obsessed with rain and always tries to set it up in battle. You can tweak their routine like so:
`;routines noob,rain;`

This line is added to the trigger that initiates the battle via jcoad.

This keeps the base “Noob” behavior but adds rain-setting as a priority — perfect for giving even early trainers some personality.

!!! warning "Default Behaviour"

    You must explicitly include the default behavior (e.g. noob), even if the trainer class already has it by default. If no routine is provided, the system falls back to the routine set on the specific trainer used (as defined on the website). If that doesn’t exist either, the AI will default to using random moves. 

## Wild Pokemon AI:
It’s not just Trainers that can use battle AI - Wild Pokémon can too!

By default, wild Pokémon don’t have skill levels, so they’ll simply choose moves at random. However, you can assign routines to them manually in static encounters (such as alpha / totem / boss battles).

To do this, just add `;routines noob,rain;` at the end of the jcoad that’s generating the battle, like you would do for its level for example with `;l 50;`

For routines that follow a routine-value format, only the last instance of that routine type in the list will be used when scoring.

**For example:**
 `routines = "failedMove-3, failedMove-5, failedMove-1"` → only `failedMove-1` is counted.

This also applies when routines are defined through personas (behaviors):

 routines = "beginner, failedMove-5, noob" → the failedMove-3 from noob will override failedMove-5, since noob comes later and also includes failedMove.
 
!!! warning "Default Behaviour"
    This override behavior does not apply to routines written as "no-[routine]". These exclusions are always respected, regardless of their position in the list.
 
For example: `routines = "failedMove-3,failedMove-5,failedMove-1",` only failedMove-1 will be counted when scoring

This also applies for behaviors:
`for example: routines = "beginner,failedMove-5,noob", only failedMove-3` (and other values from 'noob' that also existed in the list) will be counted when scoring
THIS DOESNT HAPPEN IF THE ROUTINE IS `"=no-(routine)"`