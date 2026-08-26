# Generation prompts

Replace `{TEXT}` exactly. Preserve capitalization and digits. Never replace it with text visible in a reference image.

## Stage 1 shared prompt

Use the five bundled images only for lettering construction and brush-script character. Their rainbow colors and rendered surfaces are forbidden in Stage 1.

```text
Use case: logo-brand
Asset type: standalone wordmark structure draft
Primary request: Create one distinct structural design for the exact case-sensitive text "{TEXT}".
Input images: five style references for letterform construction, stroke rhythm, ligatures, and swashes only; ignore all reference colors and surface effects.
Scene/backdrop: solid pure black #000000.
Style/medium: bold custom brush-script wordmark, clean vector-like filled silhouette.
Text (verbatim): "{TEXT}"
Exact-text check: render these characters once, in this exact order and case: {TEXT}.
Constraints: one centered wordmark only; flat solid white #FFFFFF filled lettering; open black counters; clean edges; front-facing; at least 10% safe margin; fully readable at thumbnail size.
Avoid: any word seen in the references; alternate spelling; missing, substituted, duplicated, or reordered characters; gray values; sketch lines; construction guides; outlines-only lettering; color; gradient; highlight; shadow; bevel; gloss; glow; texture; 3D depth; labels; option letters; captions; frames; badges; scenery; perspective; watermark; cropped swashes.
```

Append one structural direction per separate call:

- **方案 A — compact:** `Compact emblem-like composition, controlled connections, shortest practical swash, strongest small-size readability.`
- **方案 B — expressive capital:** `More expressive first character, approximately 1.25 times the remaining character height, balanced by a restrained terminal.`
- **方案 C — continuous rhythm:** `Stronger continuous cursive rhythm and elegant ligatures, while every character remains unmistakable.`
- **方案 D — signature swash:** `Refined signature-like construction with one integrated lower swash that supports rather than crosses the text.`
- **方案 E — upright:** `Slightly more upright and geometric rhythm, reduced overlap, disciplined spacing.`
- **方案 F — dynamic:** `More dynamic slant and stroke contrast, compact overall silhouette, no loss of legibility.`

## Stage 1 exact-text retry

```text
Regenerate this one black-and-white variant. The required text is exactly "{TEXT}" and must appear once. Copy the sequence character by character: {TEXT}. Do not use, copy, or retain any word visible in the reference images. Keep the requested structural direction, pure black background, and flat solid white filled lettering. No gray sketch lines, outlines, color, rendering, labels, or mockup.
```

## Stage 1 revision

```text
Edit the selected black-and-white structure draft only. Keep the exact text "{TEXT}", solid black background, and flat solid white filled lettering. Apply only these requested structural changes: {CHANGES}. Do not add color or surface rendering. Preserve everything else.
```

## Stage 2 — locked-geometry color rendering

Use the approved Stage 1 image as the edit target.

```text
Use case: precise-object-edit
Asset type: final color-rendered wordmark
Primary request: Color only the approved white lettering; do not redraw or reinterpret it.
Input image: the selected black-and-white draft is the immutable edit target.
Scene/backdrop: keep the existing solid black #000000 background.
Text (verbatim): preserve the target image exactly.
Constraints: preserve every contour, stroke width, terminal, slant, spacing, ligature, counter, baseline, swash, scale, position, crop, and composition. Replace only the white fill with one continuous whole-word gradient: electric blue, cyan, vivid green, bright yellow, orange, red-orange. Add a narrow upper-left highlight, darker lower-right inner edge, subtle bevel depth, restrained candy-glaze gloss, crisp contours, and only a very soft grounding shadow.
Avoid: any geometry change; regenerated letters; altered spelling; per-letter rainbow resets; separate rainbow stripes; chrome; heavy extrusion; thick white outlines; neon tubes; excessive glow; textured or colored backgrounds; scenery; mockups; labels; watermarks.
```

## Stage 2 geometry-drift correction

```text
Revert to the exact selected black-and-white draft. Restore every original contour, spacing, scale, swash, crop, and position. Apply color and surface rendering only. Make zero geometry changes and keep the background solid black.
```

## Invocation checks

- `$rainbow-script-logo AXC9` → target is `AXC9`; generate four separate black-and-white variants.
- `使用 $rainbow-script-logo 生成 Logo：M3` → target is `M3`; never generate `COME`.
- `$rainbow-script-logo RS9，6张，不要尾划` → target is `RS9`; generate six separate black-and-white variants without swashes.
- `B，通过上色` → edit only方案 B into the color stage.
