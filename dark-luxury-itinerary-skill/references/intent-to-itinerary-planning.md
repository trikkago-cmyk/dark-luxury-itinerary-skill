# Intent To Itinerary Planning

Use this reference when the user does not already have a finished route guide and instead wants Codex to plan the trip from 0 to 1.

Typical prompts:

- “从武汉去西双版纳，做一个七天六夜的路书”
- “两个人清明去襄阳，帮我规划”
- “想从上海去杭州，做一个安静一点的两天微度假网页”

## 0. Planning operating model

Do not plan directly from destination keywords alone.
The stable planning pipeline is:

1. identify user profile and trip mode
2. choose the nearest planning template
3. retrieve information according to that template
4. validate, filter, and score the candidates
5. assemble the route and only then structure it into a shareable guide

The key idea is that `retrieval should follow the trip type`, not the other way around.
The same destination should be planned differently for:

- self-drive vs. flight / rail arrival
- staycation / vacation rhythm vs. special-forces high-density rhythm
- couple vs. family vs. elders vs. friends
- food-first vs. scenery-first vs. photo-first vs. mixed
- one-base trip vs. multi-hotel / moving-base trip

Treat the chosen template as a planning scaffold, not a visual template.

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

### Minimum viable inputs

At minimum, try to lock these down:

- destination
- trip length or date range
- travel party
- trip rhythm
  - staycation / relaxed
  - balanced
  - special-forces / high-density
- primary transport mode
  - self-drive
  - flight
  - high-speed rail / train
  - mixed

If possible, also capture at least one hard anchor:

- must-keep stop
- fixed reservation / event
- lodging district
- arrival / departure window

### Optional enrichers

These should improve the route, but should not block planning:

- exact flight / rail numbers
- hotel candidates
- must-eat / must-skip preferences
- budget split
- luggage, child, elder, accessibility constraints
- checklist items
- booking references

### Clarification budget

Ask at most `2` concise questions.
Only ask when a missing input would materially change the route shape, for example:

- self-drive vs. no self-drive
- domestic vs. international
- relaxed staycation vs. special-forces pace
- one-base stay vs. moving hotels

If the user is unavailable, infer conservatively and mark the assumption.

## 1.5. Template selection by user profile

Before searching, classify the trip into a working template.

### Core profile axes

- transport mode
  - self-drive
  - air / rail arrival + local taxi / transit
  - local walk-heavy
- rhythm
  - staycation / vacation
  - balanced
  - special-forces
- party
  - solo
  - couple
  - friends
  - family
  - elders-included
- lodging pattern
  - one-base
  - two-base or moving route
- priority bias
  - food
  - scenery
  - photography
  - culture
  - mixed

### Common planning templates

#### A. Self-drive loop

Best for:

- suburban / county / scenic-area routes
- multiple clusters in one or two days

Optimize for:

- parking reality
- clean loops instead of repeated returns
- rental / refuel / toll / night-drive burden
- scenic timing vs. driving fatigue

#### B. Flight / rail arrival hub-and-spoke

Best for:

- airport / station arrival into one main city base

Optimize for:

- station / airport transfer friction
- luggage handling
- arrival and departure day compression
- whether the user really needs a second cluster

#### C. Staycation / resort-centered

Best for:

- relaxed weekends
- resort / boutique hotel / thermal / lake / island stays

Optimize for:

- fewer POIs, better rhythm
- hotel-centered radius
- brunch / check-in / sunset / spa / café timing
- keeping breathing room instead of stuffing the day

#### D. Special-forces / high-density

Best for:

- short holidays with strong completion goals

Optimize for:

- opening-hour sequence
- first / last transport windows
- reservation timing
- queue avoidance
- realistic fatigue ceiling

#### E. Family / elders / low-burden

Best for:

- multigenerational travel
- stroller / luggage / low-mobility needs

Optimize for:

- shorter walks
- restroom and meal cadence
- predictable transfers
- fewer hard transitions per half day

