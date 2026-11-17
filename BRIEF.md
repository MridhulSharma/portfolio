# Build brief — Mridhul Sharma portfolio

**Read this before writing any Phase 1 code.** It is the whole spec. If something
here conflicts with a habit or a default, this document wins.

Where it is silent, **invent** — the owner has asked for no creativity constraints
beyond what is written here, and everything specified is a minimum rather than a
description of the finished site. Ask a question only when inventing would risk
one of the non-negotiables in §3, or when the answer is a fact about the owner
you cannot know.

Status at handoff: **Phase 0 complete.** Pit lane ships. Hero cutouts and the
Volta loop are encoded and production-ready in `hero/` and `media/` (§4c). The
hero reveal is specified down to the composite order (§4d). No 3D exists yet.

---

## 1. What this repo is

A personal portfolio for a senior CS undergraduate applying to Software
Engineering, Frontend, AI Engineer and AI/ML Systems Engineer roles.

It has **two modes, both first-class**:

| Mode | What it is | Status |
| --- | --- | --- |
| **Pit lane** | Fast, typographic, zero-JS reading mode. All five case studies as text. | **Done.** `index.html` |
| **Race mode** | One continuous WebGL scene, scroll-driven, five themed sectors. | Phase 1+ |

Pit lane is not a fallback. A hiring manager at an AI lab will read it and leave
without ever seeing the canvas, and that is a success, not a failure. **Race mode
must never regress pit lane.** Keep the route, keep it under a second, keep it
complete.

---

## 2. The concept

**One lap, five sectors.** The site is a single continuous track; scrolling drives
one lap. Each sector is a themed world, each world holds one project, and the
boundary between sectors is a transition inside one scene — never a page load.

| # | Sector | Theme | Carries | What the sector shows |
| --- | --- | --- | --- | --- |
| 1 | **The Grid** | Formula 1, the circuit itself | Volta | Gameplay footage on a pit-wall monitor, over original light geometry — a track ribbon and horizon, suggestive, not a simulator |
| 2 | **The City** | Travel and movement, read from above | Signum | `signums3.png` on an operator console, **plus the one interactive moment**: a scripted refusal, the 558 km² polygon meeting the 12 km² cap |
| 3 | **The Street** | Place — Boston parcels | Donna | `donna.png` on an angled desk display, plus a prominent link to the live app |
| 4 | **The Café** | The slow sector — warmth, rest | Decibels | A scripted caption replay in DOM text, then the honest scorecard |
| 5 | **The Desk** | The laptop; running cadence as the site's pace | Flosstime + credo | A short scripted sequence of a double-booking resolving — the only project with nothing public to link |

### Evidence, not re-implementation

**Read this twice. It is the rule that keeps the build finishable.**

No sector re-implements its project. A cut-down version of a working project is
a *downgrade* presented as a highlight: it undersells the original and costs more
to build than it returns. The projects are evidence — numbers, captured media,
repo links. **The portfolio itself is the demo**; its scroll, shaders and
transitions are what prove frontend ability.

So:

- **Captured video under a custom shader treatment**, not live systems. Video as
  a WebGL texture with a unifying fragment overlay (grain, scanline, dither) is
  the technique — it makes five different projects read as one site, and it is a
  fraction of the cost of rebuilding any of them.
- **No webcam, no microphone, no phone calls, no model API calls, no backend.**
  The site is static. Decibels in particular must never be able to place a call.
- **Scripted sequences, not running products.** Fixed data, a state machine, a
  timeline. This is what Stageshow is for.
- **Link the real thing** wherever one exists: Donna is a deployed app, the repos
  are public.
- **Captures live on screens that are objects in the scene** (§4b.F), never on
  frosted-glass UI cards.
- The Volta circuit and car models **do not get ported.** Build light original
  geometry that reads as a track. This is why the asset budget is achievable.

**The single exception** is the Signum refusal in Sector 2: a scripted state
machine over fixed data, no pipeline, no model calls. It is kept because it is
the only place a visitor *feels* the engineering thesis instead of reading it.
One interactive moment is memorable; five is a theme park. If the owner decides
against it, it becomes a ~15-second scripted animation and nothing else changes.
**Decided: it stays interactive.**

