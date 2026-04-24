---
name: dark-luxury-editorial-web
description: Build or refine travel guides, 路书设计网页, editorial landing pages, and lifestyle microsites in a restrained dark luxury / Kinfolk-inspired aesthetic using React + Tailwind CSS. Use when the user asks for 高级、惊艳、克制、有呼吸感的暗黑杂志风页面，尤其是要把原始旅行攻略、行程路书、游记文本转成可交互网页、需要 Hero 与下一屏无缝过渡、优雅时间轴、地点/食物标签、低饱和 earth/forest 配色、内嵌 BGM、Pixabay 素材 sourcing / generation，或要把这套体系沉淀成 Cursor 规则 / SOP / skill 的场景。
---

# Dark Luxury Editorial Web

## Use this skill for

- travel guides
- itinerary / route-guide microsites
- first-person travel memoir pages
- editorial landing pages with photography-led Hero sections
- mobile-first lifestyle story sites
- projects that need restrained BGM, Pixabay sourcing, or reusable route-guide SOPs
- route-guide systems that sometimes need elegant route guidance without losing editorial warmth

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
14. User-facing copy must sound like a caring human travel companion, not a system report, audit log, or planner console.
15. Research, source confidence, map checks, and weather reasoning are backstage scaffolding; they belong in planning artifacts, not as stiff front-end modules unless the user explicitly asks to see them.
16. Do not invent dashboard cards, KPI blocks, validation panels, or tool-looking sections that break the established benchmark family.
17. Existing benchmark-family visual rules are binding: Hero-to-second-screen transition, breathing room, restrained hover language, and editorial spacing must be preserved unless the user explicitly changes them.
18. If the trip includes multiple geographic clusters, self-drive routing, or obvious order tradeoffs, route logic may be surfaced, but it must still read as elegant editorial guidance rather than system jargon.
19. A 0-to-1 route guide must not finalize without map validation records for core stops and major hops.
20. Any route with meaningful outdoor exposure must not finalize without a weather adaptation record or an explicit seasonal fallback note.
21. Cold-start validation should end in a public Vercel URL or a clearly evidenced deployment blocker, not a local-only report.
22. Validation output should lead with the public URL and browser accessibility result, not only markdown artifacts.
23. Music suggestion and embed flow should be treated as a default part of the page family unless the user opts out.
24. Route sequencing reasons, weather swaps, and source rationale belong in agent conversation and planning artifacts by default; do not turn them into visible page modules unless the user explicitly asks.
25. Food and lodging recommendations must be backed by a layered source stack; do not let one Xiaohongshu note or one generic review page decide the final picks.
26. Cold-start music must have provenance and freshness: record source path / query / URL plus file hash, and never rename a prior project track and present it as newly sourced unless the user explicitly approved reuse.
27. A passing route-guide site must use real photographic imagery or approved photo-like bitmap assets; flat SVG illustrations, low-resolution placeholders, or muddy thumbnails do not count.
28. If the route-loop, timeline, or vinyl player cannot reach benchmark quality, simplify or omit that module instead of shipping a weak version.
29. Final visual pass is qualitative as well as structural: if a human would not mistake the result for the shipped benchmark family, the cold-start validation has not passed.
30. Mobile Hero composition must survive the smallest common viewport: no awkward forced line breaks, no title broken into isolated characters, and no hairline labels that disappear against the cover.
31. Visible route labels must be rewritten as human editorial language; raw labels like `THERE-AND-BACK`, `CLEAN LOOP`, `route topology`, `validation`, or `confidence` must never appear on the rendered page.
32. Avoid boxy dark-template chrome. If a section depends on thick borders, large framed rectangles, grid panels, or dashboard-like shells to look organized, simplify the section until it feels editorial again.
33. For cold-start visual validation, one failed benchmark symptom is enough to fail the run: broken mobile Hero, visible Hero seam, crude timeline, fake / oversized vinyl player, generic cards, system copy, or non-photographic assets.
34. Browser verification must include visual evidence, not only HTTP success: capture or provide desktop and mobile screenshots and compare them against the benchmark family before marking the run visually passed.
35. New cold-start builds should begin from the benchmark family’s proven layout patterns or source code references, not from a generic dark landing page that gets restyled later.
36. The music player must stay visually consistent with the shipped family: a compact vinyl-first control, not a new pill widget, labeled capsule, or alternate component language invented for one validation.
37. De-AI-UI is a structural rule, not a slogan: reduce repeated modules, repeated cards, and repeated panel shells until the page reads like one continuous editorial composition rather than a stack of feature blocks.
38. Semantic fit is only half the image bar. A factually correct photo that looks like a flat record shot, gray tourism proof, watermark-heavy archive capture, or lifeless placeholder still fails the family and must be replaced.

