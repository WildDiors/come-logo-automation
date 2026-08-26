# Rainbow brush-script style system

Use these rules for both generation stages. The two-stage separation and exact requested text are invariants, not suggestions. Text visible in the bundled references is never an input value.

## Shared structure

- Form: bold custom brush-script wordmark with connected cursive rhythm.
- Slant: moderate right slant, approximately 8–15 degrees.
- Stroke: substantial weight, visible thick/thin contrast, rounded terminals, clean internal counters.
- Capital: the first capital is expressive and approximately 1.20–1.35 times the lowercase height.
- Spacing: compact and flowing, with controlled overlaps that never create ambiguous characters.
- Swash: optional and integrated; one main swash is preferred. It must not cover letters or touch the frame.
- Composition: front-facing, centered, generous margins, no mockup or perspective.
- Safe area: at least 10% on every side, including swashes.

## Length adaptation

| Input | Structure | Swash | Canvas |
|---|---|---|---|
| 1–3 characters | Compact emblem-like form; expressive first character | Usually none unless balance needs it | 1:1 |
| 4–7 characters | Standard connected rhythm and modest negative spacing | Auto; preferably from the last character | 1:1 or 4:3 |
| 8–12 characters | Reduce overlap and protect readability | One long lower arc can unify the word | 16:9 |
| Letters + digits | Digits use the same slant, weight, and terminal logic | Do not cross digits | Based on total length |

## Stage 1 appearance

- Background: pure black `#000000`.
- Wordmark: flat solid white `#FFFFFF`.
- Black counters remain open and legible.
- Edge antialiasing is acceptable, but there must be no intentional gray modeling.
- Forbidden: color, gradient, glow, highlight, shadow, bevel, extrusion, texture, material simulation, scene, badge, frame, and watermark.

Stage 1 approval checks:

1. Exact case-sensitive spelling appears once.
2. Every character is identifiable.
3. Brush-script construction matches the reference family.
4. Capital, spacing, ligatures, counters, baseline, and swash are intentional.
5. The mark is centered and uncropped.
6. The image contains one option only, with no label or contact-sheet layout.
7. The lettering is flat filled white, not an outline, pencil sketch, or construction drawing.

## Stage 2 appearance

Background remains pure black `#000000`.

Apply one gradient in the coordinate space of the entire wordmark, never restart the rainbow for each letter:

| Role | Color |
|---|---|
| Electric blue | `#1479F8` |
| Cyan | `#00CFEF` |
| Vivid green | `#55DF00` |
| Bright yellow | `#FFE400` |
| Orange | `#FF8B00` |
| Red-orange | `#FF3B12` |

Surface stack, bottom to top:

1. Continuous whole-word gradient.
2. Narrow darker inner edge along the lower and lower-right side.
3. Thin brighter rim along the upper and upper-left side.
4. Small, restrained specular highlights at selected turns or dots.
5. Very soft black grounding shadow.

Forbidden in Stage 2:

- Any structure or composition change from the approved Stage 1 draft.
- Per-letter rainbow resets or separate rainbow stripes.
- Metallic chrome, neon tubes, thick white outlines, heavy extrusion, excessive glow, scenery, mockups, or a non-black background.

Stage 2 approval checks:

1. Overlay comparison shows identical contours and positions.
2. Background is still pure black.
3. Gradient runs blue → cyan → green → yellow → orange → red-orange across the whole mark.
4. Highlights and dark edges follow the specified lighting direction.
5. Spelling and readability remain unchanged at thumbnail size.
