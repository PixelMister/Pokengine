# Quest System
## Introduction

The quest widget is an extremely handy system with several benefits:

- **Keeps players on track**: It helps players follow the main story by reminding them of their current objective - especially useful for those returning after a break and unsure of what to do next.

- **Guides without hand holding**: You can place objective markers on the map, offering subtle guidance without breaking immersion or overly directing the player.

- **Organized quest categories**: You can assign quests to different categories (like Main Story, Side Quests, or Events), making it easier for players to manage multiple threads at once.

- **Focus on one task**: Players can choose to track a single quest at a time, helping them stay focused instead of feeling overwhelmed by multiple objectives.

- **Optional and unobtrusive**: Players who prefer to forge their own path can collapse categories or close the widget entirely, allowing for a more self-directed, exploration-heavy experience.

All your quest data is handled within Mapbuilder > Region > Quests

## Quest Formatting
It is important to make sure that all quests follow the format below; without adhering to this format - the quest will not work!

```json
name=Road to Champion
category=Main Quests
flavor=Battle your way across the Kanto Region! Take on Gym Leaders, stop Team Rocket, and uncover powerful legendary Pokemon.
objective=Find Professor Oak.|var[starterscene]=6|083leomi
objective=Pick a Starter.|var[starterscene]=15|08n31ado
objective=Battle your rival.|ev[starterscene]=1|08n31ado
objective=Travel to Viridian City.|ev[ViridianReached]=1|08p8ofto
```

So, this works by using the following parameters:

- **Name** - The name of the quest
- **Category** - The category the quest is organised into.
- **Flavor** - Narrative text describing the quest.
- **Objectie** - Objective description.|Completion Condition|Map ID

In the example above, once the player meets the condition `var[starterscene]=6`, that objective will be marked as completed and it will progress to the next objective.

**Important Notes**

- Once a quest has been added, you **cannot rename it** - doing so will create a new quest. Make sure your quest names are finalized before pushing them live.


Quest names can include spaces, but **avoid symbols** like exclamation marks (!) as they may break the code.


If a player starts a quest and they’ve already met the conditions for later objectives, those objectives will be automatically marked as complete. In some cases, this can result in a quest instantly completing upon being received - be careful!


The quest system **only supports linear progression**. If your story branches, you'll likely need to end the current quest and start separate ones for each path.


You can use any category name, but we recommend sticking with **"Main Quests"** and **"Side Quests"** to stay consistent with other regions and help players feel oriented.


Feel free to expand with additional categories like Rumours, Secrets, PokeHunts, and more - whatever fits your region’s tone and structure.


The quest system does **not** include built-in functionality for rewards (such items, money, etc) upon completion. If you want to reward the player, you’ll need to manually code it using events or NPCs when the final objective is completed.


**You must include two pipes (|) in every objective line**, even if you're not using a map ID. The map portion is optional, but the format still requires three sections: Example:
 `objective=Defeat the Gym Leader.|ev[badge1]=1|`

The quest tracker system was inspired by games like Skyrim and The Witcher 3, where objectives are short and to the point - for example, “Obtain the magic ring,” “Speak to the Elder,” or “Visit the grove.” We recommend following this style and avoiding overly detailed objectives that read like walkthrough steps, such as:

 “Get to the side of Route 2 blocked by a cuttable tree. Speak to the attendant inside and prove you’ve caught 10 different Pokémon to get the Flash TM.”

Instead, a concise objective like “Speak to Oak’s Attendant” with their location marked on the map is better - players will find their own way and figure out what to do once they talk to him.

Be aware that lengthy, detailed objectives can act as spoilers and frustrate some players. Keeping objectives concise helps players focus on the story and exploration without feeling micromanaged.

## Objective Completion Criteria

You can use the following triggers in quest objectives - these are the same as those used in smart answers:

`[ev[]]`

`[mapvar[]]`

`[var[]]`

`[skin[]]`

`[achievement[]]`

`[item[]]`

`[outfit[]]`

`[money[]]`

`[badge[]]`

`[badges[]]`

`[mon[]]`

`[egg[]]`

`[caught[]]`

**Important Notes**

- While using `[achievement[]]` might seem useful, achievements are saved permanently. This means if a player resets the region, quests using achievements as conditions may skip steps automatically. For this reason, avoid using achievements as completion criteria.


- Generally, `[ev[]]` is recommended for most quest conditions.


- You can combine triggers using `and`. For example:
`objective=Obtain both gemstones.|item[06k8mrwt] and item[060lbtis]|`


- TMs count as items, so you can use `item[move uid]` for them.


- For badges, you can use specific badge names like `badge[marsh]` or numeric comparisons like `badges=3` to support non-linear badge progression.


- Less than, greater than, or equal are supported, e.g. `ev[dojo]>=1`

## Triggering Quests

**Example:** `&startquest=Road to Champion`

- `&startquest=name` - Starts the quest with the given name

- `&removequest=name` - Removes the specified quest entirely

- `&completequest=name` - Instantly marks the specified quest as complete

- `&resetquests` - Clears all quests (intended for debugging or development use only)

# Quest Signifiers
Quest Indicators

To clearly communicate quest status to players, we recommend using intuitive icons.

Here's the format we suggest:

- **Star Icon** ![alt text](assets/queststaricon.png) OR **Question Icon** ![text](assets/questnotstartedicon.png) – A new quest is available at this location.


- **Ellipsis Icon** ![alt text](assets/questinprogressicon.png) – A quest is in progress, but there's no new update.


- We suggest having the NPC provide a helpful prompt or reminder about the current objective when in this state.


- **Exclamation Icon** ![alt text](assets/questcompletedicon.png) – The quest has been updated. Speak to the NPC for the next step!


This icon can also indicate that the quest is ready to be completed.


> 💡 **Credit**: The Quest system was envisaged by **Kyledove** and designed and spearheaded by **Gav**