## Preferred external skills

These skills are preferred helpers, not hard prerequisites. If they are unavailable, keep the capability and move to official web or API fallback. Never skip map or weather work just because a skill is missing.

If the current environment does not already expose map or weather capability:

- first try installing a relevant helper through FineSkills / `skills`
- preferred discovery path:
  - `npx skills find amap maps weather`
- preferred install path:
  - `npx skills add <repo-or-registry> --skill <skill-name> -g -y`
- if installation fails because of registry mismatch, auth, or provider friction, record that in the research artifact and continue with the documented web fallback instead of blocking the whole route

- mainland-China map primary: `skills.volces.com@amap-maps`
- global map supplement: `tivojn/google-maps-api-skill@google-maps-api`
  - currently installed fallback
  - requires `GOOGLE_MAPS_API_KEY` for direct API calls
- weather primary: `skills.volces.com@weather-openmeteo`
- weather fallback: `chandima/agent-skills@weather`
  - currently installed fallback
  - no API key required

Provider strategy:

- mainland-China destinations
  - prefer `amap-maps`
  - if unavailable, use Amap web or another stable mainland map product plus official venue pages
- outside mainland China
  - prefer `google-maps-api` when an API key is configured
  - otherwise use Google Maps or the dominant local map product plus official venue pages
- weather
  - prefer a forecast-capable skill
  - otherwise use built-in weather tooling when available
  - otherwise use official meteorology or stable forecast sites and record the fallback explicitly

## Benchmark family

Cold-start outputs must feel like they belong to the same project family as these shipped benchmarks, not like a generic dark text landing page.

- Xishuangbanna route guide: `https://dark-luxury-travel-itinerary.vercel.app`
- Jingshan route guide: `https://wuhan-jingshan-travel-guide.vercel.app`
- Jingshan memoir: `https://youji.travel-itinerary-jingshan.online`

Use their local implementations as the most reliable code-level baseline:

- [`/Users/yusijua/Documents/travel/Dark Luxury Travel Itinerary/src/App.tsx`](/Users/yusijua/Documents/travel/Dark Luxury Travel Itinerary/src/App.tsx)
- [`/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Hero.tsx`](/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Hero.tsx)
- [`/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Itinerary.tsx`](/Users/yusijua/Documents/travel/武汉 京山 四日游攻略 2/src/components/Itinerary.tsx)
- [`/Users/yusijua/Documents/travel/京山四天三夜游记/src/App.tsx`](/Users/yusijua/Documents/travel/京山四天三夜游记/src/App.tsx)

## Default workflow

