---
name: dark-luxury-itinerary-skill
description: Build or refine travel guides, 路书设计网页, editorial landing pages, and lifestyle microsites in a restrained dark luxury / Kinfolk-inspired aesthetic using React + Tailwind CSS. Use when the user asks for 高级、惊艳、克制、有呼吸感的暗黑杂志风页面，尤其是要把原始旅行攻略、行程路书、游记文本转成可交互网页、需要 Hero 与下一屏无缝过渡、优雅时间轴、地点/食物标签、低饱和 earth/forest 配色、内嵌 BGM、Pixabay 素材 sourcing / generation，或要把这套体系沉淀成 Cursor 规则 / SOP / skill 的场景。
---

# Dark Luxury Itinerary Skill

## Use this skill for

- travel guides
- itinerary / route-guide microsites
- first-person travel memoir pages
- editorial landing pages with photography-led Hero sections
- mobile-first lifestyle story sites
- projects that need restrained BGM, Pixabay sourcing, or reusable route-guide SOPs

The desired feeling is: restrained, cinematic, breathable, precise, and quietly expensive.

## Primary promise

This skill should help Codex turn raw travel text into a polished, mobile-first editorial webpage while preserving the user’s tone and avoiding generic app-like UI.

## Non-negotiables

1. Do not overwrite a different destination site unless the user explicitly asks to replace it.
2. Treat Hero and the next section as one composition, not two disconnected slabs.
3. Blur belongs to the background layer, not the visible Hero image.
4. Fix structure and typography before adding more effects.
5. Mobile is a first-class review surface, not an afterthought.
6. Tags are only valid when they are concrete `place / destination` or `food`.
7. Day imagery must match the itinerary or memoir literally enough that the user will not question it.
8. Music UI must follow the real media element state; do not fake playback visually.
9. A cold-start route-guide site is not a pass if it ships as a text-only page with little or no imagery.
10. Route-guide images should be sourced first and then stored inside the project; do not leave the page dependent on scattered remote placeholders.
11. Pixabay is the default free-first asset source; Pinterest may be used for scene discovery or visual direction, but licensing and source clarity still matter before shipping.
12. Do not let image sourcing stall on a single provider; use a defined fallback chain and keep the final assets stored locally.
13. Do not ship bloated CJK font payloads by accident; font choice is part of performance design.

## Benchmark family

Cold-start outputs must feel like they belong to the same project family as these shipped benchmarks, not like a generic dark text landing page.

- Xishuangbanna route guide: `https://dark-luxury-travel-itinerary.vercel.app`
- Jingshan route guide: `https://wuhan-jingshan-travel-guide.vercel.app`
- Jingshan memoir: `https://youji.travel-itinerary-jingshan.online`

If you have your own benchmark-family implementations in your workspace, inspect them as supporting references. If not, rely on the benchmark sites plus the bundled references in this skill.

## Default workflow

1. Protect project boundaries.
2. Determine whether this is a new destination, a refinement of an existing site, or a restore / rollback request.
3. Normalize the raw brief into structured content before styling.
4. Compare the target page against the benchmark family and pick the closest structural base.
5. Build the image and audio shot list before polishing visuals.
6. Source and store the required images locally before calling the page implementation complete.
7. Fix the page shell and Hero transition first.
8. Fix Hero composition, type hierarchy, and optical centering.
9. Build the day / story structure and timeline geometry.
10. Apply one coherent motion language across the full page.
11. Add BGM only after layout and interaction structure are stable.
12. Run a mobile-first QA pass.
13. Sync metadata, project naming, and deployment aliases.
14. If the user asks to preserve or recover an earlier version, restore the correct deployment first and then sync local code to it.

## Cold-start execution template

Use this when validating the skill in a brand-new empty directory and you need execution pressure, not just aesthetic guidance.

### Hard rules

1. Do not manually stop at `initializing`, `scaffold in progress`, or starter-template output.
2. Do not treat `package.json` plus placeholder files as meaningful progress.
3. Do not call the cold-start test complete until the project has:
   - real page code
   - real local image assets
   - successful build output
   - deployed public URL or a clearly documented deployment blocker

### Preferred implementation path

1. Create the empty target directory.
2. Immediately create `AGENT_STATUS.md` with:
   - status
   - current step
   - what has actually been executed
   - next concrete action
3. Scaffold a fresh React + Vite + TypeScript app from scratch.
4. Replace the starter app immediately after scaffold.
5. Define the route-guide structure before visual polish:
   - `hero`
   - `overview`
   - `packing / prep`
   - `days[]`
   - `transport / lodging`
   - `cautions`
   - `foods / specialties`
   - `budget`
