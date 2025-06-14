# Smart Answers
You can conditionally show answer options based on whether the player has met certain criteria.
This is extremely useful!

```json title="Code Example - EV"
%random%=npc(01vwqqxp,up)
%random%.msg(Ahoy, there!#Where do you want to sail?)&answers=if[ev[KnotIsland_Traveled]=1]Knot Island,if[ev[BoonIsland_Traveled]=1]Boon Island,Cancel

Knot Island=%random%.answer(All right!#All aboard the Seagallop Hi-Speed 2!)&warp=08qp3lgv,0
Boon Island=%random%.answer(All right!#All aboard the Seagallop Hi-Speed 2!)&warp=08ju24jj,0
```

In the example above, the sailor only shows the option to travel to an island if you have the corresponding ev set. 

```json title="Code Example - Money"
if !item[06q3svbf]
msg(You don't have a COIN CASE!)
else
msg(Welcome to ROCKET GAME CORNER!|Need some game coins?|Choose an amount:)&!with=enabler&!direction=d||&answers=if[money>=1000]50 - $1000,if[money>=5000]250 - $5000,if[money>=10000]500 - $10000,Cancel

500 - $10000=answer(Thanks! Here are 500 coins!)&coins=500&money=-10000
250 - $5000=answer(Thanks! Here are 250 coins!)&coins=250&money=-5000
50 - $1000=answer(Thanks! Here are 50 coins!)&coins=50&money=-1000

Cancel=answer(No? Please come play sometime!)
```

In the example above, the Game Corner clerk only shows certain options available to you, dependent on the amount of money you have.

You can use all the following:

- [ev[]]

- [mapvar[]]

- [var[]]

- [skin[]]

- [achievement[]]

- [item[]]

- [outfit[]]

- [money[]]

- [badge[]]

- [badges[]]

- [mon[]]

- [egg[]]

!!! warning "Too Many Options, So Little Time."

    It is poor game design to offer every single option and then respond with a “Sorry, that option you picked is not available.” Always aim to hide unavailable options using smart answers to avoid this.