1. Protect project boundaries.
2. Determine whether this is a new destination, a refinement of an existing site, or a restore / rollback request.
3. Normalize the raw brief into structured content and assumptions before styling.
4. Resolve the planning template and backstage route logic.
5. Validate core places and major hops with map-capable tools or manual map fallback.
6. Adapt the route with forecast or seasonal weather logic before freezing the schedule.
7. Translate the planning logic into human-facing language before writing any visible copy.
8. Compare the target page against the benchmark family and pick the closest structural base.
9. Build the image and audio shot list before polishing visuals.
10. Source and store the required images locally before calling the page implementation complete.
11. Fix the page shell and Hero transition first.
12. Fix Hero composition, type hierarchy, optical centering, and the breathing room between the first two screens.
13. Build the day / story structure and only add a route-summary treatment if it can stay graceful and non-toolish.
14. Apply one coherent motion language across the full page, including linear hover behavior that matches the benchmark family.
15. Add BGM after layout is stable and make the recommendation / selection step explicit.
16. Run a mobile-first QA pass.
17. Deploy to a public Vercel URL and verify the page in a real browser.
18. Sync metadata, project naming, and deployment aliases only after the user-facing tone and visual family are correct.
19. If the user asks to preserve or recover an earlier version, restore the correct deployment first and then sync local code to it.

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
   - browser verification evidence for that URL

### Preferred implementation path

1. Create the empty target directory.
2. Immediately create `AGENT_STATUS.md` with:
   - status
   - current step
   - what has actually been executed
   - next concrete action
3. Scaffold a fresh React + Vite + TypeScript app from scratch.
4. Replace the starter app immediately after scaffold.
5. Create planning artifacts before visual polish:
   - `planning/planning-artifact.md`
   - `planning/research-record.md`
6. Validate route logic before visual polish:
   - choose `primary template` and optional `overlay`
   - validate core stops and major hops with map sources
   - adapt outdoor / indoor order with forecast or seasonal fallback
7. Define the route-guide structure before visual polish:
   - `hero`
   - `overview`
   - `route guidance` only when the route truly needs explanation
   - `packing / prep`
   - `days[]`
   - `transport / lodging`
   - `cautions`
   - `foods / specialties`
   - `budget`
8. Source at least:
   - 1 Hero cover
   - 2 supporting atmosphere or itinerary images
   - 1 image per day or per tightly grouped day-pair
9. Store all chosen assets locally under the new project.
10. Implement the page shell and Hero transition.
11. Implement the itinerary and supporting sections in human-facing language, not planning labels.
12. Run `npm run build`.
13. Deploy to a new public Vercel URL unless a real deploy blocker exists.
14. Verify the deployed URL in a real browser.
15. Capture desktop and mobile visual evidence.
16. Write a strict benchmark-gap note before calling the validation complete.

### Minimum visible filesystem state before claiming momentum

These files or their equivalents should exist:

- `AGENT_STATUS.md`
- `planning/planning-artifact.md`
- `planning/research-record.md`
- `planning/visual-qa.md` or screenshot-backed benchmark notes
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
- the Hero or day imagery is obviously low-resolution, vector-like, placeholder-ish, or semantically wrong
- the project never reaches a successful build
- there is no map validation record for a 0-to-1 route guide
- there is no weather adaptation record for an outdoor-heavy route
- there is no public deployment URL and no evidenced blocker
- the page was not browser-verified after deployment
- browser verification has no desktop / mobile visual evidence
- the validation output does not compare the result against the benchmark family
- the timeline is crude, misaligned, or visibly pierces nodes
- the route-loop / map-summary is decorative, confusing, or lacks clear start / end logic
- the music control behaves like a fake toggle or the vinyl state drifts from the real player state
- the visible page reads like a system demo, dashboard, or audit panel instead of the benchmark family
- the overall result still reads like a prototype instead of a polished benchmark-family microsite

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

Treat these as the minimum viable planning inputs:

- destination
- trip length or date range
- travel party
- at least one hard anchor when available
  - lodging area
  - transport mode
  - must-keep stop
  - fixed reservation / event

Treat these as optional enrichers rather than blockers:

- flight / train details
- hotel candidates or preferred district
- must-eat / must-skip preferences
- budget breakdown
- accessibility, luggage, elder / child constraints
- checklist items, booking references, visa or document notes

