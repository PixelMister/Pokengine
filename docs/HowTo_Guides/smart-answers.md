# Smart Answers
You can conditionally show answer options based on whether the player has met certain criteria.
This is extremely useful!

```json title="Code Example"
%random%=npc(01vwqqxp,up)
%random%.msg(Ahoy, there!#Where do you want to sail?)&answers=if[ev[KnotIsland_Traveled]=1]Knot Island,if[ev[BoonIsland_Traveled]=1]Boon Island,Cancel

Knot Island=%random%.answer(All right!#All aboard the Seagallop Hi-Speed 2!)&warp=08qp3lgv,0
Boon Island=%random%.answer(All right!#All aboard the Seagallop Hi-Speed 2!)&warp=08ju24jj,0
```

In this example, the sailor only shows the option to travel to an island if you have the corresponding ev set. 

You can use all the following
- [random[]]

- [minute[]]

- [hour[]]

- [date[]]

- [month[]]

- [year[]]

- [time[]]

- [player.x[]]

- [player.y[]]

- [map[]]

- [mapvar[]]

- [var[]]

- [ev[]]

- [list[]]

- [outfit[]]

- [skin[]]

- [mon[]]


!!! warning "Too Many Options, So Little Time."

    It is poor game design to offer every single option and then respond with a “Sorry, that option you picked is not available.” Always aim to hide unavailable options using smart answers to avoid this.
