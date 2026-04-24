# Workflow From Brief To Site

Use this reference when the user gives raw travel text, a doc, a notion page, a feishu export, a partially finished site, or a high-level travel intention and wants a finished editorial travel webpage.

## 1. Protect the project boundary first

Before doing any styling:

- determine whether this is a new destination or an update to an existing site
- if it is a new destination, create a new local project and a new Vercel project unless the user explicitly wants replacement
- if the user says an older online version was better, restore that deployment first instead of trying to recreate it from memory

## 2. Normalize the source before designing

Convert the raw material into structured content first.

Always extract:

- Hero title
- Hero subtitle / duration
- day list
- major scenes
- food / tips / budget / packing if present
- music request or mood

If the source is only an intention and not yet a route guide, switch to the dedicated planning workflow in [intent-to-itinerary-planning.md](intent-to-itinerary-planning.md) first, then come back here once you have a structured itinerary draft.

That draft should already declare:

- chosen `primary template`
- optional `overlay`
- key assumptions
- research record
- map validation summary
- weather adaptation summary
- route topology label
- day-shape logic for each day

But those planning artifacts are backstage inputs.
Do not mirror their labels or audit language directly into the rendered page.
The visible page should read like an elegant travel guide for people, not a planning console.

## 3. Decide the content mode

### Route-guide mode

Use when the source is itinerary-first.

Structure into:

- `hero`
- `overview`
- `route-loop / map-summary`
- `packing / prep / checklist`
- `days[]`
- `transport / lodging`
- `cautions`
- `foods[]`
- `useful info?`
- `emergency / support?`
- `tips[]`
- `budget[]`

Each day should usually contain:

- one-line day title
- intro
- timed events
- concrete place / food tags
- one semantically correct image target

The overall route-guide package should usually also include:

- itinerary overview
- route-loop / map-summary when the route spans multiple clusters or self-drive logic matters
- packing, pre-trip prep, and checklist
- daily route after prep, not before
- transport and lodging notes
- cautions / reminders
- recommended foods and specialties
- useful local info when the trip is international, remote, or self-drive heavy
- emergency / support notes when the trip is international, remote, or logistics-heavy
- budget

Default route-guide reading order:

1. itinerary overview
2. route-loop / map-summary when applicable
3. packing, pre-trip prep, or checklist
4. daily itinerary
5. transport and lodging
6. cautions / reminders
7. recommended foods and specialties
8. useful local info / emergency notes when relevant
9. budget

Tone rule for visible route-guide sections:

- turn planning logic into human language
- prefer expressions like `为什么这样排`, `如果下雨就这样改`, `这一天适合慢一点`
- avoid headings or copy that read like `validation`, `topology`, `confidence`, `artifact`, `record`, `module`, `system`
- if a block starts feeling like an audit panel, collapse it back into the existing editorial sections
- never surface raw planning labels such as `clean loop`, `there-and-back`, `backtracking-heavy`, `confidence`, or `source audit`
- if a route explanation cannot be rewritten into warm travel prose, keep it in the research record instead of forcing it into the page

Validation-facing route-guide outputs should also expose:

- public Vercel URL
- build result
- browser accessibility result
- benchmark-family gap summary

### Memoir mode

Use when the source is story-first.

Structure into:

- `hero`
- `days[]`
- each day split into beats by time, moment, or emotional node

Rules:

- preserve first-person voice
- compress gently, not mechanically
- keep memorable lines and emotional anchors
- do not insert meta writing such as “from Notion” or “restored from”
- the output should sound like the author, only more structured

For tone and wording constraints, use [editorial-writing-and-mood-mapping.md](editorial-writing-and-mood-mapping.md).

## 4. Build the shot list

Before visual polish, list:

- Hero cover scene
- one image per day or beat
- any non-negotiable supporting scenes
- optional fallback images if the first-choice scene cannot be sourced

Check image targets literally against the text. If the scene is fireflies, use fireflies or a directly related garden scene, not a random animal.
Each chosen image should be traceable to a specific section or beat; do not choose by city-name vibes alone.

This is also the point where you should compare the target structure to the shipped benchmark family. If the page you are about to build would look like a text-only article rather than the Xishuangbanna / Jingshan project family, stop and fix the shot list and structural plan first.

Before implementation, also pressure-test the Hero title on mobile:

- if the title is longer than one calm line on a common mobile width, shorten the wording before shrinking the type into weakness
- if the title uses two destinations, make the separator the optical axis rather than letting the browser decide the wrap
- if the overline travel mark exists, keep the framing hairlines and shared width shell

## 4.5. Source and store the image assets

Do not move straight from shot list to implementation without real assets.

Default route-guide image workflow:

