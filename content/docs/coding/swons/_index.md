---
title: swons
bookCollapseSection: false
booktoc: false
---

# swons

> An extension of @tehn's *[snows](https://monome.org/docs/iii/library/snows/)*. 

Find the Lua file [here](https://raw.githubusercontent.com/leontoddjohnson/iii/refs/heads/main/swons.lua). Use single **KEY** presses to cycle between the following modes:

## rings

Note sequence "sprockets" through at the top of the ring each time the moving point hits 12 o'clock. Dimly lit notes are passed or to come, and the *next* note is always brightly lit at the 12 o'clock position. 

- **ENC**: adjust ring speed and direction
- **KEY + ENC**[^fn:stop]: stop movement

[^fn:stop]: Any dial adjustment will do.

## notes

The top portion shows the notes in the sequence. The selected note is brightest, the currently playing note is slightly less bright, and the rest are dim.

The bottom portion shows the selected window of the scale (within 15 chromatic notes), going from left to right. The selected note placement is the brightest, root notes are less bright, natural notes are less bright, sharps and flats are dim, and notes off the scale are dark.

- **ENC (clockwise)**: select a note
- **ENC (counter clockwise)**: place the note on the scale
- **KEY + ENC**: add/remove the last note of the sequence (up to 16 notes)[^fn:new]

[^fn:new]: New notes are the first of the window.

## window

Each sequence consists of notes from the scale within a window of 15 chromatic notes of the main scale (see below). The window is indicated by lights for each in-scale note. The root notes are brightest, natural notes are less bright, sharps and flats are dim, and notes off the scale are dark.

- **ENC**: define the window for the ring
- **KEY + ENC**: increment the scale window in octaves

## scale

Unless defined otherwise (see below), there are 8 scales to choose from, respectively: major, natural minor, major pentatonic, minor pentatonic, dorian, okinawa, whole tone, and chromatic. These scales are played using the 128 MIDI notes, where note `0` is the lowest *C*, and the rest follow in semitones (up to 10 full octaves).

The ring around **ENC 4** shows a visualization of the scale across 5 chromatic octaves inclusive (61 notes), from the lower left of the ring to the lower right. Here, the root note is the brightest, natural notes are less bright, sharps and flats are dim, and notes off the scale are dark.

- **ENC 1**: select a scale
- **ENC 2**: select root note (C, C#, D, ..., B)[^fn:ui]
- **ENC 3**: set starting octave (can be from 1 to 5; 3 is a good start)
- **ENC 4**: modulate the scale down or up by an in-scale interval[^fn:low_mod]

[^fn:ui]: The UI here is similar to the scale window, with no root.
[^fn:low_mod]: At the lowest and highest octave settings, modulating the scale may reduce the total number of notes due to MIDI only consisting of 128 notes.

You can add up to 28 scales to the top of the Lua file. Scales are defined by a sequence of semitone intervals *whose sum is equal to 12* (e.g., `{2, 2, 1, 2, 2, 2, 1}` represents a major scale). You can use the following function in Maiden to build these:

```lua
music = require 'musicutil'

function scale_intervals(scale)
  scale = music.generate_scale(1, scale, 1) or {}
  intervals = {}
  for i = 2, #scale do
    table.insert(intervals, scale[i] - scale[i - 1])
  end
  return intervals
end

-- for example
scale_intervals("phrygian")
```