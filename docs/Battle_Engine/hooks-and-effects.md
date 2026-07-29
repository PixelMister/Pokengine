# Hooks & Effects
A "hook" is a function called at a specified time in the battle that injects code. For example, the ability Justified has an `onHit` hook that checks the attack's typing. 

An "effect" is an object that holds (possibly many) hooks. Effect types are:
1. Held items
2. Abilities
3. Moves (only when attacking)
4. Volatile statuses
5. Team effects (field effects on one side, like Reflect)
6. Whole field effects (like Trick Room)
7. Weather
8. Terrain

Effects are checked from 1-8, so if a held item changes a Mon's type to Grass, but a weather changes it to Water, the Mon in the end will be a Water-type.

## Hooks That Affect Types

!!! note "Type UIDs"

    Type UIDs can be names ("Ghost") or numbers ("8"), but must always be strings. Moreover, these are case-insensitive, so "ghost" works just as well as "Ghost" or "GHOST".

### Extra Types
Adds extra type(s) to the move effectiveness calculations. For example, [Flying Press](<https://pokengine.org/moves/07u87lxx/Flying+Press>) uses:
```js
extraTypes: ["flying"]
```

### Item Types
For moves only, changes the attacking move's type depending on the held item. For example, [Techno Blast](<https://pokengine.org/moves/07ruodk6/Techno+Blast>) uses:
```js
itemTypes: { "06bvieyk": "11", "0612bbwx": "16", "06q1yd64": "12", "06yb9jf6": "14", }
```

### Normalize
Changes moves from one type to another. The classic example is Skitty's [Normalize](<https://pokengine.org/abilities/05ov0vht/Normalize>) ability, which does:
```js
normalizeMoves: {typesToChange: "all", changeTo: "normal"}
```
However, instead of "all", you can specify the types to change to and from. [Pixilate](<https://pokengine.org/abilities/05d3pf31/Pixilate>) does this:
```js
normalizeMoves: {typesToChange: ["normal"], changeTo: "fairy"}
```
Notably, this does not work for moves that have special type-changing mechanics already. For example, [Techno Blast](<https://pokengine.org/moves/07ruodk6/Techno+Blast>) has the classification `normalize-banned`.

### Self Type
For moves only, this hook changes the attacking move the user's primary type. For example, [Revelation Dance] uses:
```js
selfType: true
```

### Type Effectiveness
Overrides the normal type effectiveness calculations. For example, [Scrappy](<https://pokengine.org/abilities/0585qlhw/Scrappy>)'s code has
```js
typeEffectiveness: [{type: "ghost", multiplier: 1, moveTypes: ["normal", "fighting"]}]
```
The `moveTypes` can also be left out provided the `effect` has a `.type` property. This is what [Freeze-Dry](<https://pokengine.org/moves/07mcf6fk/Freeze-Dry>) does:
```js
typeEffectiveness: [{type: "water", multiplier: 2}]
```
Here, `moveTypes` is constructed implicitly as `[move.type]`, with `move` being the Freeze-Dry move object.