Retrieval, filtering, and route scoring should follow the chosen template.

## 1.6. Template resolution rules

Do not treat template choice as decorative labeling.
Pick:

- one `primary template`
- one optional `overlay`

The primary template decides:

- retrieval buckets
- route scoring bias
- daily density
- which supporting sections deserve more weight

The overlay adjusts burden and pacing, but should not erase the primary logistics shape.

Use these default resolution rules:

- if the trip is self-drive and the route crosses `2+` suburban / scenic clusters,
  choose `A. Self-drive loop` as primary even when the rhythm is relaxed
- if arrival and departure are by flight or rail and most nights stay in one city base,
  choose `B. Flight / rail arrival hub-and-spoke` as primary unless the trip is clearly hotel-centered
- if the hotel / resort / lake / island stay is itself the trip's main reason,
  choose `C. Staycation / resort-centered` even if there is one arrival transfer day
- if the usable time window is short and the user has strong completion goals,
  choose `D. Special-forces / high-density` even when arriving by rail or plane
- if elders, children, stroller, low mobility, or heavy luggage meaningfully constrain movement,
  apply `E. Family / elders / low-burden` as primary or as an overlay that caps pacing

Conflict priority:

1. safety, physical burden, and mobility constraints
2. fixed transport / lodging structure
3. declared rhythm
4. interest bias

Default tie-breakers:

- `E` can overlay `A`, `B`, `C`, or `D`, and should slow them down rather than disappear
- `C` beats `B` when the one-base hotel radius is the point of the trip
- `B` beats `C` when airport / station friction clearly shapes the first and last day
- `D` can sharpen `A` or `B`, but should not override `E`

If the case is mixed, declare it explicitly, for example:

- `primary: B. Flight / rail arrival hub-and-spoke`
- `overlay: E. Family / elders / low-burden`

## 1.7. Template selection matrix

Use this quick matrix before retrieval:

- self-drive + multiple outer clusters + parking matters
  - prefer `A. Self-drive loop`
- air / rail arrival + one hotel base + city districts
  - prefer `B. Flight / rail arrival hub-and-spoke`
- relaxed weekend + one resort / lake / island / boutique-hotel radius
  - prefer `C. Staycation / resort-centered`
- short window + many must-hit POIs + explicit efficiency goal
  - prefer `D. Special-forces / high-density`
- elders / children / stroller / low-mobility constraints
  - prefer `E. Family / elders / low-burden` as primary or overlay

Useful fallback rules:

- if the user says "想多玩几个点" but also wants "松弛", resolve toward `balanced` unless the time window is objectively short
- if the user gives no rhythm preference, default to `balanced`, not `special-forces`
- if there is no hotel yet, default to one-base unless the geography strongly argues for moving hotels
- if the trip is only `1-2` days and the destination is spread out, ask whether the user wants `staycation` or `special-forces`; this is one of the few good clarifying questions

## 1.8. Planning artifact contract

Every 0-to-1 route-guide plan should produce a planning artifact before webpage polish.

That artifact must include:

- brief normalization
- `primary template`
- optional `overlay`
- key assumptions
- route topology label
- map validation summary
- weather adaptation summary
- day-shape reasoning
- section skeleton for the final guide

## 2. Research order

Use this order:

1. official and primary sources
2. map-backed truth layer
3. decision layer for food and lodging
4. stable current web sources
5. public UGC

Official and primary sources should be used first for:

- transport schedules
- opening hours
- ticket prices
- lodging policies
- weather or seasonal constraints

Map-backed truth sources should be used for:

- canonical place names
- coordinates, entrances, and branch disambiguation
- rough transport burden between anchors
- whether a hotel, restaurant, scenic spot, or station is actually where the route thinks it is

Decision-layer sources should be used for:

- restaurant or cafe price band
- whether a hotel or restaurant still looks actively operating
- recent rating drift or obvious service collapse
- comparing concrete candidates inside the same district

