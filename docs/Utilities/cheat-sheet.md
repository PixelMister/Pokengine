# Kyledove's Cheat Sheet

Over the years, I’ve compiled a handy collection of code snippets to speed up my workflow. Feel free to use them too! This page is meant for quick reference - if you're looking for detailed explanations, please refer to the more detailed **How-To Guides**. A basic understanding of jCoad is assumed.

### NPC
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

### NPC Path - alternates between wwo directions
```json
%random%.path(0d,pause300,0r,pause300*)
```

### NPC Path - spinning
```json
%random%.path(0r,pause300,0d,pause300,0l,pause300,0u,pause300*)
```

### Trigger to make npc return to original direction after speech
```json
&with=%random%&direction=d
```

### Pokemon NPC - register as seen and plays cry sfx
```json 
%random%.npc(006ii7ud,right,0x0)
%random%.msg(SKITTY: Miyaaaan?)&!cry=00cz496x&show=00cz496x
```

### Permanent Icon Above NPC
```json
%random%.icon(37,1)
```

### Signpost that creates textbox without having to press action button, simply by walking into it
```json
msg()
if direction=up and ontouch
msg()
```

I highly recommend keeping a separate file to track the NPCs in your region. It’ll save you a lot of time compared to constantly searching the site.
Here’s an example list from one of my projects:

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
