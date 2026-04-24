# Benchmark Project Family

Use this reference when building a new travel website from 0 to 1 and you need to make sure the result belongs to the same visual family as the existing shipped projects.

## Benchmark sites

- Xishuangbanna route guide: `https://dark-luxury-travel-itinerary.vercel.app`
- Jingshan route guide: `https://wuhan-jingshan-travel-guide.vercel.app`
- Jingshan memoir: `https://youji.travel-itinerary-jingshan.online`

## Benchmark source files

- [`/Users/yusijua/Documents/travel/Dark Luxury Travel Itinerary/src/App.tsx`](/Users/yusijua/Documents/travel/Dark Luxury Travel Itinerary/src/App.tsx)
- [`/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Hero.tsx`](/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Hero.tsx)
- [`/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Itinerary.tsx`](/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Itinerary.tsx)
- [`/Users/yusijua/Documents/travel/京山四天三夜游记/src/App.tsx`](/Users/yusijua/Documents/travel/京山四天三夜游记/src/App.tsx)

## What these projects have in common

### 1. Photography is structural, not decorative

All three projects use photography as part of the page architecture.

- the Hero is image-led
- the next screen inherits that same atmosphere
- the blurred background is not a separate random texture
- images are integrated into the narrative rhythm
- the assets read as real photography, not vector illustrations or generic placeholder shells
- support images feel like quiet magazine spreads, not report attachments or wiki proof shots

If a cold-start site has no meaningful images, it is not in-family yet.

### 2. The Hero is built with two coordinated layers

The correct shared pattern is:

1. fixed blurred full-page background using the cover image
2. clear Hero cover using the same image
3. bottom mask fade on the clear Hero cover
4. transparent next section over the same world

This is why those pages feel continuous rather than split into slabs.

Non-negotiable reading:

- the transition is not a separate strip, divider, or gradient band
- the next screen should feel like the Hero atmosphere continuing downward
- there must be breathing room between the Hero stack and the next section
- if the first content block feels pasted directly under the cover, it is out of family
- the clear Hero image should remain readable; the blur belongs to the shared background layer only
- the second screen should not begin as a boxed slab or flat pure-color panel

### 3. Typography is centered by optical logic

Shared traits:

- travel mark on a centered axis
- title stack inside one width shell
- subtitle aligned to the same visual center
- visible text shadow over photography
- no weak hairline typography on mobile
- mobile titles are shortened or resized before they are allowed to break awkwardly
- overline travel marks keep their decorative side lines unless a benchmark explicitly proves a cleaner alternative
- raw system labels never appear in the visible design language

### 4. Content is structured, not dumped

The route guides and memoir use different content structures, but both avoid text-dump behavior.

Route-guide pages usually include:

- Hero
- itinerary overview
- daily sections
- packing
- tips / cautions
- transport / lodging
- food / specialties
- budget

Memoir pages usually include:

- Hero
- day sections
- story beats
- one image per beat when possible

What they do **not** do:

- they do not open with system labels like `editorial plan`, `validation`, or `route topology`
- they do not surface research scaffolding as front-end modules
- they do not read like internal demo pages
- they do not show route-status chips like `THERE-AND-BACK (LIGHT)` or similar planning jargon
- they do not wrap every support section in the same generic dark rectangle

### 5. Tags are concrete and icon-led

Only two reliable tag types are allowed:

1. place / destination
2. food

Tags should:

- use an icon
- align cleanly with text
- keep small radii
- avoid emotional or abstract filler words

### 6. Motion is restrained but present across the whole page

Shared motion language:

- Hero copy drift or fade
- slow bounce scroll cue
- section fade-up
- timeline / beat reveal
- subtle linear hover behavior

The page should not have one animated block surrounded by static sections.

Hover rule:

- hover should feel like a quiet lift, fill, or soft reveal
- it should never feel like a dashboard interaction or a flashy component library demo

### 6.5. Surfaces stay open and editorial

Shared traits:

- content is organized by spacing, type, and image rhythm before borders are introduced
- when borders appear, they are hairline and low-contrast
- timeline systems do not sit inside heavy framed boxes
- budget, food, prep, and route notes do not all reuse the same card shell
- support information is often merged into calmer editorial spreads instead of being split into many equal-weight modules

If a page starts to look like a generic dark template with repeated boxed modules, it has drifted out of family.

### 7. Audio is editorial, not widget-like

When music is present:

- the control is fixed and small
- the UI follows real audio state
- autoplay may be attempted only when explicitly desired
- repeated toggle must keep working
- a vinyl treatment only counts if the tonearm and disc state truly follow playback
- the chosen track has a provenance record, and reused audio requires explicit approval

## Cold-start pass criteria

A new route-guide site passes only if it reaches all of these:

1. real Hero cover image exists
2. blurred global background reuses the same cover or a tightly related one
3. second screen transitions naturally from the Hero
4. the page contains real, high-resolution itinerary imagery, not only text blocks
5. images are stored in the project before final delivery
6. content structure resembles the benchmark family
7. mobile typography is readable and visually centered
8. tags are concrete and correct
9. visible copy sounds like a warm travel guide, not a planning report
10. if music fits the page family, a real music recommendation / embed decision exists
11. if music is present, the audio provenance is real and not a silently renamed reuse from an older project
12. if a timeline is present, time, node, and text alignment feel benchmark-grade
13. if a route-loop is present, start / end logic and node interactions are clear and graceful
14. if a vinyl player is present, it behaves like a real bound control rather than a decorative toggle
15. the page would plausibly be mistaken for the shipped benchmark family by a human reviewer
16. the mobile Hero still feels like a composed cover, not a broken stack of oversized characters
17. the first visible support sections still feel airy and editorial, not like dashboard cards under a poster
18. the player still looks like the same benchmark-family black-vinyl object, not a newly invented music widget

If the site only proves “I can deploy a React page”, it fails this benchmark.
If it uses low-resolution placeholders, flat SVG fallback art, clumsy route graphics, or fake media controls, it fails this benchmark too.
If it still shows planning jargon, boxy generic surfaces, or an awkward mobile Hero, it fails this benchmark too.
If it solves structure by multiplying modules instead of calming the layout, it fails this benchmark too.

## Asset minimum for route-guide pages

Unless the user explicitly wants a minimal prototype, a route-guide page should usually ship with:

1. one Hero cover image
2. one to three supporting atmosphere images
3. at least one image per day, or one per tightly grouped pair of beats

Priority:

1. user-provided image
2. Pixabay
3. Pinterest for discovery and scene finding, then trace to a shippable asset source
4. generated replacement for only the missing scene

For a passing validation, do not settle on:

1. low-resolution thumbnails stretched to fill
2. flat SVG scenes standing in for photography
3. muddy screenshots or watermarked scraps

## Asset storage rule

Do not leave the final implementation dependent on arbitrary remote placeholders if you can reasonably store the approved media inside the project.

Preferred behavior:

1. choose the image
2. download or copy it into `public/` or another committed asset location
3. reference the local path in the app
4. verify it still looks correct both clear and blurred

## Workflow implication

For a real 0-to-1 route-guide build, the order should be:

1. structure content
2. define shot list
3. source images
4. store images locally
5. build Hero and transition
6. build itinerary sections
7. tune motion and music
8. run mobile QA

Do not postpone the image system until after deployment.
If the best available route-loop, timeline, or player still looks crude, remove that weak module and keep the page cleaner.