If some inputs are missing, make reasonable assumptions and label them clearly in the generated plan.
Ask at most `2` concise clarifying questions, and only when a missing input would materially change the route.

Before retrieval, classify the trip into a planning template using at least:

- transport mode
  - self-drive
  - flight / rail arrival
  - walk-heavy local transit
- rhythm
  - staycation / relaxed
  - balanced
  - special-forces
- travel party
  - couple
  - friends
  - family
  - elders-included

Do not stop at a loose label.
Resolve the trip into:

- one `primary template`
- one optional `overlay`
  - for example: `flight / rail hub-and-spoke` plus `family / elders`

Resolve template conflicts in this order:

1. safety, mobility, and physical burden
2. fixed transport or lodging structure
3. trip rhythm
4. interest bias

Retrieval, route scoring, and daily density should follow that resolved template rather than using one generic destination search path.

Before writing the actual route, the planner should explicitly reason through:

- multiple public research angles, not one generic search phrase
- weather-sensitive outdoor / indoor swaps
- whether each place is real, reachable, and worth the detour
- sequence by distance, transit burden, and opening-hour logic
- whether the stop order forms a clean loop, a clean linear chain, or wasteful backtracking
- a short "why it is worth going" rationale for major stops
- what can be safely omitted, downgraded to an estimate, or turned into a default checklist instead of being fabricated
- what the day shape should be for this template
  - how many hard anchors
  - how many heavy transfers
  - how much breathing room

Template-specific day-shape defaults:

- self-drive loop
  - allow `2-4` anchors and `1` heavy drive segment as the normal center of gravity
  - penalize late-night return driving and parking-friction detours
- flight / rail arrival
  - compress arrival and departure days
  - favor one-base efficiency over unnecessary hotel moves
- staycation / resort-centered
  - reward fewer anchors, longer soft windows, and hotel-centered rhythm
  - penalize overpacked days that destroy the vacation pace
- special-forces
  - reward opening-hour efficiency and queue avoidance
  - cap impossible transfer stacks and fatigue cliffs
- family / elders
  - reward shorter walks, meal cadence, restroom predictability, and indoor backup
  - downgrade routes that depend on stairs, steep terrain, or constant hard transitions

Map validation is mandatory before route finalization.

For each core stop, record at least:

- canonical place name
- map or venue source used
- branch / entrance confirmation when relevant
- stable map reference or coordinates when available
- whether it is safe to use as a timed anchor

For each major hop, record at least:

- from / to
- transport mode
- estimated duration
- whether it counts as a heavy transfer or heavy drive
- whether it introduces avoidable backtracking

Each day should also carry a route topology label:

- `clean loop`
- `clean chain`
- `there-and-back`
- `backtracking-heavy`

Weather adaptation is mandatory for outdoor-heavy routes.

Record at least:

- weather source
- query date or forecast window
- whether the result is live forecast or seasonal fallback
- weather-sensitive blocks
- outdoor / indoor reorder decision
- Plan B trigger conditions

If the travel date sits inside a usable forecast window, use forecast to shape the day.
If not, use seasonal climate guidance and mark it explicitly as an assumption.

The minimum structured output should include:

1. itinerary overview
2. route-loop / map-summary when multiple clusters or self-drive order matter
3. daily plan with time, place, and food
4. packing / pre-trip preparation and checklist
5. in-trip notes and cautions
6. transport and lodging guidance
7. recommended food and local specialties to bring back
8. overall budget
9. useful local info when the trip is international, remote, or likely to be shared with others
10. emergency / support notes when the trip is international, self-drive, remote, or logistics-heavy

The planning artifact must explicitly declare:

- `primary template`
- optional `overlay`
- key assumptions
- `route topology label`
- `map validation summary`
- `weather adaptation summary`
- `day-shape reasoning`

### If the source is a route guide

Extract and normalize:

- Hero title
- Hero subtitle or duration
- route-loop inputs when applicable:
  - canonical place names
  - coordinates or stable map references
  - stop order
  - transport mode per hop
  - drive / transit burden
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
2. map-backed truth layer
   - Amap / Google Maps / other dominant local map product
   - official venue location pages
   - station / airport / district lookup
   - branch, entrance, and coarse travel-time verification
3. decision layer for food and lodging
   - public Meituan / Dianping / OTA / hotel-booking pages when reachable
   - official hotel or restaurant pages when they exist
   - use this layer for price band, business status, recent review drift, and whether a stay or meal is actually worth recommending
4. current public web results for practical travel synthesis
5. public UGC for heuristics, atmosphere, and edge-case tips

Use public Xiaohongshu notes only as a supplemental signal source for:

- recent crowd or queue patterns
- photogenic spots
- local food heuristics
- practical gotchas
- mood and neighborhood feel

Do not treat UGC as authoritative for:

- opening hours
- ticket prices
- regulations
- transportation rules
- exact hotel availability
- exact restaurant business status

If Xiaohongshu is part of the research mix:

- prefer publicly reachable pages or search-engine-discovered note pages
- summarize patterns instead of overfitting to one note
- cross-check practical claims against more stable sources
- avoid assuming an official note-search API exists unless you have verified one

For food and lodging, apply this split:

- truth layer
  - is the place real
  - where exactly is it
  - which branch or district does it belong to
  - is it plausibly open / operating
- decision layer
  - is the price band acceptable
  - is the review pattern stable enough
  - does it fit the route without adding ugly detours
- inspiration layer
  - what people actually like there
  - what to order
  - what to avoid
  - what mood, crowd, or photo expectation to set

Recommendation rule:

- final page copy should present clean recommendations, not source talk
- but the agent should be ready to explain in chat why a hotel, district, or restaurant was chosen
- every strong meal or stay recommendation should ideally be backed by:
  - one truth-layer confirmation
  - one decision-layer confirmation
  - optional inspiration-layer support
- if only inspiration-layer evidence exists, keep it as a soft suggestion instead of a core anchor

For stronger route quality, also read:

- `references/intent-to-itinerary-planning.md`
  This file defines multi-angle UGC search, weather-aware route swaps,
  place validation, sequencing logic, and "why worth going" recommendation framing.
  It also defines the default query pack, confidence ladder, mainland-China map stack,
  and walk / transit thresholds that should be used unless the trip clearly needs an override.

Research records for 0-to-1 planning must include:

- which official venue or map-backed sources were actually checked
- which food / lodging decision-layer sources were actually checked
- which public UGC buckets were actually used
- why each major stop stayed or got dropped
- how each important hop was judged for backtracking risk
- how weather changed the order, timing, or fallback plan
- which concrete restaurant or hotel candidates were promoted, demoted, or left as backup

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
4. actual stored high-resolution image assets for the itinerary, not just text sections
5. a structured itinerary layout that feels like the benchmark family
6. tags with concrete place / food semantics and icons
7. motion and mobile spacing that feel intentional, not default
8. route-guide section order that reads cleanly on mobile:
   - overview
   - route-loop / map-summary when applicable
   - packing / prep
   - daily route
   - transport / lodging
   - cautions
   - food / specialties
   - budget
9. visible food / specialties content when the trip clearly has a food dimension
10. if the Hero uses an overline travel mark, it should be editorially framed rather than floating as a naked label
11. if a timeline is used, it must clear the node / time alignment quality bar
12. if a route-loop is used, it must communicate route logic clearly enough to justify its presence
13. if a vinyl player is used, its motion and toggle state must follow the real media state
14. the page must pass the human sniff test of looking like the shipped benchmark family, not a prototype
15. desktop and mobile screenshots must be reviewed before the run is marked visually passed

If these are missing, the result is an incomplete scaffold, not a passed cold-start website.

### Benchmark-family visual blind-test gate

Before calling a new site visually passed, inspect it as if the user only sees screenshots and does not know the planning work behind it.

