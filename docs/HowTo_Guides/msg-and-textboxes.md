# Msg and Textboxes
## Introduction
Textboxes can be created in two main ways:

- **msg()** – Typically used for NPCs, signs, and standard dialogue interactions.

- **&textbox=** – Used when you want to trigger a textbox externally, such as during a cutscene or scripted event.

While both methods serve similar purposes, there are important differences when using `&textbox=:`

Since it's not wrapped in parentheses, certain symbols (like `|`) can cause issues, as they’re interpreted differently by the engine.

To include a line break, you must use `\|`. A plain `|` will not work.
`execute(freeze&textbox=Where are you going?\|Haha, I'm just kidding! Enjoy your travels, kid)`

In the case above, `\|` ensures the dialogue splits onto two lines properly.

## NPC Nametags
Since this is a 2D top-down pixel art game where characters can’t show much expression, following cutscenes with multiple speaking characters can be tricky. To help, we’ve implemented a nametag system.

`%random%.msg(<name:Lund,255,146,50>Have you managed to collect 10 Cliff Feathers?)`
In this example, the NPC is named `Lund` with an orange nametag color set using the RGB value `255,146,50.` If you omit the color, the nametag will use the default text color.

The nametag will persist throughout the entire speech, so be sure to set a new nametag if another character speaks during the same event. You can also clear the nametag by using `<name:>` with no text.

Unfortunately, the engine doesn’t currently support showing images with nametags, but creative devs like **KingTapir** have found clever workarounds and may offer assistance if you ask nicely.

!!! warning "Accessibility"

    Choose colors carefully to ensure good readability and accessibility for all players.

!!! tip "Nametags"

    Always use nametags for important characters, especially during cutscenes with multiple speakers! Pick a unique color for recurring characters like rivals to help players keep track.

## Text Alignment

Textboxes and msg are left-aligned by default.
Use the tags in the below example to change alignment:
```json 
msg(<align:center>This text is center aligned)
```
```json 
msg(<align:right>This text is right aligned)
```

!!! note "Persistent Alignment"

    If you don’t close the alignment with `<align:>`, the alignment will persist for all following messages in the same speech.