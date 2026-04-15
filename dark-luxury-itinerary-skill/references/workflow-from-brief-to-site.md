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

## 3. Decide the content mode

### Route-guide mode

Use when the source is itinerary-first.

Structure into:

- `hero`
- `overview`
- `packing / prep`
- `days[]`
- `transport / lodging`
- `cautions`
- `foods[]`
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
- packing or pre-trip prep
- daily route after prep, not before
- transport and lodging notes
- cautions / reminders
- recommended foods and specialties
- budget

Default route-guide reading order:

1. itinerary overview
2. packing or pre-trip prep
3. daily itinerary
4. transport and lodging
5. cautions / reminders
6. recommended foods and specialties
7. budget

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

If the page still has no meaningful images at this stage, it is not ready for implementation.

## 5. Fix structure before effects

Work in this order:

1. fixed blurred global background
2. clear Hero cover with bottom mask fade
3. transparent next section over the same background
4. optical Hero centering
5. timeline or memoir beat geometry
6. section rhythm

Do not pile on new effects before this structure is correct.

## 6. Establish one motion system

Good defaults:

- section fade-up
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
4. wire the track into the page
5. verify playback behavior in a real browser

Do not silently skip the music step on a travel microsite just because the user did not provide a file.
If music is appropriate for the page family and the user has not opted out:

- proactively recommend directions
- include Pixabay search phrases
- make a recommendation
- if the user is unavailable and autonomy is expected, choose a safe royalty-free Pixabay direction and state that it was auto-selected

Rules:

- if the user wants default playback, attempt autoplay but keep a reliable click fallback
- the player UI must follow the real audio state
- if a vinyl control is used, the tonearm state must match play / pause
- keep the control fixed and small enough for mobile

## 8. Mobile pass

Check all of these explicitly:

- Hero title wrapping
- Hero vertical center of gravity
- shared axis of travel mark, title, and subtitle
- separator dot alignment
- `Scroll To Read` position
- section spacing
- timeline readability
- fixed player overlap
- Hero text readability over the cover image

Do not ship after desktop-only review.

## 9. Naming and deployment hygiene

Before shipping:

- update page title and metadata
- update local naming if relevant
- update Vercel project naming if relevant
- update the public alias
- verify the final URL is actually public and reachable

## 10. Final QA

Before closing:

- no visible seam between Hero and next section
- no blurred visible Hero image
- no image-less route-guide shell pretending to be complete
- no semantically wrong day images
- no arbitrary tags
- no dead sections while only one block has motion
- no typography that is too thin to read on mobile
- no music UI state drift
- no project-name confusion between destinations
- no final implementation that relies on scattered remote placeholder images when approved assets could have been stored locally

## 11. Strict cold-start execution checklist

Use this when testing whether the skill is truly reusable by a no-context agent in an empty directory.

### Required order

1. create empty target directory
2. create `AGENT_STATUS.md`
3. scaffold app from scratch
4. replace starter code immediately
5. source and store real local images
6. implement Hero + blurred global background + natural second-screen transition
7. implement itinerary structure and support sections
8. run build
9. deploy

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
- local image assets in the project
- a completed Hero section
- a visible second-screen atmosphere using the same cover world
- structured itinerary content
- a successful build or a clearly evidenced deployment blocker

If the output only proves “the agent can scaffold a Vite app,” the cold-start validation has failed.