Good decision-layer defaults:

- public Meituan / Dianping pages when reachable
- OTA or booking pages for hotels
- official merchant pages when they exist

Public UGC can then refine:

- food picks
- walking rhythm
- photo spots
- queue or crowd heuristics
- what is actually worth skipping
- neighborhood feel

When researching a destination, actively search across multiple user intents instead of one generic query bucket:

- avoid坑 / 不推荐 / 真实体验
- 出片 / 拍照 / 最佳时段
- 本地人推荐 / 非游客向
- 亲子 / 长辈 / 情侣 / 朋友出游
- 雨天替代 / 夜间去处 / 临时 Plan B

Add template-specific search buckets based on the trip mode:

- self-drive
  - `[destination] 自驾 路线`
  - `[destination] 停车 方便吗`
  - `[destination] 租车 / 停车场 / 高速 / 环线`
- flight / rail arrival
  - `[station/airport] 到 [district] 怎么去`
  - `[destination] 住哪里 去景点方便`
  - `[destination] 行李寄存 / 接驳 / 打车`
- staycation
  - `[destination] 松弛 / 度假 / staycation`
  - `[destination] 酒店周边 适合散步`
  - `[destination] 日落 / brunch / cafe / spa`
- special-forces
  - `[destination] 一天 打卡`
  - `[destination] 开门时间 顺序`
  - `[destination] 排队 避坑`
- family / elders
  - `[destination] 亲子 / 长辈 适合`
  - `[destination] 步行累不累`
  - `[destination] 推车 / 老人 方便吗`

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

### Food and lodging recommendation contract

When recommending concrete places to eat or stay, do not rely on a single source family.

Use this layered rule:

- truth layer
  - map-backed existence and location
  - branch or district confirmation
  - official page when available
- decision layer
  - Meituan / Dianping / OTA / official merchant page
  - price band
  - active-business confidence
  - whether the detour cost is acceptable
- inspiration layer
  - Xiaohongshu or other public UGC
  - what is worth ordering
  - what the atmosphere feels like
  - what practical pitfall to expect

Promotion rule:

- a core restaurant or lodging pick should ideally have:
  - one truth-layer confirmation
  - one decision-layer confirmation
  - optional inspiration-layer support
- if only inspiration-layer evidence exists, keep it as a soft suggestion or backup

Output rule:

- the final page should show elegant recommendations
- the agent conversation can explain why the pick won
- the page itself should not read like a sourcing audit

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
- which official map-backed or venue-backed sources were actually checked
- which food / lodging decision-layer sources were actually checked
- which UGC keywords or buckets were actually used
- why each major stop stayed in the route
- why obvious alternatives were dropped, demoted, or held as backup
- what route topology was chosen and why it was acceptable
- how important hops were judged for detour or backtracking risk
- how weather affected order, timing, or Plan B
- which concrete meal or stay candidates were promoted, demoted, or left as backup

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

### Route topology and loop judgment

Do not stop at "the places look good individually".
Judge whether the order forms a usable route.

At minimum, check:

- does the day read as a clean loop, linear chain, or there-and-back
- how many distinct clusters the day crosses
- whether there is any obvious `A -> B -> A` foldback
- the longest single hop
- total driving or heavy-transit burden
- whether the most weather-sensitive or time-sensitive stop is placed correctly

Use these labels:

- `clean loop`
  - the order circles forward and returns naturally with little repeated corridor
- `clean chain`
  - the route moves one-way with low backtracking and is still efficient
- `there-and-back`
  - acceptable only when the anchor stop clearly justifies the return leg
- `backtracking-heavy`
  - route should usually be revised before it becomes the main recommendation

Default backtracking warning signs:

- repeating a corridor or district after already leaving it without a strong sunset / booking / night-scene reason
- the longest hop also sits in the middle of the day with no sequencing justification
- spending more than about `35%` of same-day transport on repeated return segments
- crossing the city or island boundary more than once in the same half day

