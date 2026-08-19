# L.A.L. — design system

Chrome Hearts × teenage engineering, cast in bronze instead of silver: gothic blackletter on a matte-black hardware chassis, surfaced in cast bronze, bone/marble ivory, and dark oxblood glass.

## Typography

| Font | Used for |
|---|---|
| UnifrakturMaguntia | Wordmark, ABCD slot letters |
| Eagle Lake | Buttons, knobs, pad names, fader, tagline |
| Pirata One | LCD icon-grid screen labels (FILTER, DELAY, TEMPO, ERASE, CORRECT, SHIFT, TIME, PUMP, OUT) |
| JetBrains Mono | LCD digit readout, base UI font |

Sizes: wordmark `clamp(22–35px)` · ABCD letters `pad-size × 0.7` · LCD readout `clamp(20–33px)`, weight 800 · pad key trigger letters 13px · everything else (Eagle Lake/Pirata One labels) `min(8.5px, pad-size × 0.2053)` — nominally 8.5px at desktop size, scaling down below the mobile pad-size floor so labels never overflow.

## Color

The `--chrome-*` token names are legacy from an earlier silver palette — their values are now warm bronze/gold, not chrome. Kept as-is rather than renamed, to avoid touching every rule that references them.

| Token | Value | Use |
|---|---|---|
| `--chrome-hi` | `#d9b571` | Bright bronze — text/shine, highlight stop |
| `--chrome-mid` | `#a3814f` | Mid bronze — labels, gradient body |
| `--chrome-lo` | `#5c4423` | Dark bronze — gradient shadow |
| `--bg-0` / `--panel` / `--panel-2` | `#08080a` / `#0c0c0e` / `#101012` | Chassis darks |
| `--pad-face` / `--pad-face-2` | `#1a1b1e` / `#101114` | Pad-grid recess (not the keycap itself — see Materials) |
| `--red` / `--red-hi` / `--red-glow` | `#7c0f16` / `#c81c26` / `#7a1810`–`#ff2b39` | Signal red — engaged glow, LEDs, LCD icon lit-state |
| `--text` / `--text-dim` | `#e9e9ec` / `#8a8a90` | Body text |

Component accents — each of these is a full gradient in the CSS, not a flat swatch; end stops shown:

- **Bronze family** (the machine's primary metal): wordmark/ABCD clipped-text gradient, grille mesh, SHIFT/OUT buttons, TEMPO knob, shield icon's "A" slot signal, TIME/CORR chip — ranges across `#f2e0b8 → #d9b571 → #c9a468 → #a3814f → #8a6a3a → #6b4f28 → #5c4423`
- **Bone/marble ivory**: pad keycaps, VOL/FILTER/PUMP knobs, ERASE/LATCH chip, shield icon's "B"/"D" slot signal — `#faf7ef → #ece5d3 → #cec5ac → #b0a88f`, flat form `#f0ece0`
- **Oxblood glass**: LCD screen background `#b03a28 → #7a1810 → #4a0f0a → #2a0805`; REC chip `#8f131a → #5c0d12 → #3a080c`
- **Gunmetal steel**: default knob body (any knob not overridden above) `#8d9096 → #55575c → #3a3b3f`
- **Sapphire blue** `#0f52ba` — single accent, shield icon's "C" slot signal only
- **Grape purple** `#5c1f78 → #3f1450 → #260a30` — single accent, RPT chip only

The shield icon's four quadrants double as a per-slot tell: A bronze, B bone white, C sapphire, D bone white again (same tone as B, reused on purpose rather than inventing a fourth color).

## Materials

Matte black chassis · cast/polished bronze (clipped-text gradient on wordmark/ABCD/bright labels; grille; several buttons and one knob) · bone/marble ivory (pad keycaps and three of the knobs — not rubber, not flat plastic) · dark oxblood glass (LCD, REC chip) · gunmetal steel (the plain, unaccented knob body) · two single-accent gemstones (sapphire, grape purple) reserved for one control each rather than spread across the palette.

## Spacing

One fluid unit drives everything: `--pad-size: clamp(41.4–57.6px)` (a fixed-viewport desktop range; below that it shrinks further via a width-aware formula so mobile layouts still fit), `--pad-gap: pad-size / 2`. All buttons/knobs/pads are 1 square; fader is roughly 2 squares + a gap; SHIFT/FX are half a square. Nearly every other dimension in the sheet — icon-grid squares, label widths, fader/knob-pointer sizes, font sizes — is a `calc()` off this one variable, so the whole face rescales as one unit rather than by individual breakpoint overrides.

## Radius

Chassis 6px · buttons/pads/chips 2px · knobs/LEDs 50% (circular) · grille 0/6px/0/0 (only the chassis-touching corner rounds).

## States

- **Engaged** (steady on): red edge-ring glow only, no fill/LED
- **Flash** (on press): momentary red bottom-bloom, fades 0.25s
- **Two-tier buttons** (REC/ERASE, RPT/LATCH, TIME/CORR): all interaction scoped to the top chip; bottom chip is a non-clickable print
- **SHIFT**: physically depresses when engaged, not just a glow
- **Knobs**: endless rotation, decoupled from clamped value range

## Motion

No boot/entrance animation currently — the machine renders instantly at full opacity. Several approaches (whole-machine blur/fade, a melting bronze-shell cover, per-control stagger) were tried and pulled back out; if this gets revisited, keep it to a single animation on `#instrument` rather than per-control staggering, which read as "chunky" in practice.
