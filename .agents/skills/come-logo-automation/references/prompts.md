# Generation and edit prompts

Replace placeholders exactly. Preserve capitalization and digits. Never replace `{TEXT}` with text visible in a reference image.

## 1. Initial black-and-white exploration

Use the five bundled images only for lettering construction, stroke rhythm, ligatures, and swashes. Ignore their words, colors, materials, lighting, and backgrounds.

```text
Use case: logo-brand
Asset type: standalone wordmark structure draft
Primary request: Create one distinct structural design for the exact case-sensitive text "{TEXT}".
Input images: lettering-style references only. Never copy reference text, color, surface rendering, or background.
Scene/backdrop: solid pure black #000000.
Style/medium: bold custom brush-script wordmark, clean vector-like filled silhouette.
Text (verbatim): "{TEXT}"
Exact-text check: render these characters once, in this exact order and case: {TEXT}.
User-wide modifiers: {MODIFIERS}
Constraints: one centered wordmark only; flat solid white #FFFFFF filled lettering; open black counters; clean edges; front-facing; at least 10% safe margin; fully readable at thumbnail size.
Avoid: any word seen in the references; alternate spelling; missing, substituted, duplicated, or reordered characters; gray values; sketch lines; construction guides; outlines-only lettering; color; gradient; highlight; shadow; bevel; gloss; glow; texture; 3D depth; labels; option letters; captions; frames; badges; scenery; perspective; watermark; cropped swashes; colored or gradient background.
```

Append one direction per separate call:

- **方案 A — compact:** `Compact emblem-like composition, controlled connections, shortest practical swash, strongest small-size readability.`
- **方案 B — expressive capital:** `More expressive first character, approximately 1.25 times the remaining character height, balanced by a restrained terminal.`
- **方案 C — continuous rhythm:** `Stronger continuous cursive rhythm and elegant ligatures, while every character remains unmistakable.`
- **方案 D — signature swash:** `Refined signature-like construction with one integrated lower swash that supports rather than crosses the text.`
- **方案 E — upright:** `Slightly more upright and geometric rhythm, reduced overlap, disciplined spacing.`
- **方案 F — dynamic:** `More dynamic slant and stroke contrast, compact overall silhouette, no loss of legibility.`

If a user modifier conflicts with a direction, the user's modifier wins. For example, `不要尾划` removes swashes from all options, including D.

## 2. Exact-text retry

```text
Regenerate only this invalid black-and-white variant. The required text is exactly "{TEXT}" and must appear once. Copy the sequence character by character: {TEXT}. Do not use, copy, or retain any word visible in the reference images. Keep the intended structural direction and all valid user modifiers. Use a pure black #000000 background and flat solid white #FFFFFF filled lettering. No gray sketch lines, outlines, color, rendering, labels, mockup, colored background, or gradient background.
```

## 3. Single revision with locked properties

Use the selected black-and-white draft as the primary edit target. Parse the user's request before filling the fields.

```text
Use case: precise-object-edit
Asset type: revised black-and-white wordmark structure
Primary request: Edit the supplied base draft for the exact text "{TEXT}" without coloring or redrawing unrelated parts.
Input image: the selected black-and-white draft is the primary edit target.
MUST CHANGE: {CHANGES}
MUST PRESERVE: {LOCKS}
MUST AVOID: {AVOID}
Scene/backdrop: preserve solid pure black #000000.
Lettering: preserve flat solid white #FFFFFF.
Constraints: apply only MUST CHANGE. Preserve every unmentioned glyph contour, stroke width, terminal, slant, counter, spacing relationship, ligature, baseline, swash, scale, position, crop, and composition. Keep the exact text and at least 10% safe margin.
Avoid: color; gradient; highlight; shadow; bevel; gloss; glow; texture; 3D depth; labels; frames; mockups; scenery; transparent background; colored background; gradient background.
```

Examples of parsing:

- `首字母缩小15%，尾划缩短，其他不变`
  - `{CHANGES}` = `Reduce the first character by approximately 15%; shorten the terminal swash.`
  - `{LOCKS}` = `All other glyphs, spacing, slant, baseline, scale, and composition.`
- `锁定 A 和 X，只修改 C9`
  - `{CHANGES}` = `Modify only the C and 9 as specified by the user.`
  - `{LOCKS}` = `The A and X contours and positions, plus all unmentioned geometry.`

## 4. Combine selected options

Use the designated base as the actual edit target and donor images only for named attributes.

```text
Use case: controlled-reference-combination
Asset type: revised black-and-white wordmark structure
Primary request: Preserve the exact text "{TEXT}" and combine only the named structural attributes.
Base image: {BASE} is the primary geometry and composition.
Donor image: {DONOR} supplies only {DONOR_FEATURE}.
MUST PRESERVE from base: {BASE_LOCKS}
MUST AVOID: all other donor geometry, donor text, color, material, lighting, and background.
Output: one centered wordmark; pure black #000000 background; flat solid white #FFFFFF filled lettering; no rendering effects.
```

