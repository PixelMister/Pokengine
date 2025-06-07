# Move Relearner & Tutor (How-to)

!!! note
    Detailed code can be found in the **Code Library** – this page is just for examples and tips.

If you want a Pokémon to relearn a move it has already passed in its level-up set, there are several ways to do this:

- **Via the Party Menu** – No restrictions, no item required, no cost.  
- **Via an NPC** – Some NPCs may offer move relearning services.

!!! note
    The same syntax is used for Move Tutors!

---

## Via the Party Menu

Simply add this to your Region Vars:

```plaintext
var[move_learner_context]=1
```

---

## Move Relearner NPC Example  
*(Item Required – Uses a Heart Scale to reteach a move)*

```plaintext
%random%=npc(013flqt5,down)
%random%.msg(I can help your Pokemon relearn a move that it has forgotten, if you give me a Heart Scale! Would you like to have a Pokemon relearn a move?)&answers=Yes,No

if item[0683drku]
Yes=%random%.answer()&movelearner=max:1;cost:0683drku 1;
No=%random%.answer()
else
Yes=%random%.answer(But you don't have any Heart Scales...)
No=%random%.answer()
```

!!! note
    Our move relearner is designed to show **every move** in a Pokémon’s level-up set – even ones that are above its current level.  
    Those higher-level moves will appear **greyed out** and cannot be selected.  
    This gives players visibility into what their Pokémon can learn in the future.

---

## Move Tutor NPC Example

```plaintext
%random%=npc(01qplyfm,up)
%random%.msg(Can you imagine?#If this volcano were to erupt?|The explosion would be the end of us. How terrifying is that?|While we're terrified, would you like me to teach Explosion?)||&answers=Yes,No
Yes=%random%.answer(You're terribly brave!|Which Pokemon should I teach Explosion?)&movelearner=moves:07nhrhjt
No=%random%.answer(Yeah, you're right.#It is too terrifying.)
```

!!! note
    The Move Tutor screen will still appear even if a Pokémon **cannot learn** any of the listed moves – those moves will simply be greyed out.  
    Depending on how you've set it up, you may be able to scroll through your entire party to see which Pokémon are eligible to learn the move(s).

> 💡 **Credit**: The Move Relearner system was developed by **RoughKnight**.
