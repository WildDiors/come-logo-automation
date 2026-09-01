# Rainbow brush-script style system

Use these rules for exploration, revision, locking, and rendering. Exact requested text, explicit structure approval, and black-by-default backgrounds are invariants.

## Invariants

1. Render the exact case-sensitive target once. Reference-image text is never an input value.
2. Keep structural work flat solid white on pure black until the user explicitly locks it and asks to render.
3. Selecting a draft is not approval. Structural modification language always returns to black-and-white revision.
4. Preserve all unmentioned geometry during revision and honor explicit local locks.
5. The background remains pure black `#000000` in every stage unless the user explicitly requests a background change.
6. A colored or gradient reference background is visual reference only; never inherit it automatically.

## Default structure family

- Form: bold custom brush-script wordmark with connected cursive rhythm.
- Slant: moderate right slant, approximately 8–15 degrees.
- Stroke: substantial weight, visible thick/thin contrast, rounded terminals, clean internal counters.
- Capital: the first capital is expressive and approximately 1.20–1.35 times the remaining height.
- Spacing: compact and flowing, with controlled overlaps that never create ambiguous characters.
- Swash: optional and integrated; one main swash is preferred. It must not cover letters or touch the frame.
- Composition: front-facing, centered, generous margins, no mockup or perspective.
- Safe area: at least 10% on every side, including swashes.

These are defaults, not locks. Explicit user requests can make the mark more upright, geometric, wide, narrow, heavy, restrained, disconnected, or swash-free while preserving the recognizable COME reference family.

## Length adaptation

| Input | Structure | Swash | Canvas |
|---|---|---|---|
| 1–3 characters | Compact emblem-like form; expressive first character | Usually none unless balance needs it | 1:1 |
| 4–7 characters | Standard connected rhythm and modest negative spacing | Auto; preferably from the last character | 1:1 or 4:3 |
| 8–12 characters | Reduce overlap and protect readability | One long lower arc can unify the word | 16:9 |
| Letters + digits | Digits use the same slant, weight, and terminal logic | Do not cross digits | Based on total length |

## Adjustable structure controls

| Control | Default | Supported changes |
|---|---|---|
| Overall proportion | Balanced compact width | Wider, narrower, taller, flatter, shorter |
| Slant | 8–15° right | More upright or more dynamic |
| Weight | Bold | Lighter, heavier, stronger thick/thin contrast |
| First character | 1.20–1.35× height | Resize, reshape, simplify, sharpen the entry |
| Individual glyph | Reference-family construction | Edit one named letter/digit while locking others |
| Spacing | Compact | Open or tighten named pairs |
| Ligatures | Controlled connections | Add, remove, or simplify named connections |
| Overlap | Moderate | Reduce or increase without ambiguity |
| Counters | Open and legible | Enlarge or reshape negative spaces |
| Terminals | Rounded brush terminals | Sharper, softer, shorter, or cut terminals |
| Baseline | Mostly stable | Straight, rising, falling, or intentionally rhythmic |
| Swash | One restrained integrated swash | Remove, shorten, lengthen, redirect, or compare variants |
| Scale and position | Centered with 10% margin | Enlarge, reduce, or reposition while staying uncropped |

When the user specifies locks, those locks override all default balancing adjustments. Do not "improve" locked areas.

## Black-and-white structure appearance

- Background: pure black `#000000`.
- Wordmark: flat solid white `#FFFFFF`.
- Black counters remain open and legible.
- Edge antialiasing is acceptable, but no intentional gray modeling is allowed.
- Forbidden: color, gradient, glow, highlight, shadow, bevel, extrusion, texture, material simulation, scene, badge, frame, watermark, colored background, and gradient background.

### Structure approval checks

1. Exact case-sensitive spelling appears once.
2. Every character is identifiable.
3. Brush-script construction matches the requested reference-family direction.
4. Capital, spacing, ligatures, counters, baseline, and swash are intentional.
5. All explicitly locked properties remain unchanged.
6. Only requested revision properties changed.
7. The mark is centered, uncropped, and has safe margins.
8. The image contains one option only, with no label or contact-sheet layout.
9. Lettering is flat filled white, not an outline, sketch, or rendered surface.
10. The background is pure black.

## Default final rendering

Unless the user supplies other settings, apply one gradient in the coordinate space of the entire wordmark. Never restart the rainbow for each letter.

| Role | Color |
|---|---|
| Electric blue | `#1479F8` |
| Cyan | `#00CFEF` |
| Vivid green | `#55DF00` |
| Bright yellow | `#FFE400` |
| Orange | `#FF8B00` |
| Red-orange | `#FF3B12` |

Default surface stack, bottom to top:

1. Continuous left-to-right whole-word gradient.
2. Narrow darker inner edge along the lower and lower-right side.
3. Thin brighter rim along the upper and upper-left side.
4. Small, restrained specular highlights at selected turns or dots.
5. Very soft black grounding shadow.

## Adjustable rendering controls

| Control | Default | Explicit alternatives |
|---|---|---|
| Fill | Six-color continuous gradient | Solid color, two-color gradient, custom palette |
| Gradient direction | Left to right | Vertical, diagonal, radial |
| Gradient distribution | Whole word | Per-letter only when explicitly requested |
| Saturation | High | Softer, darker, pastel, retro, fluorescent |
| Bevel depth | Subtle | Flat, subtle, medium |
| Gloss | Restrained candy glaze | Matte, softer, stronger |
| Highlight | Narrow upper-left | Different direction or intensity |
| Dark edge | Subtle lower-right | Weaker, stronger, or removed |
| Shadow | Very soft black | Removed, deeper, or broader |
| Glow | Off | User-specified color and strength |
| Outline | Off | User-specified color and width |

Rendering changes never authorize structural changes.

## Background policy

Default background in exploration, revision, lock, and final rendering:

`solid pure black #000000`

Only explicit requests such as `背景改成蓝紫渐变`, `不要黑底`, or `背景也参考图3` authorize a different background. Once authorized, the user may control:

- colors and number of stops;
- linear, radial, or diagonal direction;
- light center, glow placement, and falloff;
- vignette, texture, and saturation.

`按参考图渲染`, `使用参考图颜色`, or attaching a reference with a gradient does not by itself authorize changing the background.

## Final render approval checks

1. Overlay comparison shows identical locked contours and positions.
2. Spelling and readability remain unchanged at thumbnail size.
3. Only requested rendering attributes changed.
4. Default gradient runs continuously across the whole mark unless overridden.
5. Highlights and dark edges follow the requested lighting direction.
6. Background is pure black unless an explicit background request is recorded.
7. No scenery, mockup, labels, or watermark were introduced.