## 5. Micro-variant comparison

Use one separate call per value. All other geometry remains locked.

```text
Create one black-and-white micro-variant of the supplied base draft for exact text "{TEXT}". Change only {VARIABLE} to {VALUE}. Preserve all other glyph contours, spacing, ligatures, slant, baseline, swash properties, scale, position, and crop. Keep flat solid white lettering on pure black #000000. No color, gradient, material, lighting, label, frame, or mockup.
```

## 6. Return from color to black-and-white structure

Use when a structural request arrives after rendering. Prefer the locked black-and-white source; if it is unavailable, remove the render while restoring its geometry as faithfully as possible.

```text
Return the locked wordmark to a flat black-and-white structure draft before applying structural changes. Exact text: "{TEXT}". Use pure black #000000 background and flat solid white #FFFFFF lettering. Remove gradient, gloss, bevel, highlight, shadow, glow, outline, texture, and all other rendering. Then apply only these structural changes: {CHANGES}. Preserve: {LOCKS}. Do not reapply color in this step.
```

## 7. Locked-geometry color rendering

Use the explicitly locked black-and-white image as the edit target.

```text
Use case: precise-object-edit
Asset type: final color-rendered wordmark
Primary request: Render only the approved white lettering; do not redraw or reinterpret it.
Input image: the locked black-and-white draft is the immutable geometry target.
Text (verbatim): preserve the target image exactly.
Wordmark palette: {PALETTE}
Gradient placement and direction: {GRADIENT}
Material and lighting: {MATERIAL}
Background: {BACKGROUND}
Constraints: preserve every contour, stroke width, terminal, slant, spacing, ligature, counter, baseline, swash, scale, position, crop, and composition. Apply color and material only inside the existing lettering, except for the requested soft shadow or glow.
Avoid: any geometry change; regenerated letters; altered spelling; unrequested per-letter gradient resets; heavy extrusion; unrequested outline or glow; scenery; mockups; labels; watermarks; any background change not explicitly requested.
```

Default values:

- `{PALETTE}` = `One continuous whole-word gradient: electric blue #1479F8, cyan #00CFEF, vivid green #55DF00, bright yellow #FFE400, orange #FF8B00, red-orange #FF3B12.`
- `{GRADIENT}` = `Continuous left to right across the entire wordmark; never restart per letter.`
- `{MATERIAL}` = `Restrained candy-glaze gloss; narrow upper-left highlight; darker lower-right inner edge; subtle bevel depth; crisp contours; very soft black grounding shadow; no glow or outline.`
- `{BACKGROUND}` = `Preserve solid pure black #000000.`

## 8. Explicit gradient-background rendering

Use only when the user clearly asks to change the background. An uploaded reference with a gradient is not permission by itself.

```text
Preserve the locked wordmark geometry exactly. Apply the requested wordmark palette and material. Replace the default black background only because the user explicitly requested a background change. Background specification: {BACKGROUND_REQUEST}. If a reference image is named, use only its background color relationship, gradient direction, glow placement, and atmosphere; do not copy its text, logo geometry, objects, or watermark.
```

## 9. Color/material/background-only revision

```text
Use case: precise-object-edit
Primary request: Preserve the locked wordmark geometry exactly and change only the requested rendering attributes.
MUST CHANGE: {RENDER_CHANGES}
MUST PRESERVE: every glyph contour, stroke, terminal, spacing, ligature, counter, baseline, swash, scale, position, crop, composition, and all unmentioned rendering attributes.
Background rule: keep pure black #000000 unless MUST CHANGE explicitly names a different background.
Avoid: redrawing letters, changing spelling, shifting the mark, altering unrequested color regions, or inferring a background from references.
```

## 10. Geometry-drift correction

```text
Revert to the exact locked black-and-white draft. Restore every original contour, spacing, scale, swash, crop, and position. Apply only the requested color, material, and explicit background settings. Make zero geometry changes. Keep the background solid black #000000 unless the user explicitly requested a different background.
```

## Behavior checks

- `$come-logo-automation AXC9` → generate four separate black-and-white variants.
- `$come-logo-automation RS9，6张，不要尾划` → generate six separate black-and-white variants without swashes.
- `B` → select B only; do not color.
- `选 B，但首字母缩小15%，尾划缩短` → edit B in black and white; do not color.
- `保留 B 主体，使用 D 的尾划` → create a black-and-white combined revision.
- `锁定 A 和 X，只改 C9` → preserve A and X exactly and revise only C9.
- `结构确认` → lock the current black-and-white draft; do not color yet.
- `B，通过上色` → select B, lock it, and apply default wordmark rendering on black.
- `按参考图渲染` → reference the wordmark material only; background stays black.
- `背景改成参考图的蓝紫渐变` → gradient background is now explicitly authorized.
- After color, `尾划还是太长` → return to a black-and-white structure revision; do not automatically recolor.
