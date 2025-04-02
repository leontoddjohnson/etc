---
title: moments
bookCollapseSection: false
math : true
---

# moments

moments that once were.

## set up

**requirements**

- norns
- input (mono or stereo)
- grid (optional, but recommended)

**in maiden ...**

```
;install https://github.com/leontoddjohnson/moments
```

## basic idea

Constantly record the last `loop length` seconds of input, and allow four voices to play back from (four) random points within that loop.

- The voices will only move if the amplitude of the input goes above a threshold. This creates a strange sort of lifelike feel.
- The random starting point for each voice is updated (randomly within the buffer) based on a fraction of the tempo set in `PARAMS/CLOCK`. Each voice has it's own "move rate".

# ui

{{< figure src="moments_example.png" class="center-image-75">}}

- The total loop length can be updated using either **K2** or **K3**
- Adjusting either **E2** or **E3** will update the loop length

Here, the four dots represent the four voices. When the `input_type` is set to *mono*, the four voices read from the same buffer. Otherwise, when `input_type` is set to *stereo*, voices 1 and 2 (the top two dots) read from the left input, and voices 3 and 4 read from the right input.

# grid

This script is compatible with either 128-pad monome grids, or the 64-pad Launchpad. There is a left 64-pad section, and a right 64-pad section. Each section has a top and bottom portion with four rows. Each row corresponds to a voice (or, in the UI, a dot).

**left section**

{{< figure src="page_1.svg" class="center-image-50">}}

- **level**. With level, the lowest is on the left, highest on the right. If you push the currently selected level (i.e., the highest bright pad), the level will revert to 0, and all pads in that row will dim. Once you select a new level, that will be set.
- **pan**. The pan pads are in increments of 0.25, where hard left is -1 and hard right is 1. So, shown here, the second voice is at (left) -0.5. Select the bright pad to revert back to center panning (0).

**right section**

{{< figure src="page_2.svg" class="center-image-50">}}

- **dot move time**. The time between dot moves is determined by a fraction of the `CLOCK` tempo. The 8 pads correspond to $\displaystyle \frac{1}{k}$ of a beat for $k = 8, 7, ..., 1$. I.e., faster movements are on the left, and slower less frequent movements are on the right.
- **rate**. The rate of a voice can be forward or reverse. To toggle between the two, select the bright (selected) pad. These pads divide the rate in the following increments, where `ova` is "octave", `5th` is a "perfect 5th" transposition of the sample, and `root` is a rate of 1.0:
  - `-2ova+5th | -ova | -ova+5th | root | +5th | +ova | +ova+5th | +2ova`
  - The dimly lit pads indicate the octave-level intervals.
  - The direction of the dot (forward/reverse) dictates the order of the intervals, so when *forward*, the last pad is dimly lit.

# other parameters

See `PARAMS` for more parameters. Play around with them; see what happens! :)