**Running** is not a sector. It is the pace layer under all five: the cadence the
camera moves at, the rhythm text reveals on, and an elevation profile as the
scroll indicator. **Travel** is not a sector either — it is what the four
transitions are made of.

Transitions, in order:

1. Grid → City: camera lifts off the track into the city grid
2. City → Street: the city descends to street level; fleets become parcels
3. Street → Café: step indoors — light warms, motion slows, audio enters
4. Café → Desk: the café table becomes the desk; the screen fills the frame

---

## 3. Non-negotiables

**These are floors, not ceilings.** Everything in this document is a minimum bar
and a set of guardrails — it is not a description of the finished site, and it is
not a limit on ambition. The owner's instruction is explicit: no creativity
constraints beyond these. Where this brief is silent, invent. Where it specifies
a shader, a form or a transition, treat that as the least the sector should do,
and go further if the result is better and the budget holds.

The rules below exist because breaking one damages the site in a way more
ambition cannot repay. Breaking one is a bug, not a trade-off.

1. **One idea, held.** 2026 award winners commit to a single visual concept.
   Five unrelated set pieces stitched together reads as a showreel. Resist adding
   an effect because it is impressive in isolation.
2. **One signal colour.** `--signal` marks the single most important thing in a
   view. It is never decorative. If everything is accented, nothing is.
3. **One grade over everything.** A single post-processing grade across all five
   sectors is what makes different worlds read as one site.
4. **One *hero* moment per sector.** A sector with three hero moments has none.
   Supporting detail, ambient 3D and micro-interaction are unlimited — this caps
   what competes for attention, not how much craft goes in.
5. **The line never breaks** (§4b.A). If a change would cut it, the change is
   wrong.
6. **The Café sector is the only inversion.** It is there so the eye can rest. Do
   not make it loud for symmetry.
7. **Content is fixed.** Every number, sentence and claim in `index.html` is
   verified and belongs to the owner. Port it; do not rewrite, embellish, or
   generate new copy. Never invent a metric.
8. **Reduced motion is built alongside, not after.**
9. **No library's default look.** Tokens in `assets/css/tokens.css` are the
   system. Do not import a component library's theme on top.

---

## 4. Art direction

**Direction: "Telemetry."** The visual language of instrumentation, not racing
pastiche. Timing screens, split times, data overlays. Precise mono numerals,
hairline rules, a dark field, exactly one signal colour. No chrome, no carbon
fibre texture, no checkered flags, no speed-blur clichés.

### Colour
Defined in `assets/css/tokens.css`. Do not add colours; add sector themes by
overriding `--field-*`, `--ink-*` and `--signal` on `[data-sector]`.

- Field: `#0a0b0d` base, `#121418` raised, `#1a1d23` high, `#060708` inset
- Ink: `#f2f3f5` / `#9aa0aa` / `#636a75`
- Line: `#23272e` hairline, `#343a44` strong
- Signal: `#ff4d1c` (hot instrument orange — brake glow, warning lamp, split delta)
- Café inversion: `#f4ece1` field, `#191411` ink, `#b4542a` signal

### Type
- Display/body: **Archivo** variable (`wdth 75..125, wght 400..700`). The width
  axis does the timing-tower work — use it, sparingly, at display sizes.
- Mono: **JetBrains Mono**. All numerals, metadata, labels. `tabular-nums`
  everywhere a number could change.
- Phase 1: self-host woff2 subsets and drop the Google Fonts link.

### Layout
- 12-column grid, `--gutter` fluid, `--page-max` 1440px
- Prose measure 68ch, never wider
- Desktop: sticky left rail (`--rail-w` 13rem) as a timing tower
- Vertical rhythm on the 4px space scale only

### Motion
Match these exactly — the CSS and the JS must agree:

```js
gsap.defaults({ ease: "power3.out", duration: 0.85 });
gsap.ticker.lagSmoothing(0);

new Lenis({ lerp: 0.08, wheelMultiplier: 0.9, smoothWheel: true, anchors: true });
```

Lenis drives its `raf` **from the GSAP ticker**, and `lenis.on('scroll',
ScrollTrigger.update)`. One clock for DOM, scroll and the render loop. Never two
RAF loops.

