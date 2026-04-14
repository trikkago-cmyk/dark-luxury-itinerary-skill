[简体中文](./README.md)

![Dark Luxury Editorial Web Hero](./assets/screenshots/hero-desktop.png)

# Dark Luxury Editorial Web Skill

**What is it?**  
An all-in-one skill that turns trip requirements into a polished route guide and a shareable editorial travel page.  
One-line promise: give it your travel needs, get a beautiful itinerary site in one go.

**Product Screens**

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

## What Problems Does It Solve?

**Scenario: You have content, but the page still feels generic**  
Solution: structure, imagery, tags, music, and layout are aligned in one pass so it stops looking like a template.

**Scenario: You only have intent, not a route guide**  
Solution: input “from/to, days, mood, budget” and it builds the route guide before generating the page.

**Highlights**
- Foolproof: simple inputs generate both the route guide and a publishable site
- Beautiful: editorial magazine aesthetics with almost zero “AI UI” feel, plus built-in ambient music

**Who It’s For**
- Families planning trips who want it effortless but polished
- Independent travel agencies or small studios showcasing curated routes

## How Do I Use It?

1. Install `dist/dark-luxury-editorial-web-skill.skill`
2. Invoke the skill in Cursor and provide your trip requirements or existing guide
3. Generate and deploy the travel page

## What’s In This Repository?

- `dark-luxury-editorial-web-skill/`
  Full skill source

- `dark-luxury-editorial-web-skill/SKILL.md`
  Core workflow, guardrails, visual system, and QA rules

- `dark-luxury-editorial-web-skill/references/`
  Benchmarking, itinerary planning, writing guidance, implementation recipes, and media workflow references

- `dist/dark-luxury-editorial-web-skill.skill`
  Packaged installable artifact

## Common Ways To Use It

1. Install the `.skill` artifact and use it directly for new travel-web projects
2. Use `SKILL.md + references/` as your editable SOP baseline
3. Use it to calibrate your own travel-web agent so it stops producing template-looking pages

## Install Artifact

- `dist/dark-luxury-editorial-web-skill.skill`

## Repository Structure

```text
.
├── assets/
│   └── screenshots/
├── dark-luxury-editorial-web-skill/
│   ├── SKILL.md
│   ├── agents/
│   └── references/
└── dist/
    └── dark-luxury-editorial-web-skill.skill
```

## Current Version

- `v1.0.0`
