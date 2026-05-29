# Lottery Corner System

![A screenshot of the player speaking to the lottery corner assistant with the dialogue appearing.](assets/lottery-corner.png)

The Lottery Corner (also known as Loto-Id) system allows players to check a daily or weekly lottery number. If the drawn number matches the UMID number of any Pokémon they have obtained within that Region, they can win a prize. To clarify - it will check every Pokémon stored in your PC, not just your party.
## Activation

To add a Lottery Corner NPC, simply use one of the following commands:

**Daily Lottery**
```json
msg()lottery=daily
```
Allows players to participate once per (real life) day.

**Weekly Lottery**
```json
msg()lottery=weekly
```
Allows players to participate once per week. After first use, the player must wait one week from their previous attempt.

The system automatically handles:
- All dialogue
- Generating lottery numbers
- preventing duplicate claims
- Checking all eligible pokemon
- Determining highest matching prize tier
- Awarding prizes

No additional scripting is required.

## How Matching Works

The lottery number is a 5-digit number.
The system compares this number against the UMID of every Pokémon obtained within the current region.
Only Pokémon from the current region are eligible. Pokémon originating from other regions will not be considered.
The highest match found determines the prize awarded.
Since UMID can be way bigger than 5 digits, it only takes from the last five digits of your UMID.

Example:
```json
Lottery Number: 12345
Pokémon UMID: 705734
Last 5 digits from your Pokemon's UMID: 05734
```
These three digits match:
```json
345
```
This would award the Second Prize.

!!! note
    The order of the numbers doesn't have to match, even though the dialogue in game says so - that's purely for flavor.


## Prize Tiers
- 🥉 Third Prize - 2 digits match - **Max Revive**
- 🥈 Second Prize - 3 digits match - **PP Ups**
- 🥇 First Prize - 4 digits match - **Lucky Egg**
- 👑 Jackpot Prize - 5 digits match - **Master Ball**

There is no reward for matching 1 digit, as this is considered too common.

## Achievements
Achievements are handled automatically by the system. 
Prize achievements are awarded for each lottery tier, and an additional achievement is granted after entering 50 times, regardless of win or loss.
These achievements are tracked cumulatively across all Regions and are not Region-specific.

![A screenshot of all the possible lottery corner achievements.](assets/lottery-corner-achievements.png)

💡 **Credit**: The Lottery Corner system was developed by **Skur**.