Durations: `--dur-tap` 120ms, `--dur-quick` 240ms, `--dur-base` 480ms,
`--dur-slow` 900ms. Easing: `--ease-out` for entries, `--ease-in-out` for
reversible state, `--ease-entry` for first paint.

---

## 4b. THE VISUAL LAYER

This section is the art direction the rest of the brief protects. It is the part
that decides whether the site is striking or merely tasteful. Build it with real
shader work — TSL node material and custom passes, not stock effects bolted on.

### A. The signature: the line never breaks

**One continuous luminous stroke enters at the top of the page and does not break
once for the entire scroll.** It is the single idea a visitor repeats to someone
else, and it is the structural answer to "five sectors read as a showreel."

| Sector | What the line is |
| --- | --- |
| 1 Grid | The racing line through the circuit, banked, in perspective |
| 2 City | The arterial road across the city plane, seen from above |
| 3 Street | A parcel boundary — orthogonal, right-angled, surveyed |
| 4 Café | Steam curling off a cup, rising and dissipating |
| 5 Desk | The trace across the schedule grid, like a telemetry readout |

**Implementation.** One `CatmullRomCurve3` of 64 control points, rendered as a
tube or a screen-space SDF ribbon with a custom TSL material, emissive so the
bloom pass picks it up. One draw call, alive for the whole page.

The curve is **never re-instantiated**. Each sector defines a 64-point pose, and
transitions lerp control-point positions under ScrollTrigger scrub. Rebuilding
the geometry would break the line, which is the one thing it must not do.

Uniforms: `uProgress`, `uTension` (0 smooth → 1 angular, this is what turns a
racing line into a parcel boundary), `uThickness`, `uGlow`, `uDashOffset`,
`uVelocity` (fed from Lenis, drives stretch and glow on fast scroll).

Reduced motion: the line renders in its sector pose and does not morph; poses
cross-fade instead. It is decorative — `aria-hidden`, with no information
carried by it alone.

### B. The grade — one pass over everything

A single `PostProcessing` node graph applied once, to 3D and video alike. **This
is what makes five different worlds read as one site**, and it is what hides
video compression artifacts and gradient banding under a shared noise floor.

Chain, in order:

1. Scene pass
2. **Bloom** — threshold ~0.78, strength per sector
3. **Chromatic aberration** — radial, ~0.0008 base, scaling with scroll velocity
4. **Ordered dither** — Bayer 8×8, low amplitude. Quietly the most important one:
   it is the texture that unifies video and geometry
5. **Film grain** — `film()` from `three/addons/tsl/display/FilmNode.js`, or a
   custom node if you want the grain to respond to velocity
6. **Vignette**, then tone map, then output

Per sector the grade changes **only three uniforms**: `uBloomStrength`,
`uGrainAmount`, `uTint`. Do not add passes per sector.

### C. Per-sector 3D and shader programme

Mood shifts are carried by light, material and grain — not by changing the
system. Almost nothing here is a downloaded model; it is geometry from code,
which is how the asset budget is met.

| Sector | Mood | 3D elements | Shader work |
| --- | --- | --- | --- |
| **1 Grid** | Cold, high contrast, speed | Extruded track ribbon, horizon plane, instrument forms (rings, gauges), drifting dust | Velocity-driven stretch on line and type; heat-haze refraction above the asphalt; anisotropic metal |
| **2 City** | Aerial, ordered, data | ~2,000 instanced blocks from a noise field (one draw call), advisory wavefront plane, the class-cap disc | Radial propagation shader for the advisory; a hard clip of the polygon against the cap radius — **the refusal is a shader, and you can see it happen** |
| **3 Street** | Daylight, material, surveyed | Parcel plane with displacement, pin marker, instanced comparables, a volumetric confidence band | Cadastral SDF line work; the interquartile range as a translucent band with soft edges; dithered gradient sky |
| **4 Café** | Warm, slow, tactile — **the inversion** | Cup form, table plane, curl-noise steam particles, a soft light volume | The only sector with soft shadows and depth of field. Subsurface-ish scatter. Grain up, bloom down, aberration near zero |
| **5 Desk** | Precise, close, nocturnal | Laptop form, screen plane, schedule grid, cursor markers | CRT phosphor and scanline on the screen plane; the grid as an SDF with conflict cells glowing in `--signal` |

