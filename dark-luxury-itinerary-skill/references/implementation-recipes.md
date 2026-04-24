# Implementation Recipes

Use these as starting patterns, not rigid templates. Keep the structure, then tune the numbers.

## 1. Page shell with blurred global background + clear Hero image

```tsx
<div className="fixed inset-0 z-[-1] bg-[#0a0f0c]">
  <img
    src={heroBackgroundImage}
    alt="Background"
    className="h-full w-full scale-110 object-cover opacity-30 blur-[30px]"
    referrerPolicy="no-referrer"
  />
  <div className="absolute inset-0 bg-[linear-gradient(180deg,rgba(10,15,12,0.3)_0%,rgba(10,15,12,0.7)_56%,rgba(10,15,12,0.95)_100%)]" />
</div>

<section className="relative flex min-h-screen items-center justify-center overflow-hidden">
  <div
    className="absolute inset-0 z-0"
    style={{
      maskImage: "linear-gradient(to bottom, black 60%, transparent 100%)",
      WebkitMaskImage: "linear-gradient(to bottom, black 60%, transparent 100%)"
    }}
  >
    <img
      src={heroBackgroundImage}
      alt="Hero"
      className="h-full w-full object-cover opacity-[0.82]"
      referrerPolicy="no-referrer"
    />
    <div className="absolute inset-0 bg-black/40" />
    <div className="absolute inset-x-0 bottom-0 h-80 bg-gradient-to-t from-[#0a0f0c]/80 to-transparent" />
  </div>

  <div className="relative z-20 mx-auto flex min-h-screen max-w-6xl items-center px-6 py-8 md:py-12">
    {/* hero content */}
  </div>
</section>

<main className="relative z-10">
  {/* transparent content over the same global background */}
</main>
```

Critical reading:

- the transition should come from shared imagery and masking, not from inserting an extra strip between sections
- leave real vertical breathing room before the second screen starts speaking
- if the second screen appears glued directly under the cover, increase spacing before adding decoration
- do not begin `main` with an opaque slab; the first content section should sit over the same blurred cover world
- if the page looks like a flat black / green background after the Hero, the two-layer composition has failed

## 2. Hero title with the dot as the optical axis

```tsx
<div className="mx-auto flex flex-col items-center">
  <div className="grid w-full grid-cols-[minmax(0,1fr)_auto_minmax(0,1fr)] items-center gap-x-3 text-[clamp(2.2rem,7vw,4.9rem)] font-serif font-medium leading-none tracking-[0.05em] text-white/95 sm:gap-x-5 md:gap-x-7">
    <span className="justify-self-end whitespace-nowrap pr-[0.04em] text-right tracking-[0.22em] sm:tracking-[0.26em] md:tracking-[0.32em]">
      抚仙湖
    </span>
    <span className="translate-y-[-0.05em] text-[0.72em] leading-none text-white/35">·</span>
    <span className="justify-self-start whitespace-nowrap text-left">西双版纳</span>
  </div>

  <div className="mt-8 grid w-full max-w-[24rem] grid-cols-[minmax(0,1fr)_auto_minmax(0,1fr)] items-center gap-x-4 text-sm tracking-[0.3em] text-white/72 md:text-base">
    <span className="justify-self-end text-right font-light">七天六晚</span>
    <span className="text-white/32">·</span>
    <span className="justify-self-start text-left font-light">漫游指南</span>
  </div>
</div>
```

If the left place name is shorter, widen the left-side tracking rather than shifting the dot.

Mobile guardrails:

- wrap the title in a shared width shell such as `w-[min(92vw,44rem)]`
- use `whitespace-nowrap` on each destination phrase when the phrase should not break internally
- reduce the clamp minimum or shorten the title before allowing isolated Chinese characters to wrap
- never let the browser split a destination into a vertical-looking pile of characters

## 3. Scroll hint and fixed music control that do not disturb Hero centering

