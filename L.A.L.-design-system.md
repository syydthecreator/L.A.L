# L.A.L. — design system

Chrome Hearts × teenage engineering: gothic blackletter on a matte-black hardware chassis with chrome, brushed-aluminum, and dark-red-glass surfacing.

## Typography

| Font | Used for |
|---|---|
| UnifrakturMaguntia | Wordmark, ABCD slot letters |
| Eagle Lake | All other labels (buttons, knobs, pads, fader, tagline) — 8.5px |
| JetBrains Mono | LCD readout |

Sizes: wordmark `clamp(22–35px)` · ABCD letters `pad-size × 0.7` · LCD readout `clamp(20–33px)`, weight 800 · pad key numbers 10px · everything else 8.5px.

## Color

| Token | Value | Use |
|---|---|---|
| `--chrome-hi` | `#f5f6f8` | Bright silver text/shine |
| `--chrome-mid` | `#b9bcc2` | Dull silver labels |
| `--chrome-lo` | `#4a4c50` | Silver gradient shadow |
| `--bg-0` / `--panel` | `#08080a` / `#0c0c0e` | Chassis darks |
| `--pad-face` | `#1a1b1e` | Pad key surface |
| `--red` / `--red-hi` / `--red-glow` | `#7c0f16` / `#c81c26` / `#ff2b39` | Signal red — glow, LEDs |

Component accents: LCD glass `#7a0d13→#33050a`, REC chip `#8f131a→#3a080c`, aluminum chips (ERASE/LATCH) `#cdd0d4→#83868b`, CORR jade `#178a64→#0a4a36`, grille silver `#d2d5d9→#797c81`.

## Materials

Matte black chassis · polished chrome (clipped-text gradient, wordmark/ABCD/bright labels) · brushed aluminum (diagonal grain, print-only chips) · dark red glass (LCD) · woven silver mesh (grille) · flat rubber/plastic (pad keys).

## Spacing

One fluid unit drives everything: `--pad-size: clamp(46–64px)`, `--pad-gap: pad-size / 2`. All buttons/knobs/pads are 1 square; fader is 2 squares + a gap; SHIFT/FX are half a square.

## Radius

Chassis 6px · buttons/pads/chips 2px · knobs/LEDs 50% (circular) · grille 0/6px/0/0 (only the chassis-touching corner rounds).

## States

- **Engaged** (steady on): red edge-ring glow only, no fill/LED
- **Flash** (on press): momentary red bottom-bloom, fades 0.25s
- **Two-tier buttons** (REC/ERASE, RPT/LATCH, TIME/CORR): all interaction scoped to the top chip; bottom chip is a non-clickable print
- **SHIFT**: physically depresses when engaged, not just a glow
- **Knobs**: endless rotation, decoupled from clamped value range