The page fails if any of these are true:

- the mobile Hero title wraps into awkward stacked fragments, isolated characters, or uneven two-line clumps
- the Hero copy cluster is too low, too small, too thin, or missing visible shadow
- the overline travel mark loses its flanking hairlines or drifts off the title axis
- the second screen starts as a hard slab, pure flat color, or glued content block instead of continuing the blurred Hero world with breathing room
- visible page copy includes planning artifact words such as `route topology`, `there-and-back`, `validation`, `confidence`, `artifact`, `record`, `module`, or `source audit`
- food, budget, packing, or route sections are presented as generic boxed panels rather than quiet editorial sections
- the page relies on too many module shells or repeated card treatments instead of spacing, typography, and imagery
- imagery looks like low-resolution placeholders, vector art, or city-name filler rather than section-matched photography
- the timeline feels like a utility rail, misaligned schedule table, or bulky card stack
- the route-loop looks like a decorative diagram without clear start / end direction or a graceful reason to exist
- the fixed music player is visually heavier than the Hero or its tonearm / disc state does not match real audio playback
- the player silhouette or behavior no longer resembles the shipped benchmark family

If a module is the source of the failure, the correct repair is often removal or simplification, not more ornament.

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
- test the Hero at `390px` wide or narrower; if the main title cannot fit gracefully, shorten the title or redesign the title grid before shipping
- prefer a one-line title for short destinations; if a title must wrap, the wrap should be intentional and balanced, not browser-default breaking
- avoid letter-spaced English so wide that it pushes Chinese title layout into awkward wrapping
- do not use `break-all`, uncontrolled `tracking-widest`, or unconstrained large serif type on mobile Hero titles

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
- reveal states should not make key sections disappear into blank screenshots or anchored browser checks

Do not:

- animate every section with a different visual language
- rely on blur-reveal gimmicks
- stack too many overlapping motion effects in one area

## Timeline and story systems

### Route-loop / map summary

Use this module when:

- the trip is self-drive or taxi-heavy
- one day spans 3 or more distinct geographic clusters
- the user would reasonably want to know whether the route folds back on itself
- route order is part of the travel value, not just logistics

Do not use this module when:

- the trip is simple enough that overview + daily text already explain it
- the page starts feeling more like a product panel than an editorial travel story
- the visual family would be cleaner with a lighter one-paragraph route note instead

The goal is not to embed a noisy consumer map. The goal is to expose route logic editorially.

Default contract:

1. show the day or trip loop as a restrained schematic line or simplified map path
2. make each major node hoverable on desktop and tappable on mobile
3. reveal the key stop name, hop duration, and why that node matters
4. show whether the route is:
   - loop
   - linear chain
   - there-and-back
   - backtracking-heavy
5. summarize:
   - total distance or total drive burden
   - longest hop
   - cluster count
   - backtracking risk or detour note

Visible-language rule:

- backstage terms such as `topology`, `validation`, or `confidence` should not appear in user-facing headings
- prefer softer headings such as `这一天为什么这样走` or `路线这样排会更顺`
- never render raw planning labels such as `clean loop`, `clean chain`, `there-and-back`, or `backtracking-heavy`; translate them into gentle copy such as `一路向前，不折腾`, `当天往返，节奏放轻`, or `这段会稍微绕一点`
- if the route status cannot be phrased naturally in one short sentence, keep it in the planning artifact and omit it from the UI

Design rules:

- do not let the map module overpower the Hero or day timeline
- use the same motion language as the rest of the page
- keep labels sparse and readable
- prefer a stylized editorial diagram over a raw app screenshot
- if a live map embed is used, it must still be framed by a cleaner summary layer
- start and end must be legible at a glance through text, icon, or directional treatment
- nodes should read as independent stops, not as circles crudely pierced by a line
- right-side explanations should be curated prose, not unordered metadata; if the text reads like a route debugger, collapse it to one warm paragraph
- arrows, start / finish labels, and hop hints should be subtle but present when route direction matters
- do not show a route-loop just to prove map validation happened; only show it when it improves the traveler's understanding