```tsx
<motion.div
  style={{ opacity: opacityText }}
  className="absolute bottom-12 left-1/2 z-20 flex -translate-x-1/2 flex-col items-center gap-4 text-[10px] uppercase tracking-[0.34em] text-white/55"
>
  <span>Scroll to explore</span>
  <motion.div
    className="h-12 w-px bg-white/42"
    animate={{ y: [0, 8, 0], opacity: [0.72, 1, 0.72] }}
    transition={{ duration: 2.4, repeat: Infinity, ease: "easeInOut" }}
  />
</motion.div>

<div className="fixed right-4 top-4 z-40 flex items-center gap-3 border border-white/10 bg-black/18 px-3 py-2 backdrop-blur-md">
  <span className="text-[8px] uppercase tracking-[0.28em] text-white/38">Sound</span>
  <button type="button" className="text-[9px] uppercase tracking-[0.26em] text-white/58">
    Play
  </button>
</div>
```

The music control must stay fixed and subtle so the Hero layout never reflows.

Do not:

- add tool labels that make the player look like a widget
- let the player become visually louder than the Hero copy
- replace the compact benchmark-family vinyl object with a new capsule or pill component
- keep long helper text visible on mobile if it forces the player to dominate the lower corner

## 4. Inline editorial tags and itinerary pills

```tsx
<div className="mb-3 flex flex-wrap items-center gap-3 text-[1.02rem] tracking-[0.08em] text-white/84">
  <span className="font-serif font-medium">{event.name}</span>
  {event.tag && (
    <span className="inline-flex items-center border border-[#c6a37a]/25 px-2 py-0.5 text-[10px] uppercase tracking-[0.24em] text-[#c6a37a]">
      {event.tag}
    </span>
  )}
</div>

<span className="inline-flex items-center rounded-sm border border-white/6 bg-white/[0.03] px-2 py-1 text-[10px] tracking-[0.18em] text-[#bba28a]">
  <MapPin className="mr-1.5 h-3 w-3 opacity-70" />
  曼听公园
</span>
```

Use only restrained borders, small radii, and consistent icon sizing. Do not let pills become app-style chips.

## 5. Timeline layout with line segments between nodes only

```tsx
<motion.article
  initial={{ opacity: 0, y: 28 }}
  whileInView={{ opacity: 1, y: 0 }}
  viewport={{ once: true, margin: "-70px" }}
  transition={{ duration: 0.42, ease: "easeOut" }}
  className="group/event relative grid gap-y-3 sm:grid-cols-[7.25rem_1.5rem_minmax(0,1fr)] sm:gap-x-6"
>
  <div className="text-left text-[0.72rem] leading-none tabular-nums tracking-[0.14em] whitespace-nowrap text-white/34 sm:pt-[0.6rem] sm:text-right">
    {event.time}
  </div>

  <div className="relative hidden sm:block">
    {!isLast && (
      <div className="pointer-events-none absolute left-1/2 top-[1.48rem] bottom-[-2.2rem] w-px -translate-x-1/2 bg-gradient-to-b from-[#b59f84] via-[#8b806f] to-[#5d665a] opacity-72" />
    )}

    <div className="absolute left-1/2 top-[0.92rem] h-5 w-5 -translate-x-1/2 -translate-y-1/2 rounded-full bg-[#0a0f0c]" />

    <motion.div
      initial={{ opacity: 0, scale: 0.7 }}
      whileInView={{ opacity: 1, scale: 1 }}
      viewport={{ once: true, amount: 0.7 }}
      transition={{ duration: 0.34, ease: "easeOut", delay: 0.04 }}
      className="absolute left-1/2 top-[0.92rem] z-10 h-2.5 w-2.5 -translate-x-1/2 -translate-y-1/2 rounded-full border border-[#c8b396] bg-[#0a0f0c] transition duration-400 group-hover/event:border-[#e2c59e] group-hover/event:bg-[#d9b78d] group-hover/event:shadow-[0_0_18px_rgba(217,183,141,0.3)]"
    />
  </div>

  <div className={`relative flex-1 pb-9 sm:pb-10 ${isLast ? "pb-0" : "border-b border-white/[0.06]"}`}>
    {/* event content */}
  </div>
</motion.article>
```

## 6. Editorial route guidance block

