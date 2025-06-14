# Happiness Checker NPC
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