6. Source at least:
   - 1 Hero cover
   - 2 supporting atmosphere or itinerary images
   - 1 image per day or per tightly grouped day-pair
7. Store all chosen assets locally under the new project.
8. Implement the page shell and Hero transition.
9. Implement the itinerary and supporting sections.
10. Run `npm run build`.
11. Deploy to a new public Vercel URL if deployment is in scope.

### Minimum visible filesystem state before claiming momentum

These files or their equivalents should exist:

- `AGENT_STATUS.md`
- `package.json`
- `src/App.tsx`
- `src/main.tsx`
- `src/index.css`
- `public/images/*`

### Automatic fail states for cold-start validation

If the output stops in any of these conditions, the test has not passed:

- starter Vite or React content is still visible
- `App.tsx` only says `Scaffold in progress` or similar
- there are no meaningful local images
- the page is mostly text on a plain dark background
- there is no Hero-to-second-screen background continuity
- the project never reaches a successful build

## Content normalization rules

### If the source is only an intent

Use this mode when the user does not already have a full route guide and instead asks for something like:

- “从哪里去哪里”
- “几天几夜”
- “想要松弛 / 亲子 / 预算友好 / 美食导向”
- “帮我直接规划一份完整路书”

In this mode, the skill must first become a route-planning system, then a webpage system.

Always try to determine:

- origin
- destination
- trip length
- approximate travel dates or season
- travel party
- trip style
- budget level
- transport preference
- whether the user wants a memoir-like tone or a practical route-guide tone

If some inputs are missing, make reasonable assumptions and label them clearly in the generated plan.

Before writing the actual route, the planner should explicitly reason through:

- multiple public research angles, not one generic search phrase
- weather-sensitive outdoor / indoor swaps
- whether each place is real, reachable, and worth the detour
- sequence by distance, transit burden, and opening-hour logic
- a short "why it is worth going" rationale for major stops

The minimum structured output should include:

1. itinerary overview
2. daily plan with time, place, and food
3. packing / pre-trip preparation
4. in-trip notes and cautions
5. transport and lodging guidance
6. recommended food and local specialties to bring back
7. overall budget

### If the source is a route guide

Extract and normalize:

- Hero title
- Hero subtitle or duration
- `days[]`
- timeline events with time, title, description, tags
- optional `foods[]`, `tips[]`, `packing[]`, `budget[]`

Rules:

- shorten only where needed for rhythm and hierarchy
- preserve concrete travel value
- keep desktop day titles to one line whenever reasonably possible
- if a title wraps, shorten the wording before shrinking the type too far

### If the source is a first-person memoir

Restore the story in the user’s voice.

Rules:

- keep first-person perspective
- do not insert meta phrasing such as “from Notion”, “from DOCX”, “restored from”
- lightly structure the material by day, time, or emotional beat
- compress gently, but do not discard the memorable or quotable parts
- the prose should sound like the original author, not like an AI summary
- the safest default is one text beat paired with one image

## Research rules for 0-to-1 planning

When the user only gives a travel intent, research is part of the job.

Use this source order:

1. official and primary sources
   - transport operators
   - official scenic-area or venue information
   - weather and seasonal information
   - official booking / ticket / map information when relevant
2. current public web results for practical travel synthesis
3. public UGC for heuristics, atmosphere, and edge-case tips

Use public Xiaohongshu notes only as a supplemental signal source for:

- recent crowd or queue patterns
- photogenic spots
- local food heuristics
- practical gotchas

Do not treat UGC as authoritative for:

- opening hours
- ticket prices
- regulations
- transportation rules

If Xiaohongshu is part of the research mix:

- prefer publicly reachable pages or search-engine-discovered note pages
- summarize patterns instead of overfitting to one note
- cross-check practical claims against more stable sources
- avoid assuming an official note-search API exists unless you have verified one

For stronger route quality, also read:

- `references/intent-to-itinerary-planning.md`
  This file defines multi-angle UGC search, weather-aware route swaps,
  place validation, sequencing logic, and "why worth going" recommendation framing.
  It also defines the default query pack, confidence ladder, mainland-China map stack,
  and walk / transit thresholds that should be used unless the trip clearly needs an override.

## Core visual system

This skill does not define success as “any dark page with text”. It defines success as recreating the mature visual language already established in the benchmark family.

### Page shell

Use a two-layer background system:

1. Layer A: fixed blurred background for the whole page
2. Layer B: clear Hero image inside the Hero section

Layer A should:

- use the same cover image or a closely related image
- be fixed behind the whole page
- use `object-cover`
- blur and darken the image
- carry one vertical gradient only

Layer B should:

- stay clear and readable
- fade downward using `mask-image`
- preserve the beauty of the cover image
- use only minimal dark overlays

If the transition looks wrong, fix the layer structure before changing opacities.

### Cold-start parity gate

A new route-guide site should normally include all of the following before it can be considered a successful cold-start output:

1. a full-screen photographic Hero cover
2. the same cover reused as the blurred global background
3. a seamless Hero-to-second-screen transition with no visible seam
4. actual stored image assets for the itinerary, not just text sections
5. a structured itinerary layout that feels like the benchmark family
6. tags with concrete place / food semantics and icons
7. motion and mobile spacing that feel intentional, not default
8. route-guide section order that reads cleanly on mobile:
   - overview
   - packing / prep
   - daily route
   - transport / lodging
   - cautions
   - food / specialties
   - budget
9. visible food / specialties content when the trip clearly has a food dimension
10. if the Hero uses an overline travel mark, it should be editorially framed rather than floating as a naked label

If these are missing, the result is an incomplete scaffold, not a passed cold-start website.

### Typography

- display titles: serif
- body copy: sans-serif
- supporting labels may use serif or a refined display accent font
- build hierarchy through size, weight, spacing, and placement
- use centered `·` as the default separator in titles
- keep major Hero copy readable on busy images with real shadow
- supporting labels like `JINGSHAN`, `YUNNAN TRAVEL`, or `四日三夜 · Staycation` must feel intentional, not hairline decoration
- prefer system Chinese serif / sans stacks unless a custom webfont is truly necessary
- if using CJK webfonts, import the fewest weights possible and check build output immediately
- avoid full-package multi-weight CJK font imports as the default path for Vite route-guide projects

### Color

- base background: deep green-black or deep black-green
- main titles: `text-white/90` to `text-white/96`
- body copy: `text-white/40` to `text-white/58`
- accents: low-saturation earth / forest tones only
- separators: extremely light, thin, and rare

### Form language

- prefer square or small-radius surfaces
- avoid oversized radii
- avoid thick borders, bulky cards, and component-library chrome

## Hero system

### Layout

- Hero copy must be visually centered, not merely mathematically centered
- the scroll hint must be absolute so it never pushes the title stack
- on mobile, the travel mark, main title, and subtitle should sit inside one shared width shell
- if the Hero feels low on mobile, raise the entire copy cluster before tightening line-height

### Overline travel mark

If the Hero includes an overline label such as `YUNNAN TRAVEL`,
`WESTERN SICHUAN ROUTE GUIDE`, or `四日三夜 · Staycation`:

- default to a centered row with the text flanked by thin decorative lines
- keep the lines subtle, long enough to read as intentional framing, and optically centered with the label
- the label should feel like one editorial component, not a stray floating caption
- do not omit the framing lines unless the chosen benchmark explicitly proves a cleaner alternative

### Title composition

If the title is two destinations plus a separator:

- use a 3-column grid
- left word right-aligned
- centered dot
- right word left-aligned
- if the left phrase is shorter, widen its tracking rather than shifting the dot

If the title is a short Chinese phrase:

- split the characters into separate inline blocks when needed
- adjust spacing through character gaps, not fake centering paddings

### Readability

- default to white title text on bright or busy cover images
- use visible shadow on all Hero text, not just the main title
- if the cover is bright, increase shadow strength before darkening the whole image

### Transition to the next section

The correct default pattern is:

- one fixed blurred cover behind the whole page
- one clear Hero cover inside the Hero section
- a bottom mask fade on the clear Hero image
- the next section rendered on a transparent canvas over the same background

Do not default to:

- a separate opaque slab at the top of `main`
- multiple stacked gradient bands trying to hide a seam
- a third background layer
- aggressive negative overlap between Hero and Day 1

## Motion rules

- keep motion sparse and coherent
- section fade-up is the safest default
- the scroll indicator line can use a slow vertical bounce
- timeline or story beats may reveal progressively on scroll
- hover should feel restrained and editorial, not flashy
- if animation stutters, simplify it before tuning durations

Do not:

- animate every section with a different visual language
- rely on blur-reveal gimmicks
- stack too many overlapping motion effects in one area

## Timeline and story systems

### Route-guide timeline

