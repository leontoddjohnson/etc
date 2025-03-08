---
title: movements
bookCollapseSection: false
math : true
---

# movements

{{% hint danger %}}
**This script is under construction.** Right now, these docs are 
{{% /hint %}}

This script is a sequencer of samples or recorded input. It requires a grid, and that's probably the best place to start ...

# sample functionality

Probably, the best way to get to understand the sample functionality is to start with the config page, and work your way backward ... When playing, it's easier to think the other way around.

## parameters

...

### filter

Be careful when setting the pattern ... 20k Hz, when swapped to high pass will essentially remove the sound. Keeping things at low pass (for the most part) will act as expected. Otherwise, if you want to swap, keep the filter parameter patterns on values other than 20k.

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

{{< figure src="grid_nav.png" >}}

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