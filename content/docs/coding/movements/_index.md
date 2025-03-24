---
title: movements
bookCollapseSection: false
math : true
---

# movements

movements is a sequencer of preloaded samples or of slices from recorded input.

**requirements**

- grid (128)
- audio files *or* sound source

**in maiden ...**

```
;install https://github.com/leontoddjohnson/movements
```

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
display | a display on the norns *screen*
`pattern` | a collection of steps for triggering or defining parameters
`bar` | one of eight partitions of 16 steps
`sample` | an audio file loaded into a **sample** bank
`slice` | a small section of the **tape** partition

**notation**

- **bold** text indicates (1) a functionality (either sample or tape), or (2) a user interface item (e.g., a key or encoder on your norns, a pad on the grid, or a specific page or display).
- *italics* indicates emphasis or some special term.
- `monospace` indicates some *particular* value (or collection of values) which could be selected or adjusted.

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

## sample

The **sample** functionality is meant for loading, playing, and sequencing audio files from a `bank`. There are 4 banks of up to 32 possible samples each, and there are 7 sample tracks with independent clocks. The **sample** functionality in this script uses an adaptation of the [Timber](https://github.com/markwheeler/timber/tree/master) engine.

- Each track has a `track_pool` of samples that the sequencer will rotate through. You can adjust *how* (forward, backward, or random) with the `play_order` parameter in the **PARAMS** menu.
- Once a sample is assigned to a `track_pool`, it cannot be assigned to any other track. So, you cannot have a sample "shared" between tracks.
- A `track_pool` can only contain samples from *one* bank. That said, each track can have a separate `track_pool_cue` for each bank, and any of these can replace the `track_pool` on the fly using the grid interface (see the [grid](#grid) section below, as well as the [ui](#ui) section).
- [According to the Timber developer](https://llllllll.co/t/timber/21407), Timber is intended to play up to 7 voices at a time; this is why the **sample** functionality is limited to seven tracks.
- When playing a sequence, movements will stop playing the "current" step before starting to play the next step.

{{% hint warning %}}
If an audio file is *over* 5 seconds stereo or over 10 seconds mono (at 48kHz), then Timber will stream it. Otherwise, shorter files will be loaded into the Timber buffer. Shorter audio files are more versatile in Timber, as streaming samples cannot be played backward, and they do not have the `Infinite Loop` option.
{{% /hint %}}

## tape

The **tape** functionality is meant for playing, recording, and sequencing slices from a `partition` of the stereo [softcut](https://monome.org/docs/norns/softcut/) buffer(s). There are *four* such partitions: each one is 80 seconds long[^fn:softcut], and each partition is divided into 32 slices. By default, these slices are evenly distributed, so they start at 2.5 seconds long, but the user can adjust the start/stop positions for each slice. There are 4 tracks, each one with access to the four partitions.

[^fn:softcut]: In total, the stereo softcut buffer is about 350 seconds long, and for this script, we use softcut for both the **tape** and the **tape delay** functionality. Since delay time is synced with the internal clock, the **tape delay** uses $6 \cdot s$ seconds of the buffer, where 6 is the highest `clock_fraction` value, and $s$ is the number of seconds per beat of the internal **CLOCK/TEMPO**. With a low end BPM of 12, this equates to $6 \cdot (60 / 12) = 30$ seconds, leaving the 320 seconds needed for the **tape** functionality.

- The `track_pool` and `track_pool_cue` for **tape** behave the same as they do for the **sample** functionality, above. Just swap out the word "sample" with "slice", and "bank" with "partition".
- Each `partition` consists of two `buffer`s, which can be thought of as either a *single* stereo buffer or *two* separate mono buffers to swap between. You can assign tracks to record/play as mono from either buffer, or as stereo from both.
- A recording can only be made to a `slice`, which can only exist within a `partition`. (Of course, the beginning and end of any slice can be adjusted, within the bounds of the partition.)
- You can record to a slice in two ways:
  - "on demand" using the **tape slice** display
  - "in time" with the sequence using the **tape seq** grid page.

## delay

Both **sample** and **tape** have their own independent delay functionalities. The **sample** side uses a SuperCollider delay bus in the Timber engine, and **tape** uses softcut. Both delay times are synced to the internal **CLOCK** using the same `clock_fraction` options as the **sequence**r (see below).

{{% hint danger %}}
When using the **tape delay**, you should keep the internal tempo *over* 12 BPM; so 13 BPM at a minimum.[^fn:softcut]
{{% /hint %}}

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

The **mode** pad toggles between the following modes:

- **PLAY MODE** (bright)
- **FOCUS MODE** (not bright)

The **mode** and **ALT** pads typically correspond to different functions within **sample** or **tape**.

{{% hint info %}}
When you switch between **sample** and **tape** functionalities on the grid, the display will also update in turn (and vice versa).
{{% /hint %}}

## sample pages

### sample config

For both **sample** and **tape**, the best place to start is often with the **config** page.

{{< figure src="sample_config_1.png" >}}

#### track parameters

- Each row in the **track param adjustment** region corresponds to a track. Making adjustments here will affect a parameter for the whole track. Select a parameter to adjust/focus on with the **track param selection**. For more on these, see the [parameters](#parameters) section, below.
  - The focused parameter will be shared across functionalities and pages.

#### track selection

- Select a track in the **track selection** region. This really just sets the display and grid to "focus" on that track.

#### bank

- Select samples in the **bank** region. The selected pad will not light up until you hold the currently selected `bank` pad in the **bank selection** region.
- The dimmest pads indicate pads *with* samples (audio files) that have been loaded into the bank. Unlit pads are "empty".
- You can dictate the row/column for audio files in a bank by using a `<row><col>*...` naming convention, where `*` is `" "`, `"-"` or `"_"`. For example, the file with the name *23_sound.wav* would be loaded into the second row and the third column.
  - Duplicate indices will be overwritten by the latest of the two.
  - If the indices are invalid, movements will load the samples in order, left-to-right, top-to-bottom.
  - Folders with more than 32 files will stop loading at file #32.
- In **PLAY** mode ...
  - pushing a pad will play (or stop) the sample loaded into that pad.
  - "currently" playing samples will be indicated with a bright pad.
- Hold **ALT** + `a sample pad` to load a sample into the current `track_pool_cue`.
- When you're ready, load the cue into the `track_pool` with **ALT** + `the track selection`.
  - This will only work if you are already focused on the track to be loaded (i.e., you are pushing an already lit `track selection` pad).

#### play mode

- For a sample (or slice), the **play mode** is different from **PLAY MODE**. It represents the way a sample/slice will be played. For a selected `sample`, we have two sets of **play mode** options
  - Streaming Samples: `"Loop"  "Loop"  "1-Shot"  "Gated"`
  - Buffer Samples: `"Loop"  "Inf. Loop"  "1-Shot"  "Gated"`

#### bank selection

- Select one of the four banks here.
- 


## tape pages

### tape config

...

Notice that the slice start/end times can only be adjusted "in the vicinity" of the current slice. I.e., you'll notice that it's not easy to use the partition range to "move" a slice anywhere in the partition. This is to keep slices in positions that *for the most part* divide the partition up, in order.

# ui

## navigation

...

## sample displays

...

## tape displays

...

## delay displays

...

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

[^fn:interval]: Right now, an exception to the parameter pattern rule is *interval*. To prevent playback sounds from getting overly complex and dissonant, the *interval* value remains constant based on the track selection. Adjusting an *interval* step is equivalent to adjusting the value across all steps for that track. This also encourages the user to record separate pitches *individually* to improve sound quality.

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

# footnotes