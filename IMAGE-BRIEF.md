# Image commissioning brief — Thames Evidence Programme

**Version 1 · 15 August 2026**
For generating additional artwork for <https://thamesevidence.org.uk>.

This brief exists so that every new image lands on the site looking like it belongs to the same
programme as the seven already there. Work through it in priority order — Tier 1 gives the
biggest visible gain.

---

## 1. Non-negotiables

**Honesty first.** This is an evidence site read by regulators, councils and MPs. Artwork
signposts a subject; it never stands in as evidence. So:

- **No invented data.** Charts, dials, numbers and map pins inside an illustration must be
  abstract and unreadable — soft shapes, not legible figures. An illustrated chart that looks
  like a real EA dataset is a liability.
- **No real-world text.** No agency names, no logos, no signage, no book spines with titles.
  (The existing "public records" image has spines reading *EPA* and *USGS* — US agencies. That
  is exactly the failure mode to avoid; it is captioned around for now.)
- **No identifiable real people** and no real, recognisable buildings presented as a specific
  named place unless it genuinely is that place.
- **British, not American.** Reference points are the tidal Thames in west London — brick and
  stucco riverside villas, plane trees, willows, narrowboats and skiffs, a grey heron, lock
  gates and weirs. Not a US river, not a Mediterranean one.

Every illustrated page on the site carries a footer line stating the artwork is illustrative and
carries no evidential weight. Keep it true.

---

## 2. House style

The seven existing images share a look. Match it.

| Element | Specification |
|---|---|
| Palette | Deep navy `#0b2545` → `#13315c`, teal `#0f6f7a`, river blue `#2a6f97`, pale sky `#cfe0ea`, off-white `#f5f8fa` |
| Mood | Calm, documentary, early-morning or overcast light. Serious and civic — not dramatic, not apocalyptic, not whimsical |
| Technique | Soft painterly digital illustration, gentle realism. Clean edges, restrained texture |
| Composition | Wide landscape. River recedes into mist; a low horizon; foreground bank detail |
| Overlays | Translucent white/pale panels, rounded corners, soft drop shadows, floating above the scene — abstract UI shapes only |
| People | Small in frame, absorbed in work, faces indistinct. Mixed ages and backgrounds |
| Do not use | Harsh contrast, neon, lens flare, heavy vignettes, cartoon outlines, visible brand marks, dramatic sunsets |

**Style suffix — paste at the end of every prompt:**

> Soft painterly digital illustration, calm documentary mood, overcast early-morning light,
> muted palette of deep navy, teal and pale blue with off-white accents, wide landscape
> composition, low horizon, misty distance, translucent rounded UI panels floating over the
> scene with abstract unreadable content, no text, no letters, no numbers, no logos, no
> signage, English riverside setting.

---

## 3. Technical specification

| Item | Value |
|---|---|
| Generate at | **1536 × 1024** (landscape) — the largest landscape ChatGPT produces |
| Final crop | **16:9** — I crop centrally to 1672 × 941 or equivalent |
| Safe area | Keep the subject inside the middle 80% vertically; the top and bottom ~10% get cropped |
| Left third | Keep **visually quiet** — headline text sits over the left third of every hero |
| Format to send | PNG straight from the generator. Do not resize or compress — I generate the WebP/JPEG derivatives |
| Deliver to | `site/images/originals/` |

**Filenames matter for SEO.** Name each file exactly as the "Filename" row in the slot specs
below: lowercase, hyphens, no spaces, no `ChatGPT Image ...`. I derive the web versions and the
alt text from these.

I then produce, for each source image: `-1600.webp`, `-1600.jpg`, `-800.webp`, `-800.jpg`
(~120 KB each) into `images/web/`, and wire them into the page.

---

## 4. Tier 1 — evidence page heroes *(highest value)*

Eight evidence pages currently share five general images plus three drawn placeholders. Giving
each page its own subject image is the single biggest improvement available.

---

### 1.1 Water quality
**Filename:** `river-thames-water-quality-sampling-teddington-weir.png`
**Replaces:** the generic data-holders image on `/docs/water-quality.html`

> A scientist in a dark waterproof jacket and blue gloves crouching on the grassy bank of a wide
> English river at dawn, lowering a clear sampling bottle into the water. Beside them a small
> open equipment case. A weir with white water stretches across the river in the middle distance,
> willows and a brick riverside villa on the far bank. Translucent rounded panels float in the
> upper right showing abstract soft line graphs and dials with no readable values. [style suffix]

---

### 1.2 Sewage & storm overflows
**Filename:** `river-thames-mogden-storm-tanks-outfall.png`
**Replaces:** the current treatment-works image on `/docs/sewage-mogden.html`

> A large municipal sewage treatment works on the bank of a wide English river seen from across
> the water on an overcast morning — circular settlement tanks, low industrial buildings, pipe
> galleries and rectangular concrete storm tanks. A discharge channel meets the tidal river in
> the foreground, the water slightly turbid where the two mix. Restrained and factual, not
> apocalyptic. Translucent rounded panels upper right with abstract bar shapes, no readable
> values. [style suffix]

---

### 1.3 WFD status & compliance
**Filename:** `river-thames-wfd-classification-assessment.png`

> A wide English river at first light with an ecologist standing at the water's edge holding a
> clipboard, looking out across the reach. Around the scene, translucent rounded panels float in
> a loose column showing abstract classification bands as soft coloured blocks stacked from poor
> to good — colour blocks only, no words, no scale labels. Reed beds and a distant stone bridge.
> [style suffix]

---

### 1.4 Fish & aquatic ecology
**Filename:** `river-thames-eel-seine-netting-richmond.png`
**Replaces:** the drawn placeholder plate on `/docs/fish.html`

> Two people in waders drawing a seine net through the shallows of a wide tidal English river at
> low water, a shallow sorting tray of river water on the exposed gravel beside them holding a
> few small silver fish and one long dark eel. Exposed muddy foreshore, moored skiffs, a stone
> bridge in the misty distance. Quiet, careful, scientific. [style suffix]

---

### 1.5 Birds & biodiversity
**Filename:** `river-thames-waterbirds-ham-foreshore.png`
**Replaces:** the drawn placeholder plate on `/docs/birds-biodiversity.html`

> A grey heron standing motionless on an exposed muddy foreshore of a wide tidal English river at
> low tide, with a scatter of ducks and gulls further out on the mud and a cormorant on a mooring
> post. In the foreground, out of focus, a birdwatcher's telescope on a tripod seen from behind.
> Willows and riverside meadow on the near bank, mist over the water. [style suffix]

---

### 1.6 Bathing water
**Filename:** `river-thames-open-water-swimmers-ham-kingston.png`
**Replaces:** the drawn placeholder plate on `/docs/bathing.html`

> Three open-water swimmers in bright coloured swim caps and one towing an orange safety buoy,
> swimming in a calm wide English river on a bright overcast summer morning, seen from the bank
> at water level. A slipway and a couple of towels on the grass in the foreground; moored boats
> and riverside trees beyond. Cheerful but calm — ordinary people swimming, not a race.
> [style suffix]

---

### 1.7 Accountability & context
**Filename:** `river-thames-regulatory-accountability-review.png`

> A formal meeting room with tall windows looking out over a wide English river, five people in
> business dress seated around a pale table reviewing bound documents and printed charts. Seen
> from the side, faces indistinct, natural overcast light. Sober and institutional. Translucent
> rounded panels float near the window with abstract soft chart shapes, no readable values.
> [style suffix]

---

### 1.8 Cross-correlations
**Filename:** `river-thames-data-correlations-analysis.png`

> A wide English river at dusk seen from a high bank, with several translucent rounded panels
> floating across the sky overlapping one another, each carrying a different abstract soft data
> shape — a line trace, a scatter of dots, a band of colour — connected by thin dotted lines into
> a loose network. No readable values or labels anywhere. Contemplative and analytical.
> [style suffix]

---

## 5. Tier 2 — landing page

### 2.1 Primary hero banner
**Filename:** `river-thames-teddington-lock-dawn-banner.png`
**Aspect:** generate 1536 × 1024, but **compose for a 2.4:1 centre crop** — everything essential
in the middle band. This becomes the main banner.

> Teddington Lock and weir on the River Thames at dawn seen from the Ham bank looking upstream —
> the long weir with white water, the lock island with its footbridge, willows and plane trees,
> mist lying on the water, a grey heron on a post in the near foreground. Wide cinematic
> landscape, very calm, cool blue-grey palette warming slightly at the horizon. Left third kept
> visually quiet and uncluttered. No floating panels on this one. [style suffix]

### 2.2 Mid-page reach banner
**Filename:** `river-thames-teddington-to-richmond-reach.png`

> A high, wide view along a curving English river valley on an overcast morning, the water
> running from the foreground into the misty distance, with wooded banks, riverside meadows,
> two stone bridges and a lock visible along its length. A soft translucent ribbon traces the
> river's course with a few plain circular markers along it — no text, no labels. Map-like but
> painterly. [style suffix]

---

## 6. Tier 3 — place portraits *(strong for local engagement and search)*

One image each, same style, no floating panels — these should read as places, not diagrams.
Local recognition is what makes residents share a page.

| # | Filename | Prompt subject |
|---|---|---|
| 3.1 | `river-thames-teddington-weir-tidal-limit.png` | The weir itself close-to, white water over the sill, the tidal limit marker post, willows behind |
| 3.2 | `river-thames-richmond-lock-footbridge.png` | An ornate Victorian iron footbridge over a tidal river with sluice gates raised, seen from downstream at low tide |
| 3.3 | `river-thames-ham-lands-riverside-meadow.png` | Rough grassland and scrub meadow beside a wide river, hawthorn and willow, a worn footpath, wildflowers, low morning mist |
| 3.4 | `river-thames-kingston-riverside-bathing-spot.png` | A grassy riverside park with a slipway and steps into a wide calm river, a few people on the bank, moored boats, town rooftops beyond |
| 3.5 | `river-thames-petersham-meadows-riverbank.png` | Water meadows with grazing cattle behind a fence beside a wide river, mature trees, a wooded hill rising beyond |

Add the style suffix to each, plus: *"no floating UI panels, no text, no signage."*

---

## 7. Priority order

1. **Tier 1.4, 1.5, 1.6** — fish, birds, bathing. These three currently use drawn placeholder
   plates; real illustrations replace them directly.
2. **Tier 2.1** — the main hero banner. Most-seen image on the site.
3. **Tier 1.1, 1.2** — water quality and sewage, the two heaviest-traffic evidence pages.
4. **Tier 3** — place portraits, for local engagement.
5. **Tier 1.3, 1.7, 1.8 and Tier 2.2** — the remainder.

---

## 8. What to send back

Drop the PNGs into `site/images/originals/` using the exact filenames above, and tell me which
slots are filled. I will:

1. Generate the WebP/JPEG derivatives at 1600 px and 800 px.
2. Wire each into its hero and card slot, with descriptive alt text.
3. Retire the drawn placeholder plates that have been replaced.
4. Update `sitemap.xml` and commit.

If a generated image comes back with stray text, a US reference, or a readable chart, say so and
regenerate rather than shipping it — on this site that detail is the difference between credible
and not.