```tsx
type RouteNode = {
  id: string
  label: string
  type: "start" | "scenic" | "food" | "stay" | "return"
  x: number
  y: number
  hopLabel?: string
  note: string
}

const routeNodes: RouteNode[] = [
  { id: "hotel", label: "市区酒店", type: "start", x: 10, y: 78, note: "从这里出发，避免早高峰后再折返" },
  { id: "longzhong", label: "古隆中", type: "scenic", x: 34, y: 22, hopLabel: "32 min", note: "白天历史景区，适合放在前半天" },
  { id: "tangcheng", label: "唐城", type: "scenic", x: 78, y: 34, hopLabel: "26 min", note: "傍晚切入夜游，顺接夜场表演" },
  { id: "dinner", label: "宜城菜馆", type: "food", x: 72, y: 76, hopLabel: "14 min", note: "夜游后就近吃饭，减少返程空驶" },
]

const [activeNodeId, setActiveNodeId] = useState(routeNodes[0].id)
const activeNode = routeNodes.find(node => node.id === activeNodeId) ?? routeNodes[0]

<section className="relative mx-auto max-w-6xl px-6 py-16 md:py-24">
  <div className="mb-8 flex items-end justify-between gap-6">
    <div>
      <p className="mb-3 text-[10px] uppercase tracking-[0.34em] text-white/40">Soft Route</p>
      <h2 className="font-serif text-2xl tracking-[0.16em] text-white/94 md:text-3xl">
        这一天这样走，会更顺
      </h2>
    </div>
    <div className="text-right text-[11px] tracking-[0.14em] text-white/48">
      <p>从市区慢慢绕进夜色</p>
      <p className="mt-1 text-white/68">约 58 km · 最长一段 32 min</p>
    </div>
  </div>

  <div className="grid gap-8 rounded-[1rem] border border-white/10 bg-black/16 p-5 backdrop-blur-md md:grid-cols-[minmax(0,1.35fr)_20rem] md:p-8">
    <div className="relative aspect-[16/10] overflow-hidden rounded-[0.9rem] border border-white/8 bg-[radial-gradient(circle_at_20%_20%,rgba(255,255,255,0.08),transparent_35%),linear-gradient(180deg,rgba(255,255,255,0.03),rgba(255,255,255,0.01))]">
      <svg viewBox="0 0 100 100" className="absolute inset-0 h-full w-full">
        <defs>
          <linearGradient id="routeStroke" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stopColor="rgba(208,191,164,0.88)" />
            <stop offset="100%" stopColor="rgba(116,137,115,0.72)" />
          </linearGradient>
        </defs>
        <path
          d="M 10 78 C 16 52, 24 34, 34 22 S 62 18, 78 34 S 84 66, 72 76"
          fill="none"
          stroke="url(#routeStroke)"
          strokeWidth="1.4"
          strokeLinecap="round"
          className="drop-shadow-[0_0_10px_rgba(208,191,164,0.28)]"
        />
      </svg>

      {routeNodes.map((node) => (
        <button
          key={node.id}
          type="button"
          onMouseEnter={() => setActiveNodeId(node.id)}
          onFocus={() => setActiveNodeId(node.id)}
          onClick={() => setActiveNodeId(node.id)}
          className="group absolute -translate-x-1/2 -translate-y-1/2"
          style={{ left: `${node.x}%`, top: `${node.y}%` }}
        >
          <span className="absolute inset-0 rounded-full bg-[#0a0f0c] blur-md" />
          <span className="relative block h-3.5 w-3.5 rounded-full border border-[#dbc3a0] bg-[#0a0f0c] transition duration-300 group-hover:bg-[#dbc3a0] group-focus-visible:bg-[#dbc3a0]" />
          <span className="mt-3 block whitespace-nowrap text-[10px] uppercase tracking-[0.22em] text-white/62">
            {node.label}
          </span>
        </button>
      ))}
    </div>

    <div className="rounded-[0.9rem] border border-white/8 bg-white/[0.03] p-5">
      <p className="text-[10px] uppercase tracking-[0.3em] text-white/38">Now Hovering</p>
      <h3 className="mt-4 font-serif text-xl tracking-[0.12em] text-white/92">{activeNode.label}</h3>
      {activeNode.hopLabel && (
        <p className="mt-2 text-[11px] tracking-[0.16em] text-[#cfb993]">{activeNode.hopLabel} from previous stop</p>
      )}
      <p className="mt-4 text-sm leading-7 text-white/60">{activeNode.note}</p>
    </div>
  </div>
</section>
```

Rules:

- use a schematic or stylized path, not a cluttered app screenshot
- node labels must stay sparse enough to avoid overlap
- the summary panel should explain route logic, not just repeat the place name
- mobile can stack the diagram and summary, but tap targets must remain usable
- if this section starts reading like an operations panel, strip it back to a lighter overview treatment
- prefer visible titles such as `怎么走更顺` or `这一天这样排` over hard technical labels
- never render raw planning labels such as `THERE-AND-BACK`, `CLEAN LOOP`, `route topology`, or `backtracking-heavy`
- show start / finish and route direction with subtle labels or arrows when the path is not obvious
- if the right-side panel becomes a list of metrics, replace it with one warm sentence about why the route is comfortable
- if the diagram cannot meet the benchmark family's polish, omit it and keep only a short route note
- if support information around this section starts multiplying into several neighboring boxes, merge it into one calmer editorial block instead

Use this block only when the route genuinely benefits from explanation.
For a simple citywalk or one-cluster staycation, fold the guidance back into overview + daily text instead of forcing a standalone section.

## 7. Small-radius image surface with subtle parallax

```tsx
<div className="group/img relative aspect-[5/6] w-full max-w-[22rem] overflow-hidden rounded-[0.95rem] border border-white/10 bg-black/30 shadow-[0_28px_90px_rgba(0,0,0,0.42)]">
  <div className="absolute inset-0 z-10 bg-gradient-to-t from-black/25 via-transparent to-white/5 transition duration-700 group-hover/img:from-black/10" />
  <motion.img
    style={{ y, scale }}
    src={src}
    alt={alt}
    className="absolute inset-0 h-full w-full object-cover transition duration-1000 ease-out group-hover/img:scale-[1.04]"
  />
</div>
```

Fill the frame completely. Large empty inner margins usually mean the crop container or image sizing is wrong.

## 8. Minimal editorial surface rules

```tsx
const sectionTitleClassName =
  "text-white/95 text-xl md:text-2xl font-serif font-semibold tracking-[0.16em] mb-16 md:mb-20 text-center";

const ghostNumberClassName =
  "absolute top-24 left-6 text-[8rem] font-serif font-thin text-white/5 select-none pointer-events-none leading-none -translate-y-1/2";
```

## 9. Ambient audio engine notes

Use one of these two paths:

1. Licensed or user-provided file
2. Generated ambient score with Web Audio or a royalty-free fallback

Rules:
- no autoplay
- fade in and fade out
- fixed control
- never block the page if audio fails
- do not ship a copyrighted track without a real license or user-provided file

## 10. Practical tuning notes

- If the transition still shows a seam, remove layers before adding layers.
- If the Hero looks muddy, the clear image is too dim or accidentally blurred.
- If the page feels fragmented, unify spacing and background logic first.
- If the page feels generic, tighten typography and remove chrome before inventing new effects.
- If the page feels wrong after a rename, check whether metadata, project slug, and public alias all moved together.
- If a day image feels off, fix the shot list before continuing to polish the UI.

## 11. Font delivery recipes for Vite travel pages

The fastest way to accidentally bloat a cold-start build is to import full CJK font packages in multiple weights.

### Safe default

```css
:root {
  font-family: "Manrope", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
}

.font-serif-editorial {
  font-family: "Songti SC", "STSong", "Noto Serif CJK SC", serif;
}
```

This keeps Chinese rendering mostly on system fonts and avoids shipping huge font payloads by default.

### Use a webfont only when it materially changes the page

If you need a custom serif feel, prefer one of these:

1. one Latin display font plus system Chinese serif fallback
2. one subsetted Chinese serif weight used only for headings

Do not default to:

- importing `400 + 500 + 700` CJK packages without checking output
- importing `@fontsource` full CJK families by habit in small Vite travel pages
- using a package that emits dozens of unicode-range font files unless you verified the tradeoff

### Post-build font audit

After adding fonts, inspect:

1. `dist/assets` file count
2. emitted `woff` / `woff2` count
3. CSS bundle size
4. whether fonts now dominate the build more than imagery or app code

If you see a large fan-out of font files, simplify immediately:

1. drop unused weights
2. revert body copy to system sans
3. revert headings to system Chinese serif
4. only keep a custom display font where it visibly matters
