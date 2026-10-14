# Battle AI
Pokengine includes its own **Battle AI System**, which governs how battles play out. To streamline its use, we’ve created a set of default **battle skill levels/behaviours**, each with tailored routines that reflect different skill levels.

---

## Behaviors

- **🧢 Noob**
    * Clueless and Inexperienced

    * May still try a move that continues to fail

- **🥈 Beginner**
    * Starting to grasp the basics

    * Uses STAB moves

    * Quicker to give up if a move fails

- **🧠 Skilled**

    * Tactically aware and reactive

    * Balances offense with strategy, status effects, and field control

    * May switch out if necessary

- **🧬 Expert**

    * Highly strategic, competitive-level AI

    * Same core as Skilled, but used for top-tier battles and bosses.

All default Trainer Classes already come with preset AI levels - for example, Tubers use the `noob` AI, while Ace Trainers use the `expert` AI - so you generally won’t need to adjust these manually. 

The blank Gym Leader, Elite Four, and Champion classes are also set to `expert` by default, so as long as you're using those templates, you're covered. 

The main exception to this might be custom rival characters, where you'll likely need to assign the AI routine yourself.

---

## Predefined routine presets
In addition to the basic Noob, Beginner, Skilled, and Expert behaviors, we also offer several more advanced and specialized behaviors for greater tactical variety.

| Preset | Expands to                                                                                                                                                                                                           |
|---|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `random` | *(no routines at all, picks totally randomly)*                                                                                                                                                                       |
| `noob` | `damage`, `typing`, `failedmove-1`, `useitems`, `optimisticmultistrike`, `ohko-200`                                                                                                                                  |
| `beginner` | `inflictstatus`, `damage`, `accuracy`, `typing`, `stab`, `failedmove-5`, `useitems`, `cautiousmultistrike`, `ohko-200`                                                                                               |
| `kamikaze` | `beginner`, `explode-5`                                                                                                                                                                                              |
| `gambler` | `beginner`, `ohko-1000`                                                                                                                                                                                              |
| `skilled` | `inflictstatus`, `sethazards`, `setweathers`, `damage`, `accuracy`, `typing`, `stab`, `failedmove-10`, `offensiveswitchout-0.5`, `statboost-15`, `priority-3-3`, `useitems`, `smartexplode`, `ohko-200`, `smartohko` |
| `expert` | same as `skilled`, but `failedmove-20`                                                                                                                                                                               |
| `inflictstatus` | `inflictparalysis-10-20`, `inflictsleep-10-20`, `inflictpoison-10-20`, `inflicttoxin-10-20`, `inflictburn-10-20`, `inflictfreeze-10-20`, `inflictconfusion-7-20`, `inflictinfatuation-7-20`                          |
| `sethazards` | `stealthrock-15`, `toxicspikes-15-3`, `spikes-15-3`, `stickyweb-15`                                                                                                                                                  |
| `setweathers` | `rain-10-20`, `harshsunlight-10-20`, `sandstorm-10-20`, `snow-10-20`, `darkovercast-10-20`, `fog-10-20`                                                                                                              |

---

## Customizing default Battle AI:
That’s not to say you have to stick strictly to the default behaviors — you can absolutely customize them for greater adaptability.

For example, say you have a Youngster who’s obsessed with rain and always tries to set it up in battle. You can tweak their routine like so:
`;routines noob,rain-10-20;`

This line is added to the trigger that initiates the battle via jCoad.
This keeps the base “Noob” behavior but adds rain-setting as a priority - perfect for giving even early trainers some personality.

---

## All Routines

Numbers in brackets are required. A routine that needs a number does nothing without it.

### Flags and controls

These change how other routines behave. They don't score moves on their own.

| Routine | Description |
|---|---|
| `no-(routine)` | Removes a routine, including ones that come from a skill level. Example: `no-useitems`. |
| `typing` | Takes type matchups into account when scoring damage and status moves. Without it, every move is treated as neutral. |
| `stab` | Boosts damaging moves that match the user's type. Only does something alongside `damage`. |
| `cautiousmultistrike` | Values multi-hit moves as if they only hit their minimum number of times. |
| `optimisticmultistrike` | Values multi-hit moves as if they hit their maximum number of times. |
| `highestscore` | The AI always picks one of its top-scoring options, instead of choosing randomly in favor of higher scores. |

### Damage

