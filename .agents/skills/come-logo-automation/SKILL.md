---
name: come-logo-automation
description: "Automate COME co-publishing wordmark design by generating 4–6 distinct flat-white-on-black brush-script structure drafts from an exact English-letter or digit logo name, then coloring only the selected approved draft. Use when the user explicitly invokes $come-logo-automation, clicks the COME联运logo自动化 skill and types only a name such as AXC9, or asks to create, revise, select, approve, or color this specific logo style. Never substitute a sample word for the user's text."
---

# COME 联运 Logo 自动化

Create an exact wordmark through a two-stage approval-gated workflow. Keep the interaction brief and make the images the main deliverable.

## Required resources

- Read [references/style-system.md](references/style-system.md) before generating either stage.
- Read the relevant section of [references/prompts.md](references/prompts.md) immediately before generation.
- For Stage 1, use `assets/reference-01.png` through `assets/reference-05.png` as local **shape and lettering-style references only**. Ignore their colors, highlights, shadows, and materials.
- Follow the active image-generation skill. Use the built-in image generator and one generation call per separate variant.

## Resolve the requested name

Determine the target before doing anything else:

1. If the message contains `Logo:` / `Logo：` / `生成：`, extract the first contiguous `[A-Za-z0-9]+` token after the final such prefix. Otherwise, extract the first such token after `$come-logo-automation` or the skill chip. Treat later text such as `6张` or `不要尾划` as modifiers, not part of the target. A message containing only a short letter-and-digit string is the target.
2. Treat the extracted target as exact and case-sensitive. Preserve every letter, digit, order, and capitalization.
3. There is no default target. `COME`, `Come`, and text visible in reference assets are examples only; never generate them unless the user explicitly requests that exact text.
4. If there is exactly one plausible `A-Z`, `a-z`, `0-9` target, start Stage 1 immediately. Do not ask for confirmation, size, style, palette, or composition.
5. If no target exists, ask only: `请输入要生成的 Logo 名称。`
6. If multiple conflicting targets exist, ask which exact target to use. Never guess or combine them.

If an unsupported character materially affects the wordmark, ask for confirmation instead of silently removing or replacing it.

## Stage 1 — four black-and-white structure drafts by default

Generate four separate variants in the same assistant turn. Generate five or six only when the user explicitly requests that count. Never generate fewer than four unless the user explicitly asks for fewer.

- Use four separate image-generation calls, not one contact sheet or multi-logo collage.
- Use the same exact target in every call.
- Keep all variants within the same reference family while varying only the structural direction described in `references/prompts.md`.
- Use a solid pure black background (`#000000`) and flat solid white filled lettering (`#FFFFFF`) with open black counters.
- Resolve glyph shape, stroke weight, slant, ligatures, spacing, proportions, baseline, swash, centering, and safe margins.
- Forbid gray sketch lines, construction guides, outlines-only lettering, color, gradients, highlights, shadows, bevels, gloss, glow, texture, and 3D depth.
- Ensure each image contains one wordmark only and no labels, captions, numbering, frames, or mockups.

Inspect all outputs. If a variant misspells, substitutes, duplicates, omits, or reorders a character, retry only that variant once using the exact-text correction prompt. Do not claim an incorrect draft is valid.

Present the images as `方案 A` through `方案 D` (and `E` / `F` when requested). Add only: `请选择方案，并回复“B，通过上色”或直接描述要修改的结构。` Do not explain the process.

## Approval gate

Begin Stage 2 only after the user selects one specific draft and clearly approves coloring, such as `B，通过上色`, `方案 C 确认上色`, or an unambiguous reference to one displayed image.

- If several drafts exist and the selection is unclear, ask only which lettered方案 to use.
- Treat the selected Stage 1 draft as immutable geometry.
- If the user requests any letterform, spacing, swash, proportion, or composition change after approval, return to Stage 1 and generate the requested revised black-and-white draft before coloring.

## Stage 2 — locked-geometry color rendering

Edit the selected Stage 1 image; do not regenerate the lettering.

- Include the selected draft as the edit target using the image generator's current-image mechanism. The selected draft takes priority over bundled style references; do not omit or displace it merely to include more references.
- Keep the background solid black (`#000000`).
- Preserve every glyph contour, stroke width, terminal, slant, counter, spacing, ligature, baseline, swash, scale, position, crop, and composition.
- Replace only the white fill with one continuous left-to-right gradient across the whole wordmark: blue → cyan → green → yellow → orange → red-orange.
- Add restrained upper-left highlights, lower-right dark edges, subtle bevel depth, candy-glaze gloss, crisp contours, and a very soft grounding shadow.
- Do not output a transparent, scenic, colored-background, or mockup composition.

Compare the result with the approved draft. If geometry changes, retry once with the drift-correction prompt. If it still changes materially, say the geometry lock was unreliable rather than claiming an exact match.

After Stage 2, show the image with one short sentence: `已按所选结构完成彩虹上色，背景保持纯黑。`
