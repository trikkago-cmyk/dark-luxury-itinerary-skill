# Image And Audio Pipeline

Use this reference when you need to source, generate, validate, or replace visuals and BGM for an editorial travel page.

## 1. Source priority

### Images

Use this order:

1. user-provided image or explicit image direction
2. Pixabay
3. Pinterest for scene discovery, composition references, and finding the right visual direction
4. Pexels or another cleared editorial-friendly stock source
5. high-quality editorial stock image or the traced original source from Pinterest
6. generated image

### Audio

Use this order:

1. user-provided local file
2. Pixabay Music
3. cleared royalty-free track
4. generated ambient fallback

Pixabay is the preferred free-first source for this project family because it can cover images, video, and audio in one pipeline.

Pinterest is useful when the missing problem is not “where do I get a file” but “what exact scene language should this page look for”. It is not a blanket license source by itself.

## 2. Hero image rules

The Hero image should:

- support a wide landscape crop
- stay strong both clear and blurred
- have depth and atmosphere
- avoid generic tourism clutter
- remain readable behind white titles with shadow

Technical target:

- around `2000px` to `3000px` wide
- clean enough for full-screen crop
- strong enough to survive both clear display and blurred reuse

## 3. Day or beat image rules

Day / beat images should:

- match the literal scene in the text
- survive portrait or narrow responsive crops
- avoid filler images
- feel editorial rather than promotional
- be chosen for a named section, day, or beat rather than for general city vibes
- still feel beautiful after the destination is identified

Reject an image if:

- the subject does not match the itinerary or memoir beat
- it becomes muddy when blurred
- it looks AI-generic or oversaturated
- it fights the page’s restrained color system
- it has a visible watermark, date stamp, screenshot chrome, or archive-like record noise
- it only proves the place exists but brings no light, depth, or emotional pull
- the sky is dull, the framing is surveillance-like, or the overall read is flat and documentary when the page needs softness

### Editorial beauty filter

Every chosen asset must pass two tests:

1. `semantic fit`
   - is this truly the place, beat, or atmosphere the copy is talking about
2. `editorial beauty`
   - would this still feel intentional if it were printed as a full-width spread in the benchmark family

If two assets are equally correct, choose the one with:

- stronger natural light or more legible shadows
- clearer focal subject
- better depth for blur and crop reuse
- less clutter from tourists, signage, vehicles, or utility lines
- more emotional pull, texture, or aftertaste

Do not lock a flat image just because it is “accurate enough”.
The recurring failure mode in cold-start route guides is `correct but plain`.
That still reads as unfinished.

### Support spread rules

Support imagery for overview / aftertaste sections may be slightly less literal than a day anchor image, but it still needs a clear narrative job.

Good support images usually do one of these:

- hold the port / street / temple atmosphere of the next cluster
- give the page a breathing beat between dense text sections
- preserve a destination texture that the user will recognize emotionally, even if it is not a ticketed stop

Bad support images usually do this instead:

- repeat the same flat frontal building shot the main day image already covered
- feel like a tourism brochure attachment
- introduce a random city-vibe picture with no section-level relationship

### Image selection record

If users say the images feel random, the problem is usually that the agent sourced by destination mood instead of by section-level scene.
To avoid this, keep a short image selection record during cold-start work.

Minimum template:

```md
### Image selection record
- target section / beat:
  - requested scene:
  - chosen asset:
  - why this fit won:
  - rejected alternative(s):
```

Rules:

- every Hero image must map to the exact cover mood or place, not just the city name
- every day / beat image must map to a specific route stop, atmosphere beat, or fallback scene
- every support spread must map to a section-level role such as `overview breath`, `south-line texture`, or `closing aftertaste`
- if you cannot explain why the image belongs to that section, do not ship it
- for cold-start validation, record at least the Hero plus one day / beat image choice

## 4. Search strategy

Search by scene, not just by city name.

Examples:

- `Xishuangbanna night market editorial`
- `Yunnan lakeside cinematic travel photo`
- `Jingshan field window view`
- `forest homestay breakfast editorial`
- `rainforest ambiance pixabay`

Useful modifiers:

- `editorial`
- `cinematic`
- `blue hour`
- `night market`
- `rainforest`
- `garden`
- `lakeside`
- `field`
- `homestay`

Pinterest discovery examples:

- `site:pinterest.com Xishuangbanna night market editorial`
- `site:pinterest.com Jingshan homestay window moodboard`
- `site:pinterest.com forest staycation cinematic travel`

Use Pinterest to sharpen the shot list, then move to a shippable stored asset.

## 4.2. Download fallback workflow

When Pixabay is the preferred source but execution gets blocked, do not stall on it indefinitely.

Use this fallback flow:

1. retry the query with the scene, not just the city
2. try a different Pixabay asset or a different orientation
3. open the asset page directly instead of relying on an unstable hotlink
4. save a stable local copy immediately after selection
5. if Pixabay still fails, move to Pexels or another cleared source
6. if no stock source gives the right scene, generate only the missing image

Common reasons to fall through quickly:

- direct download or hotlink is unstable
- only low-quality previews are reachable
- the best Pixabay result is semantically close but visually wrong
- available files collapse under blur or crop

The rule is not “Pixabay at all costs”. The rule is “Pixabay first, then the fastest valid fallback”.

## 4.5. Local asset storage

For this project family, a sourced image should usually be copied into the project rather than left as a fragile external dependency.

Preferred pattern:

1. choose the approved image
2. save it under `public/images/...`
3. use the local path in the app
4. verify the image still works when blurred and when cropped
5. rename files by scene, not by provider or random ID

Do not call a route-guide page complete if it still has almost no images or if its visuals are only vague TODOs.

## 5. Generation fallback

Generate only when the correct scene cannot be sourced cleanly.

Prompt ingredients:

- exact place or scene
- time of day
- weather or atmosphere
- photographic realism
- editorial restraint
- explicit exclusions

Example:

```text
A high-resolution editorial travel photograph of a calm lakeside boardwalk at dusk in Yunnan, soft mountain haze, restrained luxury magazine aesthetic, realistic photography, cinematic natural light, no text, no collage, no fantasy elements, no crowds.
```

## 6. Music direction workflow

Before picking a track, propose 2 to 4 directions such as:

1. rainforest / natural ambiance
2. soft cinematic piano-ambient
3. distant memory / slow folk-ambient
4. slow field-recording / soft travel dusk

Each option should include:

- one-line mood note
- why it fits the page
- a Pixabay-friendly search phrase
- source / licensing path

Then:

- recommend one option as the best fit
- let the user choose when interaction is possible
- if the user is unavailable and the page family clearly suits BGM, auto-select one Pixabay-compatible direction instead of silently omitting music
- record a music provenance note before shipping:
  - chosen direction
  - search phrase
  - source page URL or local-file origin
  - final stored project path
  - file hash
  - whether reuse was explicitly approved

For cold-start outputs, silence is not the default.
If the page supports music and the user has not opted out, the agent should proactively surface the shortlist.

Human-facing rule:

- music should be introduced as mood companionship, not as a technical feature checklist
- recommend it in the same tone as the page, for example `这页更适合雨林白噪音` or `这页更适合慢一点的钢琴氛围`
- do not make the recommendation block feel like a settings panel

## 7. Audio integration rules

Playback rules:

- attempt autoplay only if the user explicitly wants default playing
- never assume autoplay will succeed
- keep a reliable click-to-play fallback
- bind UI state to real media element events
- if the intro is nearly silent, skipping ahead to the first audible section is allowed

UI rules:

- fixed and subtle
- small enough for mobile
- no bulky control labels by default
- a vinyl-disc control is a strong default
- clicking the disc should toggle play / pause
- if a tonearm is shown, it must visibly drop on play and lift on pause
- repeated toggles must continue working after the first interaction
- do not rename an older project track and pass it off as a newly sourced cold-start asset
- if the chosen file hash matches another project and reuse was not explicitly approved, reject it and source a fresh track
- the control should feel like part of the page atmosphere, not a foreign widget

## 8. Local file replacement

If the user provides a local file:

- copy or move it into the project’s public audio path
- update the app to reference the new asset
- verify the file actually loads in the browser
- verify playback state, pause state, and re-toggle behavior
- record the original local path and final hash in the provenance note

## 9. Copyright and fallback policy

- do not ship copyrighted commercial music without a real license or user-provided file
- if the user references a commercial track for mood only, capture the feeling, not the melody
- when licensing is unclear, use Pixabay or another cleared fallback until the user provides an approved asset

## 10. Final media QA

Before shipping:

- Hero image still looks good clear
- Hero image still looks good blurred in the background layer
- day / beat images match the copy semantically
- no wrong subject substitutions
- audio actually plays
- UI state matches audio state
- fixed player does not dominate the mobile viewport
- the final page does not depend on a brittle third-party image hotlink
- music provenance exists and can explain where the shipped track came from
