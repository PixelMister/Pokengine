# Happiness
## Introduction

Happiness, also known as friendship, is a stat that measures how much a Pokémon likes its Trainer. It affects evolution, move effectiveness, and certain interactions.

Happiness is a value between 0 and 255.

You can decide how happy a Pokémon is when it’s caught, but we recommend sticking to the default value of 70 for consistency.

Some Pokémon evolve when their happiness reaches a certain threshold. We recommend using the default evolution point of 220.

Note: Pokengine does not support the heavily unbalanced mechanics from later generations where high-happiness Pokémon may survive hits with 1 HP, land critical hits more often, or shake off status effects.

## How to Increase Happiness / Friendship

- Level up your Pokémon.

- Walk with it in your party

- Receive items from it (see the Buddy System section).

- Use vitamins or other happiness-boosting items (search `“items #happiness+up”` on the website).

- Give it a Soothe Bell to hold.

- Catch it in a Luxury Ball.

## Lowering Happiness / Friendship

- Fainting in battle.

- Using bitter herbs like Revival Herb or other happiness-reducing items (search `“items #happiness+down”` on the website).

- Trading Pokémon will reset happiness.

⚠️ WARNING: Happiness Balance



!!! warning "Balancing Happiness Accessibility"

    **Happiness is designed to be something that increases gradually.**
    Because of this, you should be **extremely cautious** when implementing happiness-raising items and mechanics.
    
    **We strongly recommend that mechanics be:**
    
    - **Limited to one purchase per day**

    - **Tightly gated through quests, events, or milestones.**

    Overuse can trivialize happiness-based evolution and undermine the intended pacing of the mechanic.

## Happiness Raising Item Syntax:

```json
gameEffect: (game,mon) => {
mon.alterHappiness(15,10,5);
},
requirement: mon => mon.happiness < 255
```

The `alterHappiness` function increases a Pokémon's happiness based on how happy it currently is. The values `(15, 15, 5)` correspond to low, medium, and high happiness tiers.This system makes happiness gains **scale down** as the Pokémon becomes happier, which prevents maxing out too quickly.

## Daily happiness item seller NPC Example:

```json
if ev[day]!=date
execute(ev[day]=%date%&ev[HappinessItemGet]=0)
%random%=npc(016qossl,down)
if ev[HappinessItemGet]=1
%random%.msg(Apologies, it's one treat per customer!)
else if money>=700
%random%.msg(Hello! Would you care for a Water Manju?|Would you like one? It'll be $700!)||answers=Yes,No
else if money<700
%random%.msg(Hello! Would you care for a Water Manju?||Would you like one? It'll be $700!|...Ah, I'm afraid you can't afford it.)
Yes=%random%.answer(Here you go!)item=06lhlmrp&money=-700&ev[HappinessItemGet]=1
No=%random%.answer(Come again!)
```

## Daily Massage NPC Example:

```json
if ev[day]!=date
execute(ev[day]=%date%&ev[massageDay]=0)
%random%=npc(0)
if !mapvar[spaintro] and ev[massageDay]=0
%random%.msg(Oh, looking a little tired?#...Oh, no, not you.|I meant your Pokemon.|If you'd like, once a day - I will massage your Pokemon.)||!mapvar[spaintro]&!mapvar[massageRNG]=%random[0-100]%&answers=Yes,No
Yes=%random%.answer(Which Pokemon should I massage?)&answers=if[mon[1] and !egg[1]]%mon[1].name%#1,if[mon[2] and !egg[2]]%mon[2].name%#2,if[mon[3] and !egg[3]]%mon[3].name%#3,if[mon[4] and !egg[4]]%mon[4].name%#4,if[mon[5] and !egg[5]]%mon[5].name%#5,if[mon[6] and !egg[6]]%mon[6].name%#6,Cancel
if mapvar[spaintro] and ev[massageDay]=0
%random%.msg(If you'd like, I will massage your Pokemon.#Which should I massage?)&answers=if[mon[1] and !egg[1]]%mon[1].name%#1,if[mon[2] and !egg[2]]%mon[2].name%#2,if[mon[3] and !egg[3]]%mon[3].name%#3,if[mon[4] and !egg[4]]%mon[4].name%#4,if[mon[5] and !egg[5]]%mon[5].name%#5,if[mon[6] and !egg[6]]%mon[6].name%#6,Cancel
%mon[1].name%#1=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=1&update
%mon[2].name%#2=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=2&update
%mon[3].name%#3=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=3&update
%mon[4].name%#4=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=4&update
%mon[5].name%#5=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=5&update
%mon[6].name%#6=%random%.answer(All right! Let me get started.)freeze&fadeout&pause=700&sfx=jingle.ogg&pause=1100&mapvar[massage]=6&update
if ev[massageDay]=1
msg(Sorry!#I am exhausted from the massage earlier.|Please come back again tomorrow!)
xy(-16,0)
if ontile and mapvar[massage]=1 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[1]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[1].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=1 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[1]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[1].name% more friendly to you!
else if ontile and mapvar[massage]=1 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[1]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[1].name% much more friendly to you!
if ontile and mapvar[massage]=2 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[2]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[2].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=2 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[2]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[2].name% more friendly to you!
else if ontile and mapvar[massage]=2 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[2]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[2].name% much more friendly to you!
if ontile and mapvar[massage]=3 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[3]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[3].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=3 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[3]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[3].name% more friendly to you!
else if ontile and mapvar[massage]=3 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[3]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[3].name% much more friendly to you!
if ontile and mapvar[massage]=4 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[4]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[4].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=4 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[4]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[4].name% more friendly to you!
else if ontile and mapvar[massage]=4 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[4]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[4].name% much more friendly to you!
if ontile and mapvar[massage]=5 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[5]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[5].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=5 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[5]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[5].name% more friendly to you!
else if ontile and mapvar[massage]=5 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[5]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[5].name% much more friendly to you!
if ontile and mapvar[massage]=6 and mapvar[massageRNG]<31
msg()unfreeze&fadein&happiness[6]=5&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[6].name% a little bit more friendly to you!
else if ontile and mapvar[massage]=6 and mapvar[massageRNG]>=31 and mapvar[massageRNG]<61
msg()unfreeze&fadein&happiness[6]=15&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[6].name% more friendly to you!
else if ontile and mapvar[massage]=6 and mapvar[massageRNG]>=61
msg()unfreeze&fadein&happiness[6]=30&mapvar[massage]=0&ev[massageDay]=1&textbox=There. All done!#The massage has made %mon[6].name% much more friendly to you!
```

## Happiness Checker NPC

The example below shows an NPC based on the one from Retro Hoenn’s Verdanturf Town. She checks the happiness of the first Pokémon in your party.

```json 
%random%=npc(01972z5l,down)
if happiness[1]>255
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[1]>225
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It seems to be very happy. It obviously likes you a whole lot.)
else if happiness[1]>175
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[1]>125
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It's getting used to you. It seems to believe in you.)
else if happiness[1]>75
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It's not very used to you yet. It neither loves nor hates you.)
else if happiness[1]>25
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|It's very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[1]<0
%random%.msg(Let me see your POKEMON.#I'll check to see how much it likes you.|This is a little hard for me to say… Your Pokémon simply detests you. Doesn't that make you uncomfortable?)
```

## Advanced Happiness Checker NPC

This NPC first asks which Pokémon you want to check, improving user experience by removing the need to shuffle Pokémon around each time. It will also ignore any eggs.