### D. The four transitions, shot by shot

Each runs over roughly 100vh of **scrubbed** scroll, not a timed tween.
Percentages are of that distance. Overlap them — a transition where every change
starts and ends together reads mechanical.

**T1 · Grid → City — the lift**
- 0–25% camera pitches from chase to overhead, FOV 55 → 38
- 25–60% track ribbon dissolves on a rising dither threshold
- 30–80% city instances scale from zero on a noise-ordered stagger
- 50–100% line lerps to the arterial pose; tint cold → neutral; bloom 1.0 → 0.7
- Type: Sector 1 title exits on a SplitText mask-up; Sector 2 title enters on the
  Archivo width axis expanding 75 → 112

**T2 · City → Street — the descent**
- Altitude drops, FOV 38 → 52; city instances fall below the parcel plane
- `uTension` 0 → 1: the line goes from smooth curve to right angles. This is the
  single most satisfying beat on the site — make it land late, around 60–90%
- Grain +20%; the first daylight enters

**T3 · Street → Café — the inversion.** The hardest and the best.
- Field and ink tokens cross-fade **through a uniform, not a class swap**, so the
  flip is continuous rather than a flash. Over the full 100vh.
- Bloom down, depth of field in, grain up, scanline off, aberration to near zero
- The line rises vertical and begins to curl
- Audio, if there is any, enters here and nowhere else

**T4 · Café → Desk — the close**
- Camera dollies in; cup exits frame left; the screen plane rises to fill
- Phosphor shader fades in over the last 30%
- The line flattens into a horizontal trace and meets the schedule grid

### E. References to study before writing shaders

Open these and look at them. Do not copy; calibrate.

