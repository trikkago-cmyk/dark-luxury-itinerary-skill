# Skill To Product Evolution

Use this reference when the user wants to evolve the travel-route skill into a front-end product.

The intended product arc is:

`intent -> route guide -> route-loop visualization -> trip-time check-in -> memoir`

This is not just a prettier route-guide generator.
It becomes a full journey system that supports:

- planning before departure
- guidance during the trip
- memory capture on the road
- memoir generation after the trip

## 1. Product definition

The simplest durable product framing is:

> a cinematic travel planning and memory companion that can plan the route, visualize whether the path makes sense, collect real moments on the road, and turn them into a shareable memoir

Three user phases:

1. `Plan`
   - decide where to go
   - generate route guide
   - understand whether the route is smooth or wasteful
2. `Trip`
   - check in at stops
   - upload photos
   - record a short feeling
   - adjust the plan in real time
3. `Memoir`
   - summarize the trip
   - choose highlights
   - publish a beautiful, structured travel story

## 2. What the current skill already does

The current skill is already strong at:

- converting raw travel text or intent into a structured route guide
- editorial visual design
- image and music sourcing
- mobile-first route-guide page output

Its weak spots, before productization, are usually:

- no user account or persistence
- no real-time trip state
- no check-in or memory capture
- no route execution feedback loop

## 3. Recommended evolution path

Do not jump directly from skill to full app.
Use three phases.

### Phase 1. Productized route-guide generator

Goal:

- make route-guide generation available from a front-end form, not only from skill invocation

Minimum features:

- trip brief form
  - origin
  - destination
  - days / nights
  - season or date
  - party type
  - budget
  - transport preference
  - tone preference
- research-driven itinerary generation
- route-loop / map-summary generation
- editorial webpage output
- manual export / publish

What to keep simple:

- no user-generated trip logs yet
- generated site can still be mostly static after creation

### Phase 2. Interactive trip companion

Goal:

- let the route guide stay useful while the user is actually traveling

Minimum features:

- trip dashboard with day-by-day route
- stop-level check-in
- upload photo at each stop
- write one short feeling, note, or warning
- mark reality vs plan
  - arrived
  - skipped
  - delayed
  - loved it
  - would skip next time
- append live memories without breaking the original route structure

Key UX rule:

- the logging interaction must be lighter than writing a full diary
- one tap + one image + one line is the right default

### Phase 3. Route guide to memoir

Goal:

- transform planning data plus real trip logs into a first-person memoir

Minimum features:

- summarize each day from:
  - original route
  - actual check-ins
  - uploaded photos
  - short feelings
- extract:
  - highlights
  - detours that were worth it
  - detours that were not worth it
  - favorite meals
  - final practical tips
- publish a memoir page in the same visual family as the route guide, but with more first-person narrative weight

## 4. Core product loop

### Plan loop

1. user submits a travel brief
2. research + planning engine builds structured route data
3. route-loop module checks whether order is smooth or backtracking-heavy
4. media layer proposes imagery and music
5. editorial renderer outputs the route-guide site

### Trip loop

1. user opens today’s route
2. taps a stop
3. checks in
4. uploads photo
5. records short feeling
6. system stores actual visit state and time

### Memoir loop

1. trip ends or user asks to summarize
2. system groups memories by day and beat
3. system rewrites into first-person narrative with light structure
4. user lightly edits if desired
5. memoir page is published

## 5. Recommended system roles

If this becomes an agent-backed product, the cleanest split is:

### Planner Agent

Responsible for:

- turning user intent into structured route data
- sequencing the days
- calculating whether the route logic is clean enough

### Research Agent

Responsible for:

- official-source lookup
- UGC synthesis
- weather and place validation
- confidence scoring

### Map / Topology Agent

Responsible for:

- place normalization
- coordinates or stable map references
- cluster detection
- loop vs backtracking judgment
- route-loop summary data

### Media Agent

Responsible for:

- image shot list
- Pixabay / other source selection
- music direction shortlist

### Memoir Agent

Responsible for:

- converting route + check-ins + photos + short feelings into day summaries
- preserving first-person tone

### Publishing Layer

Responsible for:

- rendering route guide page
- rendering memoir page
- keeping both in the same visual family

## 6. Data model that survives all phases

Do not make route-guide JSON too static.
Design it so the same structure can feed both planning and memoir generation.

Minimum durable entities:

### Trip

- trip id
- title
- origin
- destination
- dates or season
- party type
- budget tier
- transport preference
- tone

### Day

- day number
- title
- theme
- summary
- planned order rationale

### Stop

- stop id
- day id
- canonical name
- coordinates or stable map ref
- planned arrival window
- transport from previous stop
- why it is worth going
- map cluster id

### RouteLoop

- scope
  - whole trip or specific day
- route type
  - clean loop / clean chain / there-and-back / backtracking-heavy
- node order
- total distance
- total drive time or heavy-transit burden
- longest hop
- detour note

### CheckIn

- stop id
- actual timestamp
- status
  - arrived / skipped / delayed / changed
- note
- mood
- uploaded assets

### MemoryBeat

- derived from one or more check-ins
- day id
- beat label
- summary
- attached images
- memoir importance score

## 7. Route guide to memoir transformation rules

The memoir should not be generated from route text alone.
It should merge:

- the planned route
- actual visit order
- uploaded photos
- in-trip feelings
- skips and detours

Transformation rules:

1. keep the route as a structural spine
2. let real check-ins override planned timing
3. keep short feelings as tone anchors
4. compress repeated logistics unless they changed the emotional rhythm
5. promote standout photos and standout notes into memoir beats
6. keep practical lessons:
   - what was worth it
   - what was too rushed
   - what should be booked earlier
   - what food surprised the traveler

## 8. MVP recommendation

If building from 0 to 1, do not start with the memoir editor.

Best order:

1. front-end route-guide generator
2. route-loop visualization
3. stop-level check-in and photo upload
4. auto-generated daily summary
5. full memoir page generation

Why:

- route-guide generation proves the core value first
- route-loop improves route trust
- check-ins create real data
- memoir generation becomes much better once real data exists

## 9. Common product mistakes

Do not:

- make the route-loop section a decorative map that says nothing about efficiency
- force the user to write long diary text during the trip
- generate memoir prose with no grounding in actual check-ins
- split route guide and memoir into unrelated visual systems
- overbuild social or community features before the planning and memory loop is solid

## 10. Output expectations when using this reference

When the user asks for product planning, the output should usually include:

1. product definition
2. phase plan
3. core user flow
4. agent or backend responsibility split
5. minimal data model
6. MVP recommendation
7. clear next build step
