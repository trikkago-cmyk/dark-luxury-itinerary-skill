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

### Search template pack

Do not stop at one generic query like `杭州 两天一夜 攻略`.
Build a small query matrix and cover at least these buckets:

- official facts and access
  - `[destination] [season/date] 天气`
  - `[origin] 到 [destination] 高铁 / 飞机 / 自驾 多久`
  - `[place] 官网 开放时间 门票 预约`
  - `[place] 官方 名称 地址`
- route fit and travel style
  - `[destination] citywalk 慢节奏`
  - `[destination] 少折返 路线`
  - `[destination] 拍照 出片 最佳时段`
  - `[destination] 本地人推荐`
- pruning and anti-hype
  - `[destination] 避坑`
  - `[destination] 不推荐`
  - `[place] 值不值得去`
  - `[place] 排队 人多`
- weather and Plan B
  - `[destination] 雨天 替代`
  - `[destination] 室内 去处`
  - `[destination] 夜间 去处`
  - `[seasonal attraction] 几月 最好`
- food and lodging
  - `[destination] 本地小吃 推荐`
  - `[district] 杭帮菜 / 早饭 / 夜宵 推荐`
  - `[destination] 住哪里 方便`
  - `[destination] 哪个片区 少折返`

If Xiaohongshu or other public UGC is part of the mix, adapt the same buckets instead of free-searching at random.
Good default patterns are:

- `[destination] + [bucket keyword] + site:xiaohongshu.com`
- `[place] + [bucket keyword] + 小红书`
- `[destination] + [food / district] + 本地人推荐`

At minimum, the planner should cover:

- 1 official fact bucket
- 1 route-fit bucket
- 1 pruning bucket
- 1 weather / Plan B bucket
- 1 food or lodging bucket

### Required research record

When the user gives only a travel intent, the planner should leave an explicit research record before moving on to webpage polish.
For cold-start validation, this record is mandatory and should be output in the generated planning artifact or validation report.

Minimum template:

```md
## Research record

### Official / primary sources checked
- [source name] - what it verified
- [source name] - what it verified

### Stable web / map sources checked
- [source name] - what it verified
- [map product] - branch / entrance / transit / live-status check

### UGC query buckets used
- [query or bucket]
- [query or bucket]
- [query or bucket]

### Keep decisions
- [place]
  - keep because:
  - factual confidence:
  - recommendation confidence:

### Drop or demote decisions
- [place]
  - drop / backup because:
  - factual confidence:
  - recommendation confidence:
```

At minimum, the record must show:

- which official sources were actually checked
- which UGC keywords or buckets were actually used
- why each major stop stayed in the route
- why obvious alternatives were dropped, demoted, or held as backup

### Confidence ladder

Treat confidence as an execution rule, not a vague feeling.
Use two parallel checks:

- factual confidence
  - can I trust the fact itself
- recommendation confidence
  - even if the place is real, is it strong enough to deserve route time

#### Factual confidence

- High
  - official / primary source confirms it
  - or one stable source plus a map-backed live status clearly agree
- Medium
  - map-backed and repeated stable-web signals exist, but no direct official confirmation
  - acceptable for soft recommendations, but not for fragile time anchors without a caveat
- Low
  - only one UGC hit, stale mention, or conflicting sources
  - do not build the route around it

#### Recommendation confidence

- High
  - the place is real and reachable
  - it fits the declared trip style
  - the detour cost is low or clearly justified
  - at least two independent signals support its value
- Medium
  - the place is plausible and usable, but the fit is less universal, more seasonal, or slightly detoured
  - keep it as optional or mark the tradeoff
- Low
  - the place is mostly hype-driven, branch status is unclear, or the transit burden is too high for the payoff
  - move it to backup or drop it

Promotion rule:

- keep a stop in the main route only when factual confidence is at least `Medium`
  and recommendation confidence is at least `Medium`
- if factual confidence is `Low`, it cannot become a timed anchor
- if recommendation confidence is `Low`, it should not stay in the core route

### Default map stack and transit calibration

Use a default map stack so route quality does not depend on ad hoc tool choice.

For mainland-China destinations:

1. official venue / scenic / transport source
   - canonical name
   - opening status
   - ticket / reservation rules
2. Amap / Gaode
   - branch existence
   - entrance / exit reality
   - live operating markers
   - walking / taxi / transit estimates
3. Baidu Maps or Apple Maps as tie-breaker
   - only when Amap is ambiguous or a branch looks suspicious

For destinations outside mainland China:

1. official venue / scenic / transport source
2. Google Maps or the dominant local map product
3. OpenStreetMap or a secondary map only as cross-check

If map and official information still conflict:

- downgrade factual confidence
- do not let the disputed place anchor the day
- prefer a cleaner nearby alternative

Default thresholds for relaxed city trips:

- `<= 1.2 km` or `<= 18 min` flat walking
  - same cluster by default
- `1.2 km - 2.5 km` or `18 - 30 min` walking
  - same cluster only if the route itself is scenic and the weather is mild
  - otherwise prefer one light transit hop
- `> 2.5 km` or `> 30 min` walking
  - treat as a different cluster unless the payoff is unusually strong

Taxi / transit defaults:

- if the next stop is roughly `2 - 6 km` away and taxi is `<= 20 min`,
  while public transit requires a transfer or takes `> 30 min`,
  taxi is usually the cleaner choice unless the budget is very tight
- treat a hop as `heavy transit` if it needs `2+ transfers`,
  `> 35 min` total door-to-door, or obvious terrain / river / scenic-area entry friction
- cap heavy-transit hops at about `2` per day, ideally `1` per half day

Threshold adjustment rules:

- reduce comfortable walking thresholds by about `30%` for luggage,
  rain, heat, steep terrain, elders, or children
- if the trip style is explicitly `citywalk` or `slow stroll`,
  a scenic `20 - 25 min` walk can still count as a valid link
  when it improves the experience rather than merely filling distance

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

If the destination is food-relevant or the route includes meal planning, this section should be treated as default, not optional.

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
