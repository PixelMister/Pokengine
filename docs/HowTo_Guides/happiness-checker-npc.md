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