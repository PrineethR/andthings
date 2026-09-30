# &things — landing page

Single file: `index.html`. No build step. Earlier versions are in `archive/`:
`v1-monochrome-figures.html` (technical figures) and `v2-collage.html` (collage,
before the Magritte pass).

## v2 thesis

The noun after the `&` never settles (things → objects → spaces → people → futures →
stuff) until a printer's manicule pokes the ampersand and knocks the word clean off.
The provoked `&` floods green, steps forward, and the camera dives into its thickest
stroke until the glyph's own fill is the page.

Visual register: collage — cut paper with offset paper shadows, engraving hatch,
museum tombstone captions, one strip of tape. Solid green / ink / cream carry the
contrast; gradients are kept to a barely-there page vignette and soft light on
cutouts.

## v3: Magritte scale jumps

Deadpan, not wacky: ordinary things at the wrong size, rendered calmly.

- **The room** (after *The Listening Room*). As the `&` grows, hairline perspective
  draws in from the screen corners and the page turns out to be a room. The back
  wall is sized to the `&` at its centre-stage scale ×1.04, so it fits the way the
  apple fits Magritte's room: barely.
- **The man in the bowler hat**, seen from behind. He stands on the "h" of *things*;
  the word changes under him and he doesn't fall. He drifts down (x and y on
  different eases, so the path curves) and ends at the foot of the `&`.
- **The label** on the floor: *Ceci n'est pas une esperluette.* / GREEN, LIFE SIZE.
  (*Esperluette* is French for ampersand.)
- **The giant hand**: on wide screens the manicule is sized from the `&`'s position
  so it reaches in from past the left edge, cuff cropped by the frame.
- **The cloud comes indoors**, ×1.8, into the notch between the `&`'s loop and curl.
  Its scrap of sky is left hanging on the wall like an empty painting.
- **A second man** beside the vessel, for scale.
- **The dive walks through the room.** Once the zoom passes centre-stage scale,
  `roomG` and `peopleG` get the same camera transform as the glyph (see
  `applyAmp`), and the stage scales ×1.9, so everything rushes past the lens.

Timeline is now 0–106: the room draws 41–58, the man lands at 58, a hold until 68,
then the dive.

## The four figures are the four praxis words, in process order

| | figure | motion | character |
|---|---|---|---|
| I. Provocation | manicule ☞ (printer's pointing hand) | wind-up, jab, recoil — and it *causes* the `&`'s reaction | percussive |
| II. Materializing | stipple haze → solid amphora | 150 marks fly to pre-computed spots inside the vessel, then it's clay | converging, `expo.out` |
| III. Playing | Calder mobile, hung from the top edge | one number `t` drives two nested pendulums and three shapes turning edge-on | oscillating, decays |
| IV. Publishing | rubber stamp + sheets | lift, slam (`power4.in`), squash, lift off; prints `&c.`; copies fan out | heavy, then generous |

Ambient: a cloud leaves its scrap of sky; dust drifts. Neither is captioned.

`&c.` is the old printed abbreviation of *et cetera* — "and the rest", i.e.
"and things". It is the stamp's impression on purpose.

## Why the & is a path, not text

v1 scaled a text glyph with CSS transforms, and the browser scaled a bitmap, which
went soft. v2 draws the `&` as EB Garamond Italic's own outline (SIL OFL), embedded
as static path data in font units. Tested: SVG `<text>` gets clipped and then
dropped past ~20× zoom in Chrome, while the path renders cleanly at 140×+.

- `AMP.F` (685, −482) is the thickest point of the stroke (found with a distance
  transform); the final zoom aims there, so the screen ends up *inside* the green.
- `M.lzMax` is computed per viewport so the stroke's half-width covers the
  screen corner to corner. The `#flood` div fades in only as a safety net.
- The typeset `&` stays in the `<h1>` (transparent) for layout; a zero-height
  probe gives its baseline and the path is laid exactly over it.
- To swap the typeface: extract the new glyph (e.g. opentype.js on the font's
  .woff), replace `AMP.d`, recompute `G`, `F`, `R`, `H`, `W`.

## Things that will bite if you edit this

- All `A` (camera) tweens are `fromTo` with `immediateRender: false`. A plain
  `.to` on the proxy re-records its start on refresh and compounds.
- The manicule is placed by script from the measured `&`, not by CSS. Wide
  screens point it straight across; under 900px it's rotated −38° and comes from
  below-left.
- Scroll positions are absolute units on 0–100. The poke lands at `hit = 29.2`;
  the flood, ripples, jolt and knock-off all key off it.

## Copy (drafts — for hand-tightening)

- Hero sub: *A design studio, -ish.*
- Cue: *Scroll for more things*
- Close: *You bring the X, Y and Z. / We'll bring the &things.*
- Tombstones: *Ink, paper, one finger* · *Stipple, eventually clay* ·
  *Card, wire, a draught* · *Rubber, ink, edition of many*
- Tail: "Not for: ~~gambling~~, ~~exclusivity~~, and stuff like that."
- Email `hello@andthings.studio` is a placeholder.