Planning rules:

- if the backtracking is obvious, revise the route before polishing the UI
- if coordinates are uncertain, downgrade the module to a cluster-summary graphic instead of pretending false precision
- if the trip is a simple single-cluster citywalk, the module may collapse into a small path summary or be omitted
- if the route-loop cannot look benchmark-grade, remove it and let overview + daily text carry the logic instead

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
8. The timeline should feel like floating editorial points, not cards hanging off a utility rail.
9. On mobile, the timeline should become clean stacked editorial beats; do not squeeze a desktop three-column rail into a narrow screen.
10. If time labels become louder than the event title, reduce their size, opacity, or visual prominence immediately.
11. Tags inside timeline rows must not create layout collisions or force paragraph text into thin columns.

Do not:

- use thick black rings
- oversize the time text
- wrap the interaction in bulky card chrome
- let time, node, and heading drift off the same visual baseline
- use cheap blur-reveal tricks or oversized occupancy blocks around each event
- keep a border box around the whole timeline if it makes the schedule feel like a spreadsheet

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
- section surfaces should feel like layers of an editorial spread, not component cards; use spacing, type, and image rhythm before borders
- if borders are needed, use hairline opacity and avoid boxing every item
- budget, food, lodging, and prep modules should each have distinct editorial hierarchy, not one generic grid-card treatment copied across sections
- visible explanations should sound useful and warm; keep research certainty, provider names, and audit details in planning files unless the user asks to see them
- collapse neighboring support content when separate boxes add more UI than clarity
- if three adjacent sections can be expressed as one quieter editorial spread, choose the spread over three modules
- the safest anti-generic move is fewer containers, not more decoration
- for route-guide pages, default section order is:
  - itinerary overview
  - route-loop / map-summary when applicable
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
- reject assets that are obviously low-resolution, screenshot-like, flat illustrative SVGs, or placeholder textures for a passing validation

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
4. Record music provenance before integration:
   - chosen direction
   - search phrase or user-provided origin
   - source URL or local source path
   - final stored project path
   - file hash
   - whether reuse was explicitly approved
5. Integrate the chosen file into the project.
6. Verify playback against the real media element.

Cold-start validation rule:

- if the audio file hash matches a prior shipped or in-repo project track and the user did not explicitly approve reuse, the run does not count as a valid cold-start pass
- renaming an old track is still reuse

Player rules:

- keep the control fixed and visually quiet
- the user should be able to understand it without bulky `Play / Stop` text
- a small vinyl-disc control is a strong default for this project family
- clicking the disc should toggle playback
- if a tonearm is present, it must drop on play and lift on pause
- keep the player small enough that it does not dominate mobile viewports
- do not expose an ornamental vinyl shell that is not truly bound to the audio element state
- keep the control language consistent with the shipped Xishuangbanna / Jingshan family; do not redesign the player into a new capsule, toolbar, or card unless the user explicitly asks
- default to disc-first interaction; any helper text should stay secondary enough that the control still reads as the same family object

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
- test at both mobile Hero and mid-page timeline positions; a site can fail even if the top screen is acceptable
- never let the fixed player cover route text, timeline nodes, or Hero overline on small screens
- if mobile screenshots do not look like an intentional travel poster plus editorial scroll, the responsive pass is not done

## Cold-start workflow standard

When the user asks for a brand-new route-guide website from 0 to 1, the workflow must be:

1. plan the itinerary structure
2. write the visual shot list
3. source images from Pixabay and other valid sources, with Pinterest allowed for visual discovery
4. save the chosen assets into the project
5. decide whether route-loop / map-summary is required and prepare its data
6. build the Hero and second-screen transition around those real assets
7. build the structured itinerary, tags, route-loop module, sections, and motion system
8. add audio only after the visual shell is already correct
9. verify mobile readability and project-family similarity before deployment
10. deploy to a public Vercel URL and verify the deployed page in a browser
11. capture desktop and mobile screenshots
12. write `planning/visual-qa.md` or an equivalent screenshot-backed note that honestly says pass / fail against the benchmark family

The workflow is not:

1. generate text
2. wrap it in dark cards
3. deploy it
4. promise that imagery can be added later
5. stop at a markdown report with no public webpage
6. stop at a public webpage with no screenshot-backed visual review

## Deployment and recovery hygiene

- a new destination usually means a new local project and a new Vercel project
- keep project name, page metadata, and public alias in sync
- if the user says an earlier version was better, inspect Vercel deployments and restore the correct one instead of approximating it from memory
- after restoring a deployment, sync local code to that restored state before continuing edits
- verify the final share URL is public and reachable
- verify the final share URL actually loads in a browser after deployment

## Anti-patterns learned from this project

### Hero mistakes

Do not:

- blur the visible Hero image
- stack multiple transition strips to hide a seam
- add a separate dark strip and call it a transition
- let Hero and the first content block crash into each other
- “fix” centering by nudging one line independently from the rest of the stack
- let destination names break into isolated characters or mismatched stacks on mobile
- make the Hero look like text placed on a plain dark background when an atmospheric cover image is expected

### Typography mistakes

Do not:

- leave Hero text too thin to read on photography
- forget shadow on bright covers
- allow key desktop day titles to wrap casually
- use supporting labels so small or thin that they feel accidental
- expose uppercase technical route labels in the visual UI
- let English subtitles become wider than the mobile title shell and force visual imbalance

### Timeline mistakes

Do not:

- let the line pierce the node
- use a permanently filled node if hollow-to-solid hover is intended
- surround the node with a heavy ring
- let hover states become noisy or cheap
- replace the light floating rhythm with bulky timeline cards that consume the layout
- draw a full-height border frame around the timeline that makes it feel like a boxed table

### Content mistakes

Do not:

- add AI-ish prefatory writing that the user did not ask for
- replace first-person memories with generic summary prose
- assign arbitrary tags
- use semantically wrong images
- show map / weather / source methodology as stiff page modules; keep it backstage unless it is rewritten into human travel guidance

### Music mistakes

Do not:

- let the UI claim music is playing when the media element is silent or blocked
- make the vinyl control oversized
- swap the compact benchmark-family player for a new component style that only appears in one validation run
- forget repeat toggle behavior after the first interaction
- hardcode a copyrighted commercial track without permission

### Process mistakes

Do not:

- create a parallel replacement skill when the user asked to refine this one
- ship after desktop-only review
- change project identity without syncing Vercel naming and metadata
- let Pixabay-only sourcing block delivery when a valid fallback source exists
- ignore build output after adding Chinese webfonts
- accept “more modules” as a shortcut for clearer information architecture when it visibly pushes the page toward AI UI

## Debug checklist

When the page still feels off, inspect in this order:

1. Is the visible Hero image accidentally blurred?
2. Is there a visible seam caused by an extra background or opaque slab?
3. Is the Hero stack mis-centered because the three lines do not share one width shell?
4. Is the Hero too low on mobile?
5. Are tags semantically wrong or visually noisy?
6. Does the timeline line pierce the node?
7. Are day images mismatched to the text?
8. Does the route-loop / map-summary reveal the real route logic, or is it decorative nonsense?
9. Is music UI detached from the real playback state?
10. Is the fixed player covering too much on mobile?
11. Is there a public URL and did the browser check succeed?
12. Would a human confuse this page with the shipped benchmark family, or does it still read like a prototype?
13. Do the mobile and desktop screenshots both pass, or did one viewport quietly regress?
14. Is the player still the same family object as the shipped projects, or did a new component language sneak in?
15. Could two or three support modules be collapsed into one calmer editorial spread to reduce AI UI?

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