For schedule-heavy pages:

1. Use a 3-column desktop structure:
   - time
   - node
   - content
2. On mobile, stack gracefully and preserve readability.
3. Time text must be smaller and lighter than the event heading.
4. The vertical line must live between nodes, not pierce them.
5. Use an occluder disc behind the node so the line never visually cuts through it.
6. Default node state should feel hollow / restrained.
7. Hover state should fill or glow slightly, but remain elegant.

Do not:

- use thick black rings
- oversize the time text
- wrap the interaction in bulky card chrome
- let time, node, and heading drift off the same visual baseline

### Memoir beat structure

For first-person story pages:

- organize by day, then by beat
- a beat may be anchored by time, moment, or emotional label
- pair one beat with one image whenever possible
- avoid giant day-level master images if they create hierarchy conflicts or messy wrapping

## Section design

- section titles should be visibly stronger than body copy
- use giant low-opacity serif numerals only when they improve rhythm
- let all major sections rise in with the same motion language
- do not sprinkle decorative elements just to fill space
- if a page feels empty, first adjust spacing and typography instead of adding more objects
- for route-guide pages, default section order is:
  - itinerary overview
  - packing / pre-trip prep
  - daily itinerary
  - transport and lodging
  - cautions
  - food and specialties
  - budget
- if packing is present, place it before the daily route rather than burying it after the itinerary
- if the trip clearly includes eating, local snacks, or take-home recommendations, do not omit the food / specialties section

## Tags and inline details

Only two tag categories are valid:

1. `place / destination`
2. `food`

Rules:

- every tag needs a concrete icon
- align tags carefully with surrounding text baselines
- keep radii small and borders light
- do not use abstract emotion words as tags
- do not create filler tags that merely paraphrase the paragraph

## Image system

- start with user-provided images or explicit image direction
- when free sourcing is acceptable, prefer Pixabay first
- if Pixabay blocks, downgrades badly, or download links are unstable, move through an explicit fallback chain instead of stalling
- Pinterest is valid for scene discovery and composition reference; when using it, trace back to a shippable asset source or otherwise confirm the asset can be stored and used
- if sourcing fails, generate only the exact missing scene
- Hero images must survive both clear presentation and blurred-background reuse
- day images must match the literal scene or memory beat
- reject images that feel generic, oversaturated, muddy when blurred, or semantically wrong

For route-guide pages, the minimum visual contract is:

1. one Hero cover image
2. one blurred-background reuse of that same cover
3. at least one meaningful image per day, or one per two tightly related beats when the rhythm really supports it

Do not ship a route-guide page with no usable imagery merely because the text structure is finished.

### Asset sourcing fallback chain

When Pixabay does not produce a reliable shippable file, use this order:

1. retry Pixabay with a scene-based query and a different crop / resolution
2. open the asset page directly and save a stable local copy
3. use Pinterest only to sharpen scene language, not as the final ship source by itself
4. move to another cleared stock source such as Pexels
5. generate only the exact missing scene

Do not spend excessive time forcing one provider when a valid fallback exists and the scene requirements are already clear.

### Font payload control

For React + Vite travel microsites, treat font delivery as part of the design system.

Default rules:

1. use system Chinese font stacks first
2. add one custom Latin or display font only when it materially improves the page
3. if a CJK webfont is necessary, prefer a single weight or a subsetted self-hosted file
4. inspect `dist/assets` after build whenever custom fonts are added

Warning signs:

- dozens or hundreds of emitted `woff` / `woff2` files
- CSS ballooning because font packages inline too many unicode ranges
- total build output dominated by fonts instead of imagery and app code

If this happens, revert to a lighter font strategy before shipping.

## Music system

When music is part of the page:

1. Recommend 2 to 3 mood directions first.
2. Let the user choose a direction.
3. Source from Pixabay or accept a user-provided local file.
4. Integrate the chosen file into the project.
5. Verify playback against the real media element.

Player rules:

- keep the control fixed and visually quiet
- the user should be able to understand it without bulky `Play / Stop` text
- a small vinyl-disc control is a strong default for this project family
- clicking the disc should toggle playback
- if a tonearm is present, it must drop on play and lift on pause
- keep the player small enough that it does not dominate mobile viewports

Playback rules:

- if the user wants default playing, attempt autoplay but never trust it
- always preserve click-to-play fallback
- bind UI state to real `play`, `playing`, `pause`, `ended`, and `error` events
- if the intro is nearly silent, skipping ahead to the first audible section is allowed
- do not ship copyrighted music unless it is licensed or user-provided
- when building the reusable workflow, offer build-time music choice; do not default to an in-page local file picker unless explicitly requested