| Routine                       | Description                                                                                                                                              |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `damage`                      | Scores moves by their power. Hitting teammates counts against a move.                                                                                    |
| `random-(max)`                | Adds a random score from 1 to max to each move and target. Never targets allies unless the move requires it.                                             |
| `failedmove-(penalty)`        | Discourages moves that have already failed against a target. The penalty is applied once per failure, so bigger numbers are harsher. Misses don't count. |
| `explode-(multiplier)`        | Multiplies the score of self-destructing moves. Bigger numbers make explosions far more likely.                                                          |
| `smartexplode`                | Discourages self-destructing moves, more so when the user is healthy.                                                                                    |
| `ohko-(score)`                | Adds the given score to one-hit-KO moves.                                                                                                                |
| `smartohko`                   | Rules out one-hit-KO moves that would fail, such as against a higher-level or immune target.                                                             |
| `priority-(bonus)-(exponent)` | Encourages priority moves, especially against targets with low HP. Actual score is `1 + bonus * (1 - hpFraction) ** exponent`.                           |
| `accuracy`                    | Discourages less accurate moves. The lower the accuracy, the bigger the penalty.                                                                         |

### Status infliction

Each of these encourages moves that inflict the status on a target that doesn't have it, and discourages them on a target that already has it, or on an allied target. The first number is the bonus, the second is the penalty for hitting an ally. The `inflictstatus` group sets all of these with sensible defaults.

| Routine | Status |
|---|---|
| `inflictparalysis-(score)-(allyPenalty)` | Paralysis |
| `inflictsleep-(score)-(allyPenalty)` | Sleep |
| `inflictpoison-(score)-(allyPenalty)` | Poison |
| `inflicttoxin-(score)-(allyPenalty)` | Bad poison |
| `inflictburn-(score)-(allyPenalty)` | Burn |
| `inflictfreeze-(score)-(allyPenalty)` | Freeze |
| `inflictconfusion-(score)-(allyPenalty)` | Confusion |
| `inflictinfatuation-(score)-(allyPenalty)` | Infatuation |

### Category boosts

| Routine | Description |
|---|---|
| `statusmoves-(score)` | Adds the given score to all status moves. |
| `damagemoves-(score)` | Adds the given score to all damaging moves. |
| `physicalmoves-(score)` | Adds the given score to all physical moves. |
| `specialmoves-(score)` | Adds the given score to all special moves. |

### Field setup

The `sethazards` and `setweathers` groups set all of these with sensible defaults.

| Routine | Description |
|---|---|
| `stealthrock-(score)` | Encourages setting up Stealth Rock. |
| `stickyweb-(score)` | Encourages setting up Sticky Web. |
| `spikes-(score)-(layerPenalty)` | Encourages setting up Spikes. Each extra layer is worth a little less. |
| `toxicspikes-(score)-(layerBonus)` | Encourages setting up Toxic Spikes. Each extra layer is worth a little more. |
| `rain-(score)-(overwriteScore)`<br>`harshsunlight-(score)-(overwriteScore)`<br>`sandstorm-(score)-(overwriteScore)`<br>`snow-(score)-(overwriteScore)`<br>`darkovercast-(score)-(overwriteScore)`<br>`fog-(score)-(overwriteScore)` | Encourages setting up that weather. The first score applies when the sky is clear, the second when replacing a different weather. Never re-sets weather that is already active. |
| `statboost-(score)` | Encourages stat-boosting moves, but only on the first turn after being sent out. |

### Switching and items

These only apply to trainers. Switching out and using an item compete with the mon's moves as possible actions.

| Routine | Description |
|---|---|
| `offensiveswitchout-(multiplier)` | Compares the current mon with the rest of the party, and may switch if a teammate has a better move. Lower multipliers mean less switching. Also helps pick the best mon to send out after a faint. |
| `savelastmon` | Tries to keep the last mon in the party in reserve for as long as possible. |
| `useitems` | Uses healing items when a mon is low on HP. |

---

## Warnings

Code not working like you expect? Remember the following:

 - Parameters are required. A routine like `rain` or `ohko` without a dash and number does nothing.
 - Listed values win over presets. For example, `beginner,failedmove-10` has `failedmove-5` inside `beginner`. Because `failedmove-10` was specified last, the result is `failedmove-10`.
 - Wild Mons default to `random-5` and trainers default to `beginner`.