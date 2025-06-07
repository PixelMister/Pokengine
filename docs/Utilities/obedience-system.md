# Obedience System
## What does it do?
Lets region devs pick level caps at which mons will disobey their trainer, and change those caps when some condition is met (this can be getting gym badges, changing a certain EV or when the player is in a specific map), also works as a level cap so players wont overlevel their mons and be unable to control them, but wont force mons levels down.

## How to use it?
Go to your region 'Vars' textbox and add the following var `disobedience={20: badge-1}`, for example.

## How to use a specific condition?
All conditions are used by writing after the level cap a key word for that condition followed by a '-' and different values, for example `disobedience={20: badge-1}`, for the badge condition.

## Can you use different conditions in the same level cap?
Yes, to do that you can separate the condition using a `|` to represent an `OR` operate or a `&` to represent an `AND` operator, for example: `disobedience={20: map-08kz3tmv|badge-1&map-03fz21mf}`, where the `AND` operators are always checked first.

## Which conditions can be used?
- **Badges**, will use the specified level cap if the player doesn't have the specified badge, the value represents the number of that badge, for example: `disobedience={20: badge-1}`, for the first badge in your region;

- **EVs**, will use the specified level cap if the player has an EV value lower the the value, the first value represents the name of the ev and the second value represents at which ev the player will unlock the cap, for example: `disobedience={30: ev-EVName-3}`.

- **Maps**, will use the specified level cap if the player is in the specified map uid, value is the map uid, for example: `disobedience={40: map-08kz3tmv}`.

- **Always**, will always use the specified cap, no values, for example: `disobedience={90: always}`

```json title="Code Example"
disobedience={20: map-08kz3tmv|badge-1&map-03fz21mf, 30: badge-2, 40: ev-EVisland-2, 90: always}
```

!!! note "Requests"

    If you want a condition not present yet just ping me and ask for it to be implemented, same if there is any questions about how to use it!


> 💡 **Credit**: The Move Relearner system was developed by **Demonyc**.
