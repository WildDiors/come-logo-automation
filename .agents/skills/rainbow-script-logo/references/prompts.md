# Generation prompts

Replace `{TEXT}` exactly. Preserve capitalization and digits.

## Stage 1 prompt — black-and-white structure draft

```text
Create one monochrome structure draft for a standalone wordmark displaying the exact case-sensitive text: "{TEXT}". Derive the letterform language from the attached five reference images: bold custom brush-script lettering, connected cursive rhythm, rounded terminals, moderate right slant, an expressive larger first capital, controlled stroke contrast, and an optional integrated swash. Use a solid pure black background (#000000) and flat solid white lettering (#FFFFFF), including white edge-to-edge fills with clean internal black counters. Focus only on spelling, glyph construction, stroke weight, ligatures, spacing, baseline, proportions, swash, centering, and safe margins. The text must appear exactly once, remain fully readable, and match the requested capitalization and digits. No color, no gray modeling, no gradient, no highlight, no shadow, no bevel, no gloss, no glow, no texture, and no 3D depth. Output one front-facing black-and-white structure draft, not a mockup.
```

Negative prompt:

```text
Avoid misspelled, duplicated, substituted, or missing characters; illegible ligatures; thin typography; serif or sans-serif print fonts; intentional gray values; gradients; colored pixels; outlines instead of filled lettering; highlights; shadows; bevels; gloss; glow; extrusion; texture; scenery; mascots; badges; frames; perspective mockups; watermarks; and cropped swashes.
```

## Stage 1 revision prompt

```text
Revise the black-and-white structure draft only. Keep the solid black background and solid white filled lettering. Apply only these requested structural changes: {CHANGES}. Do not add color or rendering effects.
```

## Stage 2 prompt — locked-geometry color rendering

Use the approved Stage 1 image as the edit target and include the five style references when the image tool permits it.

```text
Use the attached approved black-and-white structure draft as immutable geometry. Preserve the exact case-sensitive text and keep every glyph contour, stroke width, terminal, slant, spacing, ligature, counter, baseline, swash, scale, position, crop, and composition unchanged. Do not redraw, reinterpret, or regenerate the lettering. Keep the background solid black (#000000). Replace only the white lettering fill with one continuous left-to-right gradient across the entire wordmark: electric blue, cyan, vivid green, bright yellow, orange, and red-orange. Add a narrow upper-left highlight, a darker lower-right inner edge, subtle bevel depth, restrained candy-glaze gloss, crisp vector-like contours, and only a very soft grounding shadow. The final text must remain identical to the approved structure draft. Output one front-facing color-rendered wordmark on black.
```

Negative prompt:

```text
Do not change or regenerate any letter shape, stroke, ligature, spacing, slant, baseline, swash, proportion, scale, position, crop, or composition. Avoid misspelled or duplicated characters, per-letter repeated rainbow gradients, separate rainbow stripes, metallic chrome, heavy extrusion, thick white outlines, neon tubes, excessive glow, textured backgrounds, scenery, mascots, badges, frames, perspective mockups, watermarks, and cropped swashes.
```

## Stage 2 geometry-drift correction

```text
Revert to the exact approved black-and-white structure draft. Restore every original contour, spacing, scale, swash, crop, and position. Apply color and surface rendering only; make zero geometry changes. Keep the background solid black.
```

## Invocation examples

- `$rainbow-script-logo COME`
- `$rainbow-script-logo RS9，1:1，不要尾划`
- After approving the displayed Stage 1 draft: `通过，上色`
- Stage 1 correction: `修改：首字母小一点，尾划缩短；仍然只要黑底黑白稿`
