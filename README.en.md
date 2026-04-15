[简体中文](./README.md)

![Dark Luxury Itinerary Skill Hero](./assets/screenshots/hero-desktop.png)

# Dark Luxury Itinerary Skill

Have you ever had one of those moments?

You already did the hard part. The route is planned, the restaurants are picked, the hotel is decided, the notes are written. But the final thing you send out still feels like a rushed document dump. The information is there, but the feeling is gone.

Or maybe you only have the outline in your head: from where to where, how many days, what mood you want, roughly what budget you can accept. And the moment you realize you still need to build the route guide, source images, shape the page, and make it all look good, the energy drops immediately.

If that sounds familiar, this skill is for you.

It turns trip requirements, existing itineraries, and first-person travel memoirs into a travel page that actually feels worth sharing.

In one sentence: you tell it where the trip is going, and it turns that trip into a polished, editorial-style microsite.

What makes it easy to love is pretty simple:

- Foolproof: give it a travel brief, and it can generate both the route guide and the page
- Beautiful: editorial magazine aesthetics, almost zero AI-UI feel, and optional ambient background music
- Smarter planning: it does multi-angle search, checks information confidence, and sequences the route with maps and weather instead of just stitching together a few guides
- Better atmosphere: it matches images to specific sections and proactively suggests Pixabay-friendly music directions instead of leaving the page emotionally empty

Here is what it looks like in the wild.

## Real Outputs

These are real project outputs from the benchmark family and cold-start validation flow.

<table>
  <tr>
    <td align="center">
      <a href="https://dark-luxury-travel-itinerary.vercel.app">
        <img src="./assets/screenshots/xishuangbanna-hero-mobile.png" alt="Xishuangbanna route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Xishuangbanna Route Guide</strong>
      <br />
      Fuxian Lake · Xishuangbanna itinerary
    </td>
    <td align="center">
      <a href="https://wuhan-jingshan-travel-guide.vercel.app">
        <img src="./assets/screenshots/jingshan-route-mobile.png" alt="Jingshan route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Jingshan Route Guide</strong>
      <br />
      Wuhan · Jingshan itinerary
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://youji.travel-itinerary-jingshan.online">
        <img src="./assets/screenshots/jingshan-memoir-mobile.png" alt="Jingshan memoir mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Jingshan Memoir</strong>
      <br />
      Four-day memoir site
    </td>
    <td align="center">
      <a href="https://skill-solid-coldstart-routeguide-ag.vercel.app">
        <img src="./assets/screenshots/coldstart-hangzhou-mobile.png" alt="Cold-start Hangzhou route guide mobile screenshot" width="220" />
      </a>
      <br />
      <strong>Cold-start Validation</strong>
      <br />
      Hangzhou two-day route-guide test
    </td>
  </tr>
</table>

If you have ever built travel materials for yourself, your family, or a client, you probably know these small frustrations:

- the itinerary is finished, but what you share still looks like a long document
- you want it to feel premium, but all your time disappears into image hunting, layout tweaking, and mobile fixes
- you only wanted a route page people could actually read and forward, but it slowly turned into a template-looking site
- every new destination means rebuilding the same structure, prompts, and visual logic all over again

This skill exists to absorb that repeated work.

It helps align route structure, research record, information confidence, map logic, weather fallback, visual pacing, imagery, tag semantics, and music interaction first, then turns them into a travel site that is actually usable.

More concretely, the workflow is designed to be sturdier than “search a bit and make a page”:

- search from multiple angles, not one generic query
- separate official facts, map-backed checks, stable web results, and UGC signals
- use maps and weather to reduce backtracking and place outdoor scenes in better windows
- choose imagery by section-level scene targets, not random city vibes
- proactively recommend Pixabay music directions so the final page feels intentional, not unfinished

It is especially helpful for:

- family trip planning that should feel polished without becoming a design project
- independent travel agencies or small studios presenting curated routes
- memoir, diary, and guide writers who want their content to feel shareable instead of merely readable

## How To Start

No matter which app you use, the fastest setup is usually the same:

1. Open `dark-luxury-itinerary-skill/SKILL.md`
2. Put the core instructions into your app’s project rules, system prompt, or custom agent
3. Give it your travel brief and let it start generating

For example:

> Build a two-day travel route-guide site from Wuhan to Xiangyang, mobile-first, with an editorial look, automatic image sourcing, and a gentle ambient BGM.

If your tool supports direct skill import, you can also use:

- `dist/dark-luxury-itinerary-skill.skill`

## What’s In This Repository?

- `dark-luxury-itinerary-skill/`
  Full skill source

- `dark-luxury-itinerary-skill/SKILL.md`
  Core workflow, guardrails, visual system, and QA rules

- `dark-luxury-itinerary-skill/references/`
  Benchmarking, itinerary planning, writing guidance, implementation recipes, and media workflow references

- `dist/dark-luxury-itinerary-skill.skill`
  Packaged installable artifact

## Common Ways To Use It

1. Import the `.skill` artifact directly
2. Or use `SKILL.md + references/` as your reusable rule baseline
3. Then give it a travel brief and let it generate

## Install Artifact

- `dist/dark-luxury-itinerary-skill.skill`

## Repository Structure

```text
.
├── assets/
│   └── screenshots/
├── dark-luxury-itinerary-skill/
│   ├── SKILL.md
│   ├── agents/
│   └── references/
└── dist/
    └── dark-luxury-itinerary-skill.skill
```

## Current Version

- `v1.0.0`
