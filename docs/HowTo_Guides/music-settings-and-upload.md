# Music Settings and Uploading Music

## Default Battle Themes
To set the default battle music for your region:

- Go to the Region tab in Mapbuilder.

- Enter your desired track in the relevant battle music input fields.

[insert image here]

## Setting Music Per Map
If you want a specific map to use a different track:

- Open the map in Mapbuilder.

- Navigate to the Settings tab.

- Scroll down and enter your music file into the Music input field.

Note:



!!! note "Night Time Ambience"

    You can optionally set a night version of your track. Most places don’t use this, but it can help add atmosphere in key areas.

!!! note "Night Time Ambience"

    For interiors within a town (e.g. houses), you should usually use the same music as the town itself - unless it’s a unique location.

!!! tips "Kyledove's Tip"

    When multiple maps share the same music track, the engine will seamlessly continue the song as the player moves between them - no restart! Super clean.

[insert image here]

## Triggering Music via jCoad

Please see the following example from Sinnoh Region:

```json 
%random%=npc(01k86ru4,down)if !beaten
%random%.spot(6)&track=db:s/brm2ibkabxai4t5/Look%21%20Shorts%20Boy.mp3
%random%.msg(You're a Pokemon Trainer, and so am I!|Our eyes met, so battle we must!)|&battle=613;
else
%random%.msg(Don't be shy about talking to Trainers you'd like to battle.|Pokemon grow stronger and stronger from battling.)
```

You can use this as a separate trigger anywhere - not just when a trainer spots the player. For example, it’s useful during cutscenes if you want to change the music after a specific event occurs.

`&track=db:s/brm2ibkabxai4t5/Look%21%20Shorts%20Boy.mp3`

## Setting a Song for Specific Trainer Battles

1. **Set it directly in the Trainer Battle Data Context Menu**
    Simply input the desired music track in the designated **Theme** field of the trainer's data.
    [insert image here]

2. **Set it manually via jCoad**
    Trigger the battle with a custom theme like so:
    `battle=843;theme db:s/wo28e1a78gcfg35/Seth%20Theme.mp3`

!!! note "Overrides"

    Any time you set music via jcoad or directly in the Trainer Battle Data, it will automatically override whatever is set in your Region settings. Simple!

## Uploading Music
**Optional Step: Downloading from SoundCloud**
If you found a song you like on SoundCloud, you can use [KlickAud](https://www.klickaud.co/) to download it in `.mp3` format.

1. **Upload your MP3 to Dropbox**
    * Right-click the file > Share

    * Click Create link > Copy link

    * Example link:
        `https://www.dropbox.com/scl/fi/69vowblrn64j6bes6mi8s/TomsDinerBW.ogg?rlkey=hjonbnsh93vzne572kuozv12h&st=pa462te2&dl=0`

2. **Convert the Dropbox Link**
    * Replace everything before the file ID with `db:s/`

    * Replace all instances of & in the link with `^` (This step is only necessary if you are adding the Dropbox link to jCoad)

    * Final format:
       `db:scl/fi/69vowblrn64j6bes6mi8s/TomsDinerBW.ogg?rlkey=hjonbnsh93vzne572kuozv12h^st=pa462te2^dl=0`

3. **Paste this link into Pokengine - refer to Music Settings page**

We have a [central music repository](https://docs.google.com/spreadsheets/d/1Xyfc4jBWfXcuyLiJx3uErtb6lZyAsQ5ypMVCUBDzTt4/edit?usp=sharing) that anyone is welcome to take from or contribute to.

!!! warning "Broken Links"

    Since music is externally hosted, there’s always a risk that links may break or stop working in the future. Unfortunately, Pokengine does not currently support uploading `.mp3` files directly to the engine, so external hosting is the only option for now.