If the trip is self-drive, taxi-heavy, or spans `3+` clusters in a day, the final route-guide should normally include a route-loop / map-summary module.

### Map validation contract

Do not freeze the route until map validation is complete.

For each core stop, record at least:

- canonical place name
- source used for map validation
- branch / entrance confirmation when relevant
- stable map reference or coordinates when available
- whether it is safe to use as a timed anchor

For each major hop, record at least:

- from
- to
- transport mode
- estimated duration
- whether it counts as heavy transit or heavy driving
- whether it introduces avoidable foldback or cross-city drag

Timed-anchor rule:

- a place should only become a timed anchor when it has adequate factual confidence
- if the map source is ambiguous, keep it as a soft recommendation or backup

### Map provider strategy

Preferred map providers depend on region, but map validation is mandatory regardless of tool availability.

For mainland-China destinations:

1. if a skill such as `skills.volces.com@amap-maps` is installed and usable, prefer it
2. if no map skill is available yet and installation is allowed, first try FineSkills / `skills` discovery and install
   - recommended discovery: `npx skills find amap maps`
   - recommended install: `npx skills add <repo-or-registry> --skill <skill-name> -g -y`
3. otherwise use Amap web or another stable mainland map product plus official venue pages
4. use Baidu Maps or Apple Maps only as cross-check when the primary map signal is ambiguous

For destinations outside mainland China:

1. if `tivojn/google-maps-api-skill@google-maps-api` is installed and a valid `GOOGLE_MAPS_API_KEY` is configured, prefer it
2. otherwise use Google Maps or the dominant local map product plus official venue pages
3. keep a manual fallback path rather than skipping map validation

If an external skill is unavailable or blocked:

- continue with manual map validation
- record the fallback in the research record
- do not downgrade the route into unsupported guesswork

### Template-specific scoring and sequencing

For every candidate stop, evaluate:

- factual confidence
- recommendation confidence
- route topology fit
- time-window fit
- burden cost
- party fit
- weather resilience

Then bias the decision using the active template.

#### A. Self-drive loop

Reward:

- a clean forward loop instead of repeated return corridors
- easy parking or drop-off reality
- scenic windows that align with daylight rather than exhaustion
- meal / restroom / refuel support around the longest hop

Penalize:

- city-core parking pain for low-payoff stops
- isolated detours that add long return driving
- mandatory night driving after the longest hop
- too many ticket gates, scenic shuttles, or checkpoints in one driving day

#### B. Flight / rail arrival hub-and-spoke

Reward:

- one-base efficiency
- luggage-friendly arrival and departure logic
- districts that combine transport convenience with night-food value
- full days that radiate outward once, not repeatedly

Penalize:

- unnecessary hotel swaps
- arrival day outer-suburb detours
- departure day long reverse-direction trips
- city-crossing with luggage only to chase one weak stop

#### C. Staycation / resort-centered

Reward:

- low hop count and hotel-centered walking / taxi radius
- long dwell time for brunch, café, sunset, spa, or lakeside / seaside wandering
- atmosphere-rich stops with low coordination cost

Penalize:

- pre-10 a.m. forced departures without a strong reason
- more than about `3` hard anchors in one day
- crossing town for one viral but low-conversion stop
- adding ticketed POIs merely to make the page look fuller

#### D. Special-forces / high-density

Reward:

- opening-hour sequencing
- reservation alignment
- queue avoidance
- same-direction cluster progression
- night windows that extend value instead of adding drag

Penalize:

- aimless scenic wandering in prime hours
- long sit-down meals that break the route
- impossible transfer stacks
- late-day fatigue cliffs with no bailout option

#### E. Family / elders / low-burden

Reward:

- short walks and predictable rest cadence
- shade, seating, restroom access, and stroller / elevator friendliness
- lower-uncertainty attractions and meal stops
- indoor backup options that are truly nearby

Penalize:

- stairs, steep terrain, and long queue exposure
- frequent hotel changes
- late meals after hard transfers
- overly dense old-town / scenic-area routing with no rest logic

### Template-specific day-shape heuristics

The route is not complete until each day has the right shape for the chosen template.

#### A. Self-drive loop

- target `2-4` anchors per day
- allow `1` heavy drive segment as normal; `2` is usually the ceiling
- place the most scenic / weather-sensitive stop before fatigue peaks
- try to land dinner near lodging rather than after the longest return hop

#### B. Flight / rail arrival hub-and-spoke

- arrival day: `1-2` light anchors at most
- full day: usually `2-3` clusters
- departure day: `1` light anchor or airport / station-side meal
- leave explicit departure buffer; do not spend it on a fragile detour

#### C. Staycation / resort-centered

- target `1-3` anchors per day
- protect `2-4` hours of breathable soft time
- treat check-in, tea, sunset, bath / spa, or quiet wandering as real anchors
- each day should feel slightly underfilled rather than optimized to the edge

#### D. Special-forces / high-density

- target `3-5` anchors per day, with `6` only when several are micro-stops in one cluster
- keep at most `2` heavy transfers in a day
- compress lunch if needed, but not hydration / recovery
- include one explicit bailout or skip candidate if the schedule slips

#### E. Family / elders / low-burden

- target `1-3` anchors per day
- keep one main outing per half day
- plan a rest, restroom, or seated food window every `2-3` hours
- surface indoor backup earlier, not as an afterthought

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

### Weather adaptation contract

Any route with meaningful outdoor exposure needs a weather record before finalization.

Record at least:

- weather source
- query date or forecast window
- whether the result is live forecast or seasonal fallback
- weather-sensitive blocks
- outdoor / indoor reorder decision
- Plan B trigger conditions

Decision rules:

- if the travel date is inside a usable forecast window, use forecast to decide outdoor / indoor order
- if the travel date is outside a usable forecast window, fall back to seasonal climate guidance and mark it explicitly as an assumption
- if rain, heat, wind, cold, blossom timing, beach timing, firefly timing, or night-scene timing matters, surface the uncertainty instead of hiding it

Provider strategy:

- first choice: forecast-capable skills such as `skills.volces.com@weather-openmeteo`
- if no weather skill is available yet and installation is allowed, first try FineSkills / `skills`
  - recommended discovery: `npx skills find weather`
  - recommended install: `npx skills add <repo-or-registry> --skill <skill-name> -g -y`
- fallback: lightweight tools such as `chandima/agent-skills@weather`
- if no external skill is usable, use official meteorology or stable forecast websites and document the fallback

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

Voice rule:

- the final webpage can keep the lived wisdom
- it should not sound like it is citing buckets, sources, or search templates to the reader
- when the user asks why something was arranged this way, the agent should explain in chat instead of adding a new visible rationale module to the page

## 4. Minimum route-guide schema

When the user wants a full route guide, the structured output should usually include all of the following:

### 1) Itinerary overview

Include:

- total days and nights
- overall route
- daily theme summary
- who the route suits

### 2) Route-loop / map-summary

Include this when:

- the trip is self-drive
- the route spans multiple geographic clusters
- the user would benefit from seeing whether the route is smooth or wasteful

Include:

- route type
  - clean loop / clean chain / there-and-back / backtracking-heavy
- major nodes in sequence
- total distance or total drive / heavy-transit burden
- longest hop
- cluster count
- one short route note
  - for example: why the route is efficient, or where the only acceptable detour is

For each node:

- canonical place name
- stable map reference or coordinates when the place is niche
- why the node exists in the route
- hop note from previous node

### 3) Daily itinerary

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

Every route-guide plan should also include a short weather adaptation summary:

- which blocks are weather-sensitive
- which ones were reordered because of forecast or seasonal assumptions
- what the default Plan B is

### 4) Pre-trip preparation

Include:

- weather-aware packing
- departure checklist
- footwear
- rain / sun / thermal needs
- medications or small utilities if relevant
- digital prep
  - booking apps
  - map apps
  - ticketing

Checklist rule:

- if the user provides checklist items, keep and group them
- otherwise generate a default checklist based on trip type
  - domestic
  - international
  - self-drive
  - family / elder

### 5) In-trip cautions

Include:

- crowd rhythm
- weather risks
- walking intensity
- reservation timing
- cash / mobile payment edge cases
- local etiquette or scenic-area constraints when relevant

### 6) Transport and lodging

Include:

- how to reach the destination from origin
- local transport strategy
- where to stay and why
- hotel selection logic
  - convenience
  - atmosphere
  - budget
  - access to morning / night scenes

Data-fidelity rule:

- never fabricate confirmed hotel names, room types, booking references, train numbers, or flight numbers
- if exact transport or lodging is unknown, provide strategy or area recommendations instead of fake precision

### 7) Food and specialties

Include:

- what to eat on the route
- what is destination-specific
- what can be bought as take-home specialties
- rough per-item price bands where helpful

If the destination is food-relevant or the route includes meal planning, this section should be treated as default, not optional.

### 8) Budget

Budget should be structured by category:

- intercity transport
- local transport
- lodging
- tickets
- food and drinks
- buffer / extras
- souvenir allowance if relevant

Give a range, not a fake-precision exact number.

### 9) Useful local info (conditional)

Include this when the trip is international, remote, self-drive-heavy, or likely to be shared as a practical guide.

Typical contents:

- timezone or time difference
- currency and common payment pattern
- voltage / plug when relevant
- local weather rhythm
- local ride-hailing / map / booking app hints

For low-friction domestic trips, compress this into a small practical note or omit it.

### 10) Emergency and support (conditional)

Include this when the trip is international, self-drive, remote, island-based, mountain-based, or otherwise logistics-sensitive.

Typical contents:

- local emergency number
- hospital / clinic or urgent-care hint when relevant
- consulate / embassy cue for international trips
- roadside / rental / ferry / weather alert note when relevant

Omit or compress for ordinary domestic city breaks when it adds little value.

## 4.5. Graceful degradation and omission rules

If input is incomplete, degrade the plan gracefully instead of inventing fake certainty.

- no confirmed intercity transport
  - provide access strategy and time range
  - do not invent train codes or flight numbers
- no confirmed hotel
  - recommend stay areas and why they fit the route
  - do not invent reservation details
- no detailed day-by-day asks
  - build day skeletons by morning / afternoon / evening anchors
- no exact budget split
  - provide category ranges and clearly label estimates
- no niche coordinates or stable map reference
  - keep the route textual; do not force pseudo-precise pins
- no user checklist
  - generate a default checklist based on domestic / international and trip mode

The planner should omit low-confidence sections rather than pad them with guesses.

## 5. Output style rules

- plan for usefulness first, polish second
- compress without losing decision-making value
- keep the plan realistic by day length and transit burden
- do not overpack every day
- leave breathable gaps in at least some days
- every major recommendation should answer "why this place / meal / stop is worth the time"
- avoid itinerary lists that read like unordered POI dumps; the route should have logic
- never fabricate booking references, confirmed prices, or exact schedules when the source does not support them

## 6. Planning heuristics that should survive compression

When the route is later compressed into webpage copy, preserve these decision signals whenever possible:

- why a place is included
- why the day order is structured that way
- why the route topology is acceptable and whether there is any intentional detour
- where the main transport burdens are
- where weather or reservation risk could change the plan
- what can be skipped without hurting the trip
- what is especially suitable for the declared travel party

## 7. Hand-off to webpage production

Once the route guide is planned:

1. convert it into the route-guide structure used by the main skill
2. decide whether the route-loop / map-summary should be a full section or a lighter day-level module
3. create the shot list
4. decide the music direction
5. deploy the finished validation site by default and verify the public URL in a browser
6. move into the standard page workflow