1. user-provided files when available
2. Pixabay for shippable free assets
3. Pinterest for scene discovery and visual-reference discovery
4. trace Pinterest references to a shippable asset source when needed
5. generate only the missing scene if sourcing still fails

Then:

1. save the chosen assets into the project
2. wire the local paths into the page
3. verify the Hero image works both clear and blurred
4. reject assets that are obviously low-resolution, vector-like, or too muddy for both clear and blurred use
5. reject assets that are semantically correct but visually flat, watermark-heavy, documentary, or lifeless in the benchmark family

Before you approve an asset, run this short beauty check:

- does it have one readable focal subject
- does the light help the page, rather than flatten it
- does it still feel elegant after a crop, blur, or dark overlay
- would a human describe it as beautiful, not just informative

If the answer is no, keep sourcing.
Do not let the first factually correct image become the final shipped image.

If the page still has no meaningful images at this stage, it is not ready for implementation.

## 5. Fix structure before effects

Work in this order:

1. fixed blurred global background
2. clear Hero cover with bottom mask fade
3. transparent next section over the same background
4. optical Hero centering
5. route-loop / map-summary geometry when applicable
6. timeline or memoir beat geometry
7. section rhythm

Visual family guardrail:

- the first two screens must keep breathing room and soft continuity
- do not introduce hard bands, dashboard rows, loud tinted strips, or abrupt seams
- use the established benchmark family as the ceiling, not as loose inspiration
- do not rescue weak structure with extra cards, extra borders, or extra gradients
- if the second screen feels glued to the Hero, add breathing space and fix the shared background before styling the module itself
- if support content starts turning into a stack of equal-looking modules, merge and simplify until the page breathes again

Do not pile on new effects before this structure is correct.

If the source started as a 0-to-1 planning brief, do not enter this implementation phase until:

- map validation has been recorded for core stops and major hops
- weather adaptation or seasonal fallback has been recorded for outdoor-sensitive blocks
- the research record explains keep / drop decisions
- if map or weather capability had to be installed on the fly, the install attempt and fallback result are recorded explicitly

### Route-loop / map-summary contract

When a route-guide includes multiple clusters, self-drive sequencing, or obvious order tradeoffs, add a route-loop / map-summary module instead of forcing the user to infer the route from timeline text alone.

Only keep this module if it still feels editorial.
If it starts reading like a product dashboard, route debugger, or operations panel, simplify it or fold the logic back into overview + daily text.

What it should communicate:

- the macro route order
- whether the route is a loop, chain, there-and-back, or backtracking-heavy
- total drive / transit burden
- longest hop
- why each major node exists

Interaction rules:

- desktop: hover major nodes to reveal stop name, hop time, and short value note
- mobile: tap nodes or use a compact accordion / drawer pattern
- keep the module editorial and schematic; do not default to a noisy raw map screenshot
- start and end must be clearly legible through label, icon, or directional treatment
- avoid line-through-node geometry that makes the module feel cheap
- supporting explanation should read like a short route note, not a metadata dump
- if labels overlap, stack awkwardly, or turn into a small dashboard, simplify the module immediately

Quality rule:

- if the diagram reveals clear wasteful backtracking, revise the route before polishing the section
- visible labels should stay soft and human-facing
- prefer `怎么走更顺` over `route topology`
- prefer `雨天怎么改` over `weather adaptation module`
- if the module cannot reach benchmark quality, collapse it into lighter overview prose rather than shipping a weak diagram
- do not print uppercase technical chips such as `THERE-AND-BACK (LIGHT)` or `CLEAN LOOP`

### Timeline quality bar

If a route-guide uses a visible time-based timeline:

- keep time, node, and heading on a disciplined shared rhythm
- time text should be quieter than the event title
- the line must never visually pierce the node
- the node should feel hollow by default and fill or glow gently on hover / reveal
- avoid bulky timeline cards that consume space and break the editorial lightness
- if the timeline still feels clumsy after simplification, reduce the chrome rather than adding more effects
- do not frame the whole timeline in a hard rectangle if that makes it read like a schedule table
- on mobile, convert the rhythm into clean stacked beats rather than squeezing the desktop rail intact
- tags must not force the content column into narrow text wraps

## 6. Establish one motion system

Good defaults:

- section fade-up
- restrained route-loop node reveal
- progressive reveal on scroll
- restrained timeline hover
- slow bounce for the scroll line
- subtle fixed music-control motion

If any effect stutters:

- simplify it
- reduce overlap
- avoid blur-heavy reveal patterns

## 7. Add music after layout is stable

When the page is visually stable:

1. recommend 2 to 4 music directions
2. let the user choose a direction
3. source from Pixabay or use a user-provided local file
4. record music provenance:
   - chosen direction
   - search phrase or local-file origin
   - source URL or original local path
   - final in-project path
   - file hash
   - whether any reuse was explicitly approved
5. wire the track into the page
6. verify playback behavior in a real browser

Do not silently skip the music step on a travel microsite just because the user did not provide a file.
If music is appropriate for the page family and the user has not opted out:

- proactively recommend directions
- include Pixabay search phrases
- make a recommendation
- if the user is unavailable and autonomy is expected, choose a safe royalty-free Pixabay direction and state that it was auto-selected

Validation rule:

- a cold-start sample should either include a functioning music choice / embed result
- or explicitly record why music was deferred
- it should not simply forget the music chain

Rules:

- if the user wants default playback, attempt autoplay but keep a reliable click fallback
- the player UI must follow the real audio state
- if a vinyl control is used, the tonearm state must match play / pause
- keep the control fixed and small enough for mobile
- do not count a decorative vinyl shell as complete if the disc / tonearm states are visually reversed or disconnected from playback
- if a cold-start validation reuses the same audio hash as another local or shipped project without explicit approval, invalidate the run and source a fresh track
- keep the player visually in-family with the shipped projects; do not replace the compact vinyl object with a new pill / widget style for one-off validations
- if helper text makes the player louder than the page, reduce or remove the text before changing the player shape

## 8. Mobile pass

Check all of these explicitly:

- Hero title wrapping
- Hero vertical center of gravity
- shared axis of travel mark, title, and subtitle
- separator dot alignment
- `Scroll To Read` position
- section spacing
- route-loop readability and tap targets
- timeline readability
- fixed player overlap
- Hero text readability over the cover image
- whether the page still resembles the benchmark family when seen only as a mobile screenshot
- whether any section has drifted into repeated generic card styling

Do not ship after desktop-only review.

## 9. Naming and deployment hygiene

Before shipping:

- update page title and metadata
- update local naming if relevant
- update Vercel project naming if relevant
- update the public alias
- verify the final URL is actually public and reachable
- verify the final URL in a browser, not just through CLI output

Validation report order should be:

1. public URL
2. browser check result
3. desktop / mobile screenshot evidence
4. planning / research summary
5. benchmark-family gap summary

## 10. Final QA

Before closing:

- no visible seam between Hero and next section
- no blurred visible Hero image
- no image-less route-guide shell pretending to be complete
- no decorative route-loop diagram that hides the real detour logic
- no semantically wrong day images
- no arbitrary tags
- no dead sections while only one block has motion
- no dead air created by over-padding or hidden reveal states
- no typography that is too thin to read on mobile
- no music UI state drift
- no low-resolution or illustrative fallback imagery posing as final photography
- no crude timeline / route-loop / player module surviving just because it was harder to remove
- no boxy support sections that read like a generic dark template
- no multiplication of support modules when a calmer merged editorial section would read better
- no raw planning-status labels visible anywhere on the page
- no project-name confusion between destinations
- no final implementation that relies on scattered remote placeholder images when approved assets could have been stored locally
- no 0-to-1 route guide that skips map validation or weather adaptation records
- no final validation handoff that only contains markdown and no public URL unless a blocker is proven

## 11. Strict cold-start execution checklist

Use this when testing whether the skill is truly reusable by a no-context agent in an empty directory.

### Required order

1. create empty target directory
2. create `AGENT_STATUS.md`
3. scaffold app from scratch
4. replace starter code immediately
5. create planning artifacts
   - `planning/planning-artifact.md`
   - `planning/research-record.md`
6. validate core stops and major hops with map sources
7. validate weather adaptation or seasonal fallback
8. source and store real local images
9. decide whether route-loop / map-summary is required and prepare its node data
10. implement Hero + blurred global background + natural second-screen transition
11. implement itinerary structure, route-loop if needed, and support sections
12. run build
13. deploy
14. browser-verify the deployed URL
15. capture desktop and mobile screenshots
16. write a benchmark-family pass / fail note backed by those screenshots

### Do not stop early

These are not acceptable stopping points:

- only `package.json`
- only `index.html` plus starter source
- `App.tsx` with placeholder text
- one downloaded test image with no implemented page
- a route-guide page without stored local imagery

### Required output state

At minimum, the cold-start project should contain:

- real React page code
- planning artifacts with map and weather records
- local image assets in the project
- a completed Hero section
- a visible second-screen atmosphere using the same cover world
- structured itinerary content
- a successful build
- a public deployment URL or a clearly evidenced deployment blocker
- browser verification evidence for that URL when deployment succeeds
- screenshot-backed desktop and mobile benchmark notes

If the output only proves “the agent can scaffold a Vite app,” the cold-start validation has failed.
