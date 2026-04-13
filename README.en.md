[简体中文](./README.md)

# Dark Luxury Editorial Web Skill

Not for pasting travel notes onto a webpage.  
For turning travel material into a site people actually want to open, scroll through, listen to, and share.

It is built for a very familiar and very annoying situation:  
the source material is good, the taste is there, but the moment a generic generator touches it, the result becomes a dark background, a few paragraphs, a few mismatched images, and a Hero that does not belong to the screen below it.

## What Problem Does It Solve?

If you have ever tried to make a travel microsite, you have probably run into some version of this:

- the writing exists, but the page still has no cover-worthy presence
- the Hero and the second screen have a visible seam, so the illusion breaks on scroll
- the timeline, tags, and imagery exist, but they feel generic or semantically wrong
- desktop survives, but mobile exposes weak hierarchy and bad optical balance immediately
- music, asset sourcing, and font payload problems appear right before shipping

This skill is not just “one more page generator.”  
It turns those recurring failure points into explicit rules and a reusable workflow.

## When Would You Actually Use It?

### 1. You already have the guide, and you need a site that feels worth sharing

Maybe your input is:

- a Feishu doc
- a Notion page
- a Word / DOCX file
- a cleaned-up chat log

You do not just want to “put it online.”  
You want:

- a strong cover-led first screen
- a seamless transition into the second screen
- clear day structure without killing the mood
- something polished enough to send to friends without having to say “ignore the design”

### 2. You only have an intention, not a finished route guide

Maybe you only know:

- from where to where
- how many days
- what kind of mood you want
- roughly what budget you have

In that case, this skill is not only a presentation tool.  
It can help shape the route guide first, then turn it into a real editorial travel page.

### 3. You have a first-person memoir and do not want AI to sand your voice away

Many tools flatten memoir writing into something tidy, readable, and completely unlike the original author.  
This skill explicitly separates route-guide mode from memoir mode, so the structure can improve without erasing the voice.

### 4. You already have a half-finished site, but it still feels off

This is exactly the kind of cleanup it is good at:

- fixing Hero / second-screen seams
- simplifying heavy or awkward timelines
- correcting visual centering and hierarchy
- forcing tags and imagery back into semantic alignment
- making the music control feel integrated instead of bolted on
- keeping font choices from silently bloating the build

## How Does It Help?

Its workflow is simple, but practical:

1. It identifies whether your source is a travel intention, a route guide, or a first-person memoir
2. It structures the content before styling it: Hero, day flow, timeline nodes, place / food tags, transport, stay, prep, and budget all get normalized first
3. It writes the shot list before the polish pass, then sources imagery and atmosphere early instead of treating visuals like a last-minute patch
4. It checks the things that usually break the illusion: Hero transitions, timeline geometry, tag semantics, music state, mobile hierarchy, and font payload

## How Would You Actually Use It?

- Drop in a Feishu / Notion / Word / chat-based route guide and let it turn that into a travel site
- Give it only “from where to where, how many days, what mood, what budget” and let it build the route guide before the page
- Use it to rescue a half-finished travel microsite that still feels too generic
- Use it as the baseline workflow for your own travel-web agent

## Why Is It Better Than a Generic Page Generator?

Because it does not stop at “make it look premium.”  
It encodes the kinds of issues that come up in real travel projects and turns them into a working production system.

In practice, it behaves less like a page prompt and more like a travel-web producer who already knows where the project is most likely to go wrong.

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