- [Stefan Vitasović's portfolio](https://tympanus.net/codrops/2025/03/05/case-study-stefan-vitasovic-portfolio-2025/)
  — video as WebGL texture with a unifying fragment overlay. **The core technique
  for this site.**
- [Shader.se's scroll-driven WebGPU pipeline](https://tympanus.net/codrops/2026/05/19/80s-business-tech-and-seamless-scene-transitions-inside-shader-ses-scroll-driven-webgpu-pipeline/)
  — selective scene rendering and seamless scene transitions in R3F
- [Sketching the Impossible](https://tympanus.net/codrops/2026/06/11/sketching-the-impossible-a-3d-portfolio-built-without-a-single-3d-model/)
  — an award-winning 3D world built entirely from flat geometry and shaders
- [More Than a Portfolio](https://tympanus.net/codrops/2026/04/28/more-than-a-portfolio-building-a-scroll-driven-3d-world-with-something-to-say/)
  — scroll-driven 3D where each technical decision serves a message
- [HAOQI.DESIGN](https://tympanus.net/codrops/2026/08/15/inside-haoqi-design-letting-dom-and-webgl-share-a-retro-futurist-stage/)
  — DOM and WebGL sharing one stage, glass shaders, scroll sync

### F. The screens — how projects appear

Projects appear on **screens that are objects in the scene**, not on UI cards
floating over it. A console, an angled desk display, a pit-wall monitor, a laptop.
The capture lives inside the object and stays pin-sharp.

**Explicitly not frosted-glass cards.** Glass-card grids are the default output of
every prompt-built portfolio in 2026 and will date within a year — and the site's
whole thesis is that it was not generated. Refraction, thickness and caustics go
on the **bezel, the edge, the housing**. Never over the content: the Signum
capture carries `SIGNATURE: verified` and `TIME TO ADVISORY 2.8s` in small type,
and blurring those throws away the best asset on the site.

What a screen object does: catches light and tilts as you scroll; the glass edge
refracts the sector behind it; the panel emits enough to register in the bloom
pass; the capture itself gets only the shared dither and grain, nothing more.

### G. The hero

**Recommended, and what to build unless the owner says otherwise:** a
brush-reveal over the owner's portrait that uncovers **the pose skeleton** — 33
MediaPipe landmarks, joints green when clean and red when flagged, exactly as
Volta renders them.

The mechanic is an SDF brush accumulating into a mask texture; layer A is the
portrait, layer B is the landmark overlay. It is personal, it is instrumentation
rather than costume, and it is a direct callback to a system the owner built —
the hero says "I built the thing that is looking at me."

Requirements:

- The name sits in the background plate at display size, Archivo wide, partially
  occluded by the portrait. The line (§4b.A) enters through this composition.
- **Touch fallback is mandatory**: hover does not exist on half of visitors.
  Drag to paint, plus a slow automatic sweep after ~2s of no input.
- Reduced motion: show the revealed state, no brush.
- The portraits are **already cut out with real alpha** and registered to a
  shared frame (§4c). Composite onto the dark field; nothing more to prepare.
- Full mechanics, including the composite order and five mandatory corrections:
  **§4d**.

Alternatives the owner floated, recorded so they are not re-litigated: revealing
a racing-driver image instead of the skeleton (rejected — it ends by replacing
the owner's face with an anonymous figure and says only "I like F1"), and no
portrait at all (viable: name at display size, the line entering, first metric
above the fold).

---

## 4c. Asset inventory

### Production-ready — use these, do not re-derive them

| File | Spec | Use |
| --- | --- | --- |
| `hero/me.webp` · `hero/suit.webp` | 1200×1777, real alpha, cut with a human-segmentation model + alpha matting. **Both cropped to one shared frame**, so the subject is pixel-registered between them | Hero reveal, §4d. PNG lossless copies sit beside them |
| `media/volta.av1.mp4` · `media/volta.h264.mp4` | 12.0 s, 1024×576, no audio, **seamless 0.5 s crossfade loop**. 1.9 MB / 1.8 MB, from a 65 MB source | Sector 1's screen |
| `media/volta.poster.jpg` | 1024 wide, frame at 0:10 | Poster for the above |

The hero cutouts have one limitation that is in the source images, not the
cutout: the helmet is larger than the subject's head and the suit figure's
shoulders are broader, so the silhouettes do not match. The reveal reads as
"becomes a driver" rather than "changes clothes." Accept it or regenerate the
sources at matching build and framing. **Do not** scale one to fit the other —
that breaks registration, which is the thing holding the effect together.

The Volta footage has a known weakness: the webcam picture-in-picture is black
for the whole capture, so the pose skeleton — the actual achievement — never
appears. If a re-record arrives with the camera feed live, re-cut to the same
spec and replace.

### Raw sources in `pics/`

| File | What it is | Use |
| --- | --- | --- |
| `signums3.png` | **The best asset on the site.** Signum's operator console — photoreal Austin, red KEEP_CLEAR polygons, the agent pipeline rail, the advisory card with signature verified and 2.8 s to advisory | Sector 2's screen. Build the sector around it |
| `signumpage.png` | Signum landing page | Secondary at most |
| `donna.png` | Donna's product UI — clean, dark, legible | Sector 3's screen |
| `volta.mp4` | 65 MB raw capture. Already encoded above; keep out of git | Source only |
| `volta.png` | The Volta **landing page**, not gameplay | Unused. A screenshot of a website inside a website proves nothing |
| `me2.jpg`, `suit2.jpg` | Raw portraits, white background | Already cut out above |
| `flosstime.jpg` | A photo of the company's treatment room | **Do not use.** It shows nothing the owner built, and may be the company's own marketing image |

Flosstime has no screenshot and will not get one — it is internal. That is
exactly why it keeps a built moment: the scripted schedule grid with two cursors
and a double-booking resolving.

Decibels' capture is still to come from the owner.

Add `pics/*.mp4` to `.gitignore`. The raw capture should never enter git history.

Any further video follows the same recipe: cut to ~12 s, scale to 1024 wide,
strip audio, wrap the tail into the head with a 0.5 s crossfade so it loops
without a seam, then encode AV1 (`libsvtav1 -crf 41 -preset 6`) and H.264
(`libx264 -crf 29 -preset slow`), both `-g 120 -pix_fmt yuv420p -movflags
+faststart`, plus a poster frame.

---

## 4d. The hero reveal — implementation spec

A hard-edged paint trail follows the pointer. Inside the trail the front image
is **erased** and the back image shows through. Stamps hold briefly at full size
then shrink out of existence, so the trail clears about 1.1 s after the pointer
stops. It is not a permanent wipe.

Per §4b.G the recommended back layer is the **pose skeleton** over the portrait.
The mechanics below are identical whichever back layer is chosen.

### Architecture

Three canvases: the visible one, an offscreen `mask` (the trail as an alpha
shape), and an offscreen `buf` (the back image clipped to that shape). Size all
three to `round(W*dpr) × round(H*dpr)`, `dpr = min(devicePixelRatio, 2)`, on load
and on resize.

The `<img>` elements are `opacity: 0` and exist only to load bitmaps and carry
alt text. Nothing else is ever painted.

Per-frame composite order, exactly:

1. reset transform, `source-over`, clear, `drawCover(ctx, front)`
2. if any stamps: `ctx` → `destination-out`, `drawImage(mask)` — punches a hole
   clean through the front
3. back to `source-over`
4. clear `buf`, **set `bctx` to `source-over`**, `drawImage(mask)` into `buf`,
   then `bctx` → `source-in`, `drawCover(bctx, back)`
5. `ctx.drawImage(buf, 0, 0)`

Never layer the back over the front without the `destination-out` erase first —
the front would show through every transparent pixel of the back.

`drawCover(c, img)` cover-fits into `c.width × c.height`, centred horizontally,
**anchored to the bottom**. Both layers go through the identical function so the
bodies stay registered.

The mask is **cleared and rebuilt every frame** from a live stamps array;
nothing accumulates. `mctx.setTransform(dpr,0,0,dpr,0,0)` so brush sizes stay in
CSS pixels — re-apply after every resize, since resizing a canvas resets its
transform. Lobes are solid-fill circles: no gradient, no blur, no `shadowBlur`,
no `globalAlpha`. **Hard edges are the entire character of the effect.**

### Brush

```
LIFE  = 1100 ms
base  = max(W, 260) * (coarse ? 0.15 : 0.12)
lobes = 3 + floor(random()*3)
  each: random angle, offset random()*base*0.45,
        radius base*(0.45 + random()*0.55)
decay: k = 1 - age/LIFE;  scale = k < 0.75 ? k/0.75 : 1
       offsets *= scale;  radii *= pow(scale, 0.8)
```

The stamp **shrinks**. It never fades — no alpha ramp, ever.

Between the previous pointer position and the new one, interpolate stamps every
`max(W,260)*0.04` px, capped at 40 per move, so a fast flick leaves one
continuous stroke rather than a dotted line.

### Five corrections to the original spec — all mandatory

1. **`bctx` must be reset to `source-over` before drawing the mask into `buf`.**
   Left on `source-in` from the previous frame, clearing `buf` and drawing the
   mask onto an empty canvas produces nothing, and the reveal works exactly once
   before dying.
2. **Cap live stamps at ~240, dropping oldest.** Stamps live 66 frames; a fast
   full-width sweep can otherwise leave 1,500+ alive, each 3–5 lobes, rebuilt
   from scratch every frame. The 60 fps target is unreachable without this cap.
3. **`aspect-ratio: 2/3`, not `3/4`.** The assets are 1200×1777 (0.675).
   At 3/4 with a bottom anchor, the top of the head is cropped off.
4. **Gate `ready` on both images.** Stamping before the back layer decodes
   punches a hole with nothing behind it.
5. **Reduced motion shows the revealed state, statically.** The original spec
   disabled auto-wander under `prefers-reduced-motion`; combined with no hover on
   touch and no text, that leaves some visitors a dead page.

### Events and input

Pointer events only, so mouse and touch share one path. `pointermove` →
convert to figure-local, interpolate, stamp, move the cursor dot. `pointerleave`
→ clear `last`, hide the dot. `pointerdown` → stamp.

`const touchMQ = matchMedia("(hover: none), (pointer: coarse)")`; set `coarse`
from it on init and on its `change` event.

**Auto-wander on coarse pointers**, after 2500 ms of no input:

```
autoT += 0.016
x = W*(0.5 + sin(autoT*1.3)*0.28)
y = H*(0.32 + sin(autoT*0.9 + 1)*0.22)
```

Stamp whenever the point has moved more than `W*0.02`. This is the only cue a
touch visitor gets.

Custom cursor: a flat solid 14 px dot, `position: fixed`, `pointer-events: none`,
above everything, moved with `transform: translate()`. No ring, no glow, no
shadow, no trailing lag. Stage is `cursor: none`; hidden entirely under
`(hover: none)`.

### What differs from a standalone demo

The original spec called for **zero visible text**. That cannot stand for the
site's hero: it would leave the page with no `h1`, nothing for a crawler, and
nothing for a screen reader beyond one `alt`. Keep the no-chrome discipline — no
nav, no hint line, no captions — but the **name is real text in the composition**
per §4b.G, and the page keeps its single `h1`.

---

## 5. Technical stack

Stable releases only. Pin everything. **Nothing ships on an alpha** — the site
has to still run in June when someone opens it from a job application.

| Layer | Pick | Notes |
| --- | --- | --- |
| Framework | Next.js 16, App Router, `output: 'export'` | Static export. **No API routes, no ISR, no runtime server components.** Design for that from day one. |
| 3D | Three.js r182+, `WebGPURenderer`, automatic WebGL2 fallback | WebGPU is Baseline since Safari 26 (Sept 2025) |
| React bridge | `@react-three/fiber` **v9 stable** + `drei` | v10 is alpha. Pin with `three` via an `overrides` entry. |
| Shaders | TSL, from `three/tsl` | One source compiles to WGSL and GLSL. Do not hand-write both. |
| Motion | GSAP 3.13+ — ScrollTrigger, SplitText, Flip, MotionPath, Observer, CustomEase | All plugins free since the Webflow acquisition; single `npm i gsap` |
| Scroll | Lenis | Config above |
| Ambient shaders | `@paper-design/shaders-react`, **pinned exactly** | Breaking changes ship under 0.0.x |
| Physics | `@react-three/rapier` | Desk sector only, and only if the objects earn it |
| State | Zustand | Already the owner's pattern in Volta |
| Assets | Blender → glTF 2.0 → `gltf-transform` (Draco + meshopt + KTX2) | See budget below |
| Hosting | Cloudflare Pages, static, from this repo | Unlimited bandwidth; 25 MiB cap per asset |

---

## 6. Performance budget

Agreed before modelling starts. These are gates, not aspirations.

| Metric | Budget |
| --- | --- |
| Pit lane LCP | **< 1.0 s** on a mid laptop |
| Race mode interactive | **< 6 s** on a mid laptop |
| Mobile Lighthouse performance | **≥ 90** |
| Total 3D payload, all sectors | **< 15 MB** after compression |
| Any single asset | **< 25 MiB** (hard — Cloudflare Pages rejects larger) |
| Frame rate, race mode | **60 fps** on integrated graphics |

Volta's existing assets are ~91 MB of geometry before textures (Red Bull Ring:
1,009 nodes / 352 meshes; RB19: 549 nodes / 190 meshes). **They are not ported.**
Sector 1 uses light original geometry — a track ribbon, a horizon, instrument
forms — with captured gameplay footage carrying the actual project. That decision
is what makes this budget reachable, and it also removes the model-licence
question entirely.

Video is the heaviest thing on the site. Encode AV1 with an H.264 fallback, cap
each clip at 12 seconds, serve from Cloudflare, and never autoplay more than the
sector in view. Clips **autoplay muted and loop** — they are not scrubbed by
scroll, which would need dense keyframes and is unreliable in Safari. Every clip
ships with a poster frame so a sector is never blank.

Volta is already encoded to spec (§4c): 12 s, 1024×576, seamless loop, 1.9 MB.
Do not re-derive it from the 65 MB source.

Mobile drops WebGL entirely: native video and a simpler grid, the same call
Stefan Vitasović made on his 2025 portfolio. Do not try to run five sectors on a
phone.

WebGL context loss already occurred on this project's assets. Register
`webglcontextlost` / `webglcontextrestored` handlers in the first commit of
Phase 1, not after a demo dies.

---

## 7. Accessibility

Not optional, and partly a credibility signal — Donna's own test suite asserts
WCAG 2.1 AA invariants, so this site failing them would undercut the case study.

- Single `h1`, correct heading hierarchy, no skipped levels
- `prefers-reduced-motion: reduce` → no camera movement, no parallax, no
  auto-playing motion. Sectors become static compositions. Content stays complete.
- Full keyboard path through every sector and every interaction
- Visible focus rings (`--focus-ring`), never `outline: none`
- Contrast AA against the actual rendered background, including over canvas
- No state carried by colour alone
- Decorative canvases `aria-hidden`, with a real text equivalent nearby
- A visible control to switch to pit lane, present in every sector

---

## 8. Phase gates

No phase starts until the previous gate passes. Each gate is checkable by
someone who did not build it.

| Phase | Scope | Gate |
| --- | --- | --- |
| **0** ✅ | Content, tokens, pit lane, deploy | Five case studies readable as plain text at a live URL |
| **1** | The Grid (Volta) + the line + the grade + the video treatment + asset pipeline | 60 fps on a mid laptop; LCP < 1 s on pit lane; context-loss handler proven by forcing a loss; **the line renders and responds to scroll velocity** |
| **2** | The City (Signum) + the scripted refusal + transition 1→2 | Refusal works on touch and under reduced motion; no network call of any kind |
| **3** | The Street (Donna) + The Café (Decibels) | Scored against two reference sites with the Awwwards MCP `verify_build` |
| **4** | The Desk (Flosstime) + credo + polish | Mobile Lighthouse ≥ 90; full keyboard pass; AA contrast verified; **the line is unbroken from first scroll to last** |

---

## 9. Suggested Phase 1 structure

```
app/
  layout.tsx            # fonts, tokens, <SmoothScroll>
  page.tsx              # race mode shell
  pit/page.tsx          # pit lane, ported from index.html
components/
  scroll/SmoothScroll.tsx   # Lenis + GSAP ticker, one place only
  canvas/Stage.tsx          # the single Canvas; sectors mount into it
  canvas/sectors/{Grid,City,Street,Cafe,Desk}.tsx
  canvas/post/Grade.tsx     # the one grade over everything
  ui/TimingTower.tsx        # nav; reuse pit lane markup
content/
  projects/*.mdx        # ported verbatim from index.html
lib/
  gsap.ts               # registerPlugin once, defaults set here
  budget.ts             # asset budget assertions, fails the build if exceeded
```

One `<Canvas>` for the whole site. Sectors are scenes inside it, swapped on
scroll progress. Never mount a second canvas.

---

## 10. What not to do

- Do not rewrite the case-study copy. Port it.
- Do not add a second accent colour, a gradient mesh background on every sector,
  or a particle system without a reason that survives being said out loud.
- Do not use motionsites.ai prompts as the build source. Reference shelf only —
  built from, the site reads as generated, which is the one failure mode we are
  designing against.
- Do not re-implement any project. See "Evidence, not re-implementation" above.
  No webcam, no microphone, no calls, no model API calls, no backend.
- Do not port the Red Bull Ring or RB19 models, and keep F1 and Red Bull marks,
  liveries and names off the site. Original geometry only.
- Do not let a sector's loading state be a blank screen. Pit lane content is the
  loading state.
- Do not build frosted-glass project cards, and do not put refraction over a
  capture's content. See §4b.F.
- Do not use `flosstime.jpg`.
- Do not re-encode the Volta clip or re-cut the hero portraits. They are
  production-ready (§4c), and re-deriving them loses the shared frame that keeps
  the two portraits registered.
- Do not ship an alpha dependency.

---

## 11. Open items for the owner

- [ ] Contact details for the footer — email, LinkedIn, résumé PDF. Deliberately
      left out of `index.html` rather than guessed.
- [ ] A Decibels capture — the caption stream revising in place. The only
      sector still without its asset.
- [ ] Confirm the hero's back layer: pose skeleton (recommended, §4b.G) or the
      racing-driver cutout, which is cut and ready either way. The reveal
      mechanics in §4d are the same for both.
- [ ] Optional: re-record Volta with the webcam feed live, so the pose skeleton
      is visible in the footage.
- [ ] Clean the Decibels public repo: a real phone number, org IDs, and an
      unauthenticated ingest endpoint are in it per the owner's own audit.
- [ ] Confirm what is public in Signum (`MridhulSharma/headsup`) and how the
      two teammates are credited.
- [ ] Domain purchase, pointed at Cloudflare Pages.
