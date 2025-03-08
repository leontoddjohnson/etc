---
title: movements
bookCollapseSection: false
math : true
---

# movements

{{% hint danger %}}
**This script is still under construction.** Right now, these docs represent the script in its current alpha state. There will probably be bugs ...
{{% /hint %}}

movements is a sequencer of preloaded samples or of slices from recorded input.

**Requirements:**

- grid
- audio files *or* sound source

## overview

We define two different "functionalities": **sample**, management of pre-loaded audio files, and **tape**, management of slices from recorded input. The idea is for these two script functionalities to share *roughly* the same attributes. I.e., if you can do it with **sample**, you can do it with **tape**. Thus, both share the same parameters, with a few caveats.

This script is ... 

## tldr; basic setup

### sample

1. Click **K2**, and load some samples.
2. On the sample config page, load samples onto a track cue by holding the sample pad and **ALT**.
3. Once you have samples you'd like to load onto a track, hold the track pad and **ALT**.
4. Start playing around with the sequence page, maybe adjust some levels on the levels page (select the **seq** page pad twice).
5. Adjust time for each track on the **time** page, and track levels on the **config** page.

### tape

TBD

# parameters

Both functionalities share mostly the same parameters. These parameters are at the track level and the sample/slice level. When you make adjustments to the track level, you (typically) will also make "proportional" adjustments at the sample/slice level.

## amplitude

This is just the amplitude of the playing sample/slice.

## filter

Be careful when setting the pattern ... 20k Hz, when swapped to high pass will essentially remove the sound. Keeping things at low pass (for the most part) will act as expected. Otherwise, if you want to swap, keep the filter parameter patterns on values other than 20k.

# sample functionality

Probably, the best way to get to understand the sample functionality is to start with the config page, and work your way backward ... When playing, it's easier to think the other way around.

## parameters

...

# tape functionality


# grid navigation

{{% hint warning %}}
**reminder**  
move all this to the main movements page (make a "grid" section). Then, talk about grid operations within only *sample* and *tape* pages. I.e., remove this page, leaving only the two sub-pages (sample and tape)
{{% /hint %}}

For sample and tape functionalities, there are four grid pages:

- sequence
- levels
- time
- config

For the most part, these pages are the same for both sample and tape functionalities, with small deviations for tape. In general, all grid pages will share the same navigation bar on the lower right.

{{< figure src="main_grid.png" >}}

Here, **S** corresponds to **sample** and **T** corresponds to **tape**. For each of these, you have the following:

- **_1:** toggle between **sequence** and **levels**.
- **_2:** the **time** page
- **_3:** the **config** page

The **mode** corresponds to the following:

- **PLAY MODE** (bright)
- **FOCUS MODE** (not bright)

Both the **mode** and **ALT** pads correspond to different functions within sample or tape.

## selected track

... 

Note: when you switch between **sample** and **tape** functionalities, your selected track will revert to the "first" track. Otherwise, your selected track should remain preserved. For example, if you select Sample Track 2, and move from the **sample_levels** page to the **tape_levels** page, then your new selected track will be the Tape Track 1.