# Kyledove's jCoad Cheat Sheet

Over the years, Kyledove has compiled a handy collection of code to speed up your region creation workflows. This quick reference page provides code snippets, that you can copy and paste directly into an object. If you're looking for detailed explanations, please refer to the more detailed **How-To Guides**. A basic understanding of jCoad is assumed.

## Non Player Characters

### Quick NPC
```json
%random%=npc()
%random%.msg()
```

### Trainer Battle NPC
```json
%random%=npc()
if !beaten
%random%.spot(3)
%random%.msg()&battle=;
else
%random%.msg()
```

### NPC with a Question
```json 
%random%.msg(?)&answers=Yes,No
Yes=%random%.answer()
No=%random%.answer()
```

### Move Tutor NPC
```json 
%random%.msg()&answers=Yes,No
Yes=%random%.answer(All right, pick which Pokemon I should teach it to.)&movelearner=moves:07a4uh4j
No=%random%.answer(Well, that's fine, too.)
```

### NPC Path - Alternate Between Two Directions
```json
%random%.path(0d,pause300,0r,pause300*)
```

### NPC Path - Alternate Between Two Directions
```json
%random%.path(0r,pause300,0d,pause300,0l,pause300,0u,pause300*)
```

### NPC Path - Return to Original Direction After Speech
```json
&with=%random%&direction=d
```

### Pokemon NPC - Register as Seen and Plays Cry SFX
```json 
%random%.npc(006ii7ud,right,0x0)
%random%.msg(SKITTY: Miyaaaan?)&!cry=00cz496x&show=00cz496x
```

## Signs
### Automatic Sign Interaction (Ontouch)
```json
msg()
if direction=up and ontouch
msg()
```

## Icons
### Permanent Icon Above NPC
```json
%random%.icon(37,1)
```
!!! tip "NPC Overworld Log"

    We highly recommend keeping a separate file to track the NPCs in your region. It'll save you a *lot* of time, compared to constantly searching the site.

Here's an example list from a developer project:
**Johto**
- `01ih0r1l` youngster

- `01ll2v4i` schoolboy

- `01cgzbbj` bug catcher

- `01zdunzm` lass

- `01bj2c1x` ace trainer man

- `01q8oh6a` ace woman

- `01hl0ytt` aroma lady

- `0137s72e` blonde pigtail battle girl

- `01hrk1do` blonde squinty rocker guy

- `017505nk` camper boy

- `011szhnf` camper girl