## Responsive rules

- mobile comes before desktop polish
- reduce title size before allowing awkward wrapping
- keep the Hero block optically centered on small screens
- verify the shared axis of travel mark, main title, and subtitle
- verify separator dots stay centered
- keep enough breathing room between Hero and the next section
- turn desktop side-by-side layouts into vertical stacks cleanly
- preserve line-height; do not cram the page into a dense mobile list
- confirm the fixed music control does not block key text on mobile

## Cold-start workflow standard

When the user asks for a brand-new route-guide website from 0 to 1, the workflow must be:

1. plan the itinerary structure
2. write the visual shot list
3. source images from Pixabay and other valid sources, with Pinterest allowed for visual discovery
4. save the chosen assets into the project
5. build the Hero and second-screen transition around those real assets
6. build the structured itinerary, tags, sections, and motion system
7. add audio only after the visual shell is already correct
8. verify mobile readability and project-family similarity before deployment

The workflow is not:

1. generate text
2. wrap it in dark cards
3. deploy it
4. promise that imagery can be added later

## Deployment and recovery hygiene

- a new destination usually means a new local project and a new Vercel project
- keep project name, page metadata, and public alias in sync
- if the user says an earlier version was better, inspect Vercel deployments and restore the correct one instead of approximating it from memory
- after restoring a deployment, sync local code to that restored state before continuing edits
- verify the final share URL is public and reachable

## Anti-patterns learned from this project

### Hero mistakes

Do not:

- blur the visible Hero image
- stack multiple transition strips to hide a seam
- add a separate dark strip and call it a transition
- let Hero and the first content block crash into each other
- “fix” centering by nudging one line independently from the rest of the stack

### Typography mistakes

Do not:

- leave Hero text too thin to read on photography
- forget shadow on bright covers
- allow key desktop day titles to wrap casually
- use supporting labels so small or thin that they feel accidental

### Timeline mistakes

Do not:

- let the line pierce the node
- use a permanently filled node if hollow-to-solid hover is intended
- surround the node with a heavy ring
- let hover states become noisy or cheap

### Content mistakes

Do not:

- add AI-ish prefatory writing that the user did not ask for
- replace first-person memories with generic summary prose
- assign arbitrary tags
- use semantically wrong images

### Music mistakes

Do not:

- let the UI claim music is playing when the media element is silent or blocked
- make the vinyl control oversized
- forget repeat toggle behavior after the first interaction
- hardcode a copyrighted commercial track without permission

### Process mistakes

Do not:

- create a parallel replacement skill when the user asked to refine this one
- ship after desktop-only review
- change project identity without syncing Vercel naming and metadata
- let Pixabay-only sourcing block delivery when a valid fallback source exists
- ignore build output after adding Chinese webfonts

## Debug checklist

When the page still feels off, inspect in this order:

1. Is the visible Hero image accidentally blurred?
2. Is there a visible seam caused by an extra background or opaque slab?
3. Is the Hero stack mis-centered because the three lines do not share one width shell?
4. Is the Hero too low on mobile?
5. Are tags semantically wrong or visually noisy?
6. Does the timeline line pierce the node?
7. Are day images mismatched to the text?
8. Is music UI detached from the real playback state?
9. Is the fixed player covering too much on mobile?

## References

Read only the reference you need:

- [benchmark-project-family.md](references/benchmark-project-family.md)
  Use for the concrete visual baseline extracted from the three shipped benchmark sites and for cold-start pass / fail gates.
- [implementation-recipes.md](references/implementation-recipes.md)
  Use for Tailwind / React patterns for Hero layout, timeline nodes, vinyl control, and image surfaces.
- [workflow-from-brief-to-site.md](references/workflow-from-brief-to-site.md)
  Use for the end-to-end production flow from raw text to deployed microsite.
- [image-and-audio-pipeline.md](references/image-and-audio-pipeline.md)
  Use for Pixabay-first sourcing, image shot selection, generation fallback, and BGM workflow.
- [intent-to-itinerary-planning.md](references/intent-to-itinerary-planning.md)
  Use when the user only provides travel intent and expects a full 0-to-1 route guide before webpage production.
- [editorial-writing-and-mood-mapping.md](references/editorial-writing-and-mood-mapping.md)
  Use for Chinese editorial microcopy constraints, content schema guidance, and mood-to-shot / mood-to-search-term mapping.
