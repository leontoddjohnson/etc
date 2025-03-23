---
title: movements
bookCollapseSection: false
math : true
---

# movements

movements is a sequencer of preloaded samples or of slices from recorded input.

**Requirements:**

- grid (128)
- audio files *or* sound source

## overview

This script was designed with flexible sequencing and independent track adjustment in mind. movements consists of 11 individual tracks, each with their own separate clock. Each track has its own set of parameters which can be individually adjusted, without affecting the other tracks. Also, each track allows you to sequence up to 128 steps.

The 11 tracks are divided into two different "functionalities":

- **sample** (tracks 1-7): pre-loaded audio files
- **tape** (track 8-11): slices from recorded input (or loaded files)

The idea is for all tracks (regardless of functionality) to share *roughly* the same attributes. I.e., if you can do it with **sample**, you can do it with **tape**, and vice versa. Thus, both share the same parameters, with a few caveats.

{{% details title="some terminology" open=false %}}

**vocabulary**

Just a few terms that might otherwise be easily confused:

term | definition
:---: | :---
page | a *grid* page, navigable by the 6 nav keys on the lower right corner of the grid
display | a display page on the norns UI
pattern | a collection of steps for triggering or defining parameters
bar | one of eight partitions of 16 steps
sample | an audio file loaded into a **sample** bank
slice | a small section of the **tape** partition

**notation**

- **bold** text indicates (1) a functionality (sample or tape), or (2) a user interface (e.g., a key or encoder on your norns, a pad on the grid, or a specific page or display).
- *italics* indicates emphasis or some special term.
- `monospace` denotes a parameter adjustment or parameter value.

{{% /details %}}

## tldr; basic setup

### sample

*Refer to the grid navigation bar and the **sample config** page, below.*

1. Load some samples from a folder into a bank with **K2** on the **sample main** display.
2. On the **sample config** (grid) page, load samples onto the selected track *cue* by holding **ALT** + the sample pad.
3. Once you have samples you'd like to load onto a track, hold **ALT** + the track pad. When this track's sequence is played, it will cycle through these samples.
4. Add some steps on the **sample seq** page. Maybe adjust some levels on the **sample levels** page (select the **S1** pad twice).
5. Play with the clock time for each track on the **sample time** page, and control track levels on the **sample config** page or the **sample params** display.
6. Navigate to the **delay** display section with **K1 + E1**, and adjust the **sample** delay on the corresponding display.

### tape

*Refer to the grid navigation bar and the **tape config** page, below.*

1. Choose a buffer with load some audio into a partition:
    - Option 1: Load a file at the current slice with **K2** on the **tape main** display.
    - Option 2: Record into the current slice with **K2** on the **tape slice** display.
2. On the **tape config** (grid) page, load slices onto the selected track *cue* by holding **ALT** + the slice pad.
3. Once you have slices you'd like to load onto a track, hold **ALT** + the track pad. When this track's sequence is played, it will cycle through these slices.
4. Add some steps on the **tape seq** page. Maybe adjust some levels on the **tape levels** page (select the **T1** pad twice).
5. Play with the clock time for each track on the corresponding **tape time** page, and control track levels on the **tape config** page or the **tape params** display.
6. Navigate to the **delay** display section with **K1 + E1**, and adjust the **tape** delay on the corresponding display.

# grid

## navigation

For *both* the **sample** and **tape** functionalities, there are four grid pages:

- sequence
- levels
- time
- config

For the most part, these pages are the same for both functionalities, with small deviations for **tape**. *All* grid pages will share the same navigation bar on the lower right (with **mode** and **ALT** pads included).

{{< figure src="main_grid.png" class="center-image-75">}}

Here, **S** corresponds to **sample** and **T** corresponds to **tape**. For each of these, you have the following:

- **_1:** toggle between the **sequence** and **levels** page
- **_2:** the **time** page
- **_3:** the **config** page

The **mode** corresponds to the following:

- **PLAY MODE** (bright)
- **FOCUS MODE** (not bright)

The **mode** and **ALT** pads typically correspond to different functions within **sample** or **tape**.

## sample pages

### sample config

Often, the best place to start is with the **config** page.

{{< figure src="sample_config_1.png" >}}

- Each row in the `track param adjustment` region corresponds to a track. Making adjustments here will affect the whole track (for more on this, see the [parameters](#parameters) section, below).
- The `track param selection` region indicates the  

# parameters

Both functionalities share the following parameters:

- amplitude
- panning
- filter
- delay
- probability
- scale
- interval

These are adjustable at both the track level and the step level. In addition to these, the **sample** functionality has an option to add *noise* to a sample, and the **tape** functionality has an option to set the *overdub* (or "pre"/"preserve") level for recording, and loop-*crossfade* time for slices. These three parameters are adjustable only at the track level.

Samples are loaded onto **sample** tracks, and recording slices are loaded into **tape** tracks. These samples/slices are triggered in a sequence by a pattern of selected steps. Further, each step can have its own set of parameter settings (for the 7 above parameters); so, tracks have parameter patterns so their parameter values can can change from step to step.[^fn:interval]

[^fn:interval]: An exception to this rule is *interval*. To prevent playback sounds from getting overly complex and dissonant, the *interval* value remains constant based on the track selection. Adjusting an *interval* step is equivalent to adjusting the value across all steps for that track. This also encourages the user to record separate pitches individually to improve sound quality.

Lastly, when you make adjustments to the track level, you will also make proportional adjustments to each step based on the parameter pattern and the track level itself; we'll call this "squelching".

## amplitude

This is the amplitude (volume) of the playing sample/slice.

**Squelching:**

The track amplitude level, $v_{\text{max}}$, is the maximum amplitude allowed. A pattern step value of $v$ on a scale between $[0, 1]$ will be squelched to one on the scale between $[0, v_{\text{max}}]$. 

## panning

...

## filter

Be careful when setting the pattern ... 20k Hz, when swapped to high pass will essentially remove the sound. Keeping things at low pass (for the most part) will act as expected. Otherwise, if you want to swap, keep the filter parameter patterns on values other than 20k.

## scale

...

# sample functionality

Probably, the best way to get to understand the sample functionality is to start with the config page, and work your way backward ... When playing, it's easier to think the other way around.

## parameters

...

# tape functionality

...

## selected track

... 

Note: when you switch between **sample** and **tape** functionalities, your selected track will revert to the "first" track. Otherwise, your selected track should remain preserved. For example, if you select Sample Track 2, and move from the **sample_levels** page to the **tape_levels** page, then your new selected track will be the Tape Track 1.