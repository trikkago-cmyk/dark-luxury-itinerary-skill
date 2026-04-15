# Intent To Itinerary Planning

Use this reference when the user does not already have a finished route guide and instead wants Codex to plan the trip from 0 to 1.

Typical prompts:

- “从武汉去西双版纳，做一个七天六夜的路书”
- “两个人清明去襄阳，帮我规划”
- “想从上海去杭州，做一个安静一点的两天微度假网页”

## 1. Intake checklist

Always try to determine:

- origin
- destination
- trip duration
- travel dates or season
- number of travelers
- trip type
  - city walk
  - nature
  - food-first
  - family
  - couple
  - photography
  - mixed
- budget level
- transport preference
- whether the final output should skew practical or literary

If information is missing, infer conservatively and label the assumptions.

## 2. Research order

Use this order:

1. official and primary sources
2. stable current web sources
3. public UGC

Official and primary sources should be used first for:

- transport schedules
- opening hours
- ticket prices
- lodging policies
- weather or seasonal constraints

Public UGC can then refine:

- food picks
- walking rhythm
- photo spots
- queue or crowd heuristics
- what is actually worth skipping

When researching a destination, actively search across multiple user intents instead of one generic query bucket:

- avoid坑 / 不推荐 / 真实体验
- 出片 / 拍照 / 最佳时段
- 本地人推荐 / 非游客向
- 亲子 / 长辈 / 情侣 / 朋友出游
- 雨天替代 / 夜间去处 / 临时 Plan B

## 3. Xiaohongshu usage rule

Treat public Xiaohongshu content as a supplemental signal source, not a source of record.

Good uses:

- finding repeated food recommendations
- identifying recent photogenic or crowded spots
- noticing practical tips that official pages omit
- spotting common itinerary mistakes

Bad uses:

- trusting one note for price or schedule
- copying one creator’s route wholesale
- treating a single viral post as representative

Best practice:

- search for multiple public note hits
- summarize recurring patterns
- cross-check practical claims against more stable sources

## 4. Minimum route-guide schema

When the user wants a full route guide, the structured output should usually include all of the following:

### 1) Itinerary overview

Include:

- total days and nights
- overall route
- daily theme summary
- who the route suits

### 2) Daily itinerary

For each day:

- day number
- one-line day title
- intro
- timed blocks
- a day theme
- why this day is ordered this way

For each block:

- time
- place
- activity
- recommended food when relevant
- how to get there / distance note when relevant
- ticket / reservation note when relevant
- 1 to 2 practical tips when needed
- a short "why it is worth going" reason

Daily sequencing rules:

- cluster nearby stops before crossing the city
- respect opening hours, meal windows, and sunset / night-scene timing
- minimize backtracking unless the detour buys a clearly better experience
- avoid stacking multiple heavy-transit hops in one half day
- cap physically demanding days with a realistic walking load

Place validation rules:

- verify the place actually exists and is open to the public when relevant
- capture the best available official or map-backed name
- record coordinates or a stable map reference when the place is niche or easy to mis-pin
- if multiple branches exist, identify the intended branch explicitly

Weather adaptation rules:

- check destination weather before finalizing outdoor-heavy days
- if rain, wind, heat, or cold may materially change the experience, create a swap-ready indoor or lower-risk fallback
- move scenic outdoor windows to the best light / weather period when possible
- if the route depends on blossom, foliage, fireflies, beach, or night market conditions, state the seasonal uncertainty clearly

### 3) Pre-trip preparation

Include:

- weather-aware packing
- footwear
- rain / sun / thermal needs
- medications or small utilities if relevant
- digital prep
  - booking apps
  - map apps
  - ticketing

### 4) In-trip cautions

Include:

- crowd rhythm
- weather risks
- walking intensity
- reservation timing
- cash / mobile payment edge cases
- local etiquette or scenic-area constraints when relevant

### 5) Transport and lodging

Include:

- how to reach the destination from origin
- local transport strategy
- where to stay and why
- hotel selection logic
  - convenience
  - atmosphere
  - budget
  - access to morning / night scenes

### 6) Food and specialties

Include:

- what to eat on the route
- what is destination-specific
- what can be bought as take-home specialties
- rough per-item price bands where helpful

### 7) Budget

Budget should be structured by category:

- intercity transport
- local transport
- lodging
- tickets
- food and drinks
- buffer / extras
- souvenir allowance if relevant

Give a range, not a fake-precision exact number.

## 5. Output style rules

- plan for usefulness first, polish second
- compress without losing decision-making value
- keep the plan realistic by day length and transit burden
- do not overpack every day
- leave breathable gaps in at least some days
- every major recommendation should answer "why this place / meal / stop is worth the time"
- avoid itinerary lists that read like unordered POI dumps; the route should have logic

## 6. Planning heuristics that should survive compression

When the route is later compressed into webpage copy, preserve these decision signals whenever possible:

- why a place is included
- why the day order is structured that way
- where the main transport burdens are
- where weather or reservation risk could change the plan
- what can be skipped without hurting the trip
- what is especially suitable for the declared travel party

## 7. Hand-off to webpage production

Once the route guide is planned:

1. convert it into the route-guide structure used by the main skill
2. create the shot list
3. decide the music direction
4. move into the standard page workflow