```json 
%random%=npc(011007k8,down)
%random%.msg(If you let me see your Pokemon, I'll check to see how much it likes you!|Which do you want me to check?)|answers=if[mon[1] and !egg[1]]%mon[1].name%#1,if[mon[2] and !egg[2]]%mon[2].name%#2,if[mon[3] and !egg[3]]%mon[3].name%#3,if[mon[4] and !egg[4]]%mon[4].name%#4,if[mon[5] and !egg[5]]%mon[5].name%#5,if[mon[6] and !egg[6]]%mon[6].name%#6,Cancel

if happiness[1]>255
%mon[1].name%#1=%random%.answer(%mon[1].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[1]>225
%mon[1].name%#1=%random%.answer(%mon[1].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[1]>175
%mon[1].name%#1=%random%.answer(%mon[1].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[1]>125
%mon[1].name%#1=%random%.answer(%mon[1].name% is getting used to you. It seems to believe in you.)
else if happiness[1]>75
%mon[1].name%#1=%random%.answer(%mon[1].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[1]>25
%mon[1].name%#1=%random%.answer(%mon[1].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[1]<0
%mon[1].name%#1=%random%.answer(This is a little hard for me to say… %mon[1].name% simply detests you. Doesn't that make you uncomfortable?)

if happiness[2]>255
%mon[2].name%#2=%random%.answer(%mon[2].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[2]>225
%mon[2].name%#2=%random%.answer(%mon[2].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[2]>175
%mon[2].name%#2=%random%.answer(%mon[2].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[2]>125
%mon[2].name%#2=%random%.answer(%mon[2].name% is getting used to you. It seems to believe in you.)
else if happiness[2]>75
%mon[2].name%#2=%random%.answer(%mon[2].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[2]>25
%mon[2].name%#2=%random%.answer(%mon[2].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[2]<0
%mon[2].name%#2=%random%.answer(This is a little hard for me to say… %mon[2].name% simply detests you. Doesn't that make you uncomfortable?)

if happiness[3]>255
%mon[3].name%#3=%random%.answer(%mon[3].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[3]>225
%mon[3].name%#3=%random%.answer(%mon[3].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[3]>175
%mon[3].name%#3=%random%.answer(%mon[3].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[3]>125
%mon[3].name%#3=%random%.answer(%mon[3].name% is getting used to you. It seems to believe in you.)
else if happiness[3]>75
%mon[3].name%#3=%random%.answer(%mon[3].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[3]>25
%mon[3].name%#3=%random%.answer(%mon[3].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[3]<0
%mon[3].name%#3=%random%.answer(This is a little hard for me to say… %mon[3].name% simply detests you. Doesn't that make you uncomfortable?)

if happiness[4]>255
%mon[4].name%#4=%random%.answer(%mon[4].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[4]>225
%mon[4].name%#4=%random%.answer(%mon[4].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[4]>175
%mon[4].name%#4=%random%.answer(%mon[4].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[4]>125
%mon[4].name%#4=%random%.answer(%mon[4].name% is getting used to you. It seems to believe in you.)
else if happiness[4]>75
%mon[4].name%#4=%random%.answer(%mon[4].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[4]>25
%mon[4].name%#4=%random%.answer(%mon[4].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[4]<0
%mon[4].name%#4=%random%.answer(This is a little hard for me to say… %mon[4].name% simply detests you. Doesn't that make you uncomfortable?)

if happiness[5]>255
%mon[5].name%#5=%random%.answer(%mon[5].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[5]>225
%mon[5].name%#5=%random%.answer(%mon[5].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[5]>175
%mon[5].name%#5=%random%.answer(%mon[5].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[5]>125
%mon[5].name%#5=%random%.answer(%mon[5].name% is getting used to you. It seems to believe in you.)
else if happiness[5]>75
%mon[5].name%#5=%random%.answer(%mon[5].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[5]>25
%mon[5].name%#5=%random%.answer(%mon[5].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[5]<0
%mon[5].name%#5=%random%.answer(This is a little hard for me to say… %mon[5].name% simply detests you. Doesn't that make you uncomfortable?)

if happiness[6]>255
%mon[6].name%#6=%random%.answer(%mon[6].name% adores you. It can't possibly love you any more. I even feel happy seeing it.)
else if happiness[6]>225
%mon[6].name%#6=%random%.answer(%mon[6].name% seems to be very happy. It obviously likes you a whole lot.)
else if happiness[6]>175
%mon[6].name%#6=%random%.answer(%mon[6].name% likes you quite a lot. It seems to want to be babied a little.)    
else if happiness[6]>125
%mon[6].name%#6=%random%.answer(%mon[6].name% is getting used to you. It seems to believe in you.)
else if happiness[6]>75
%mon[6].name%#6=%random%.answer(%mon[6].name% is not very used to you yet. It neither loves nor hates you.)
else if happiness[6]>25
%mon[6].name%#6=%random%.answer(%mon[6].name% is very wary. It has scary viciousness in its eyes. It doesn't like you much at all.)
else if happiness[6]<0
%mon[6].name%#6=%random%.answer(This is a little hard for me to say… %mon[6].name% simply detests you. Doesn't that make you uncomfortable?)
```