---
name: come-logo-automation
description: "Create and iteratively revise COME co-publishing brush-script wordmarks from exact English letters or digits. Generate separate flat-white-on-black structure drafts, let the user select, combine, lock, or repeatedly edit any draft, and render color only after explicit structure approval. Use when the user invokes $come-logo-automation or asks to create, revise, approve, recolor, or render this specific logo style. Never substitute sample text or infer approval from a draft selection."
---

# COME 联运 Logo 自动化

Create an exact wordmark through an approval-gated workflow in which black-and-white structure can be revised as many times as needed before color rendering. Keep the interaction brief and make images the main deliverable.

## Required resources

- Read [references/style-system.md](references/style-system.md) before generating or editing an image.
- Read the relevant section of [references/prompts.md](references/prompts.md) immediately before each generation or edit.
- For initial exploration, use `assets/reference-01.png` through `assets/reference-05.png` as local lettering references. Inherit shape language, rhythm, ligatures, swashes, and final material only where the active stage allows them. Never inherit reference text or background automatically.
- Follow the active image-generation skill. Use the built-in image generator and one generation call per separate image.

## Resolve the requested name

Determine the target before generating a new wordmark:

1. If the message contains `Logo:` / `Logo：` / `生成：`, extract the first contiguous `[A-Za-z0-9]+` token after the final such prefix. Otherwise, extract the first such token after `$come-logo-automation` or the skill chip. Treat later text such as `6张`, `更宽`, or `不要尾划` as modifiers.
2. A message containing only one short letter-and-digit string is the target.
3. Preserve the exact spelling, order, case, and digits. `COME`, `Come`, and words visible in reference images are examples only.
4. If exactly one plausible target exists, begin exploration immediately. Do not ask for confirmation, palette, material, or composition.
5. If no target exists, ask only: `请输入要生成的 Logo 名称。`
6. If multiple targets conflict, ask which exact target to use. Never combine or guess.

If an unsupported character materially affects the wordmark, ask before removing or replacing it.

## Workflow state and intent routing

Track the active state as `explore`, `revise`, `locked`, or `render`. Apply these rules before every response:

1. **A modification request overrides every later-stage cue.** Words or meanings such as `不满意`, `修改`, `只改`, `不要`, `保留`, `换成`, `缩短`, `放大`, `再来`, or `重新生成` keep the task in `explore` or `revise`, even if the user also names a方案.
2. **Selecting is not approving.** `B`, `选 B`, or `以 B 为底稿` selects a base only. It never authorizes color.
3. **Locking is explicit.** Enter `locked` only after language such as `结构确认`, `锁定结构`, or `这个版本通过`. Locking alone does not require immediate rendering.
4. **Rendering is explicit.** Enter `render` only when the user asks to color/render, including `进入上色`, `按默认上色`, or clear equivalent wording. `B，通过上色` both selects B, locks its structure, and requests default rendering.
5. If the same message selects a base and requests structural changes, revise the selected base in black and white; do not color.
6. If the same message locks the structure and supplies rendering settings, render in the same turn.
7. If a structural change is requested after color, return to a flat-white-on-black revision first. Do not reapply color until the revised structure is explicitly locked again.
8. If only color, material, or background changes are requested after color, preserve locked geometry and remain in `render`.

## Explore — black-and-white directions

Generate four separate variants by default. Generate five or six only when requested, and fewer only when explicitly requested.

- Use one call per image, never a contact sheet.
- Use the same exact target in every call.
- Apply user modifiers from the first message, such as `不要尾划`, `更硬朗`, or `更直立`, to every variant unless they ask for per-option differences.
- Use a solid pure black background (`#000000`) and flat solid white lettering (`#FFFFFF`).
- Keep every initial variant structurally distinct within the reference family.
- Forbid color, gradient, lighting, rendering, gray construction lines, labels, frames, and mockups.
- Ensure each image contains one centered, uncropped wordmark with safe margins.

Inspect every output. If a variant misspells, substitutes, duplicates, omits, or reorders a character, retry only that variant once with the exact-text correction prompt. Do not present an incorrect draft as valid.

Label outputs in the message as `方案 A` through `方案 D` and continue as needed. After initial exploration say only:

`可选择一个方案继续修改、组合多个方案，或重新生成其他方向。`

Do not mention coloring at this point.

## Select, combine, and revise

### Select a base

Treat a selected option as the current base, not approved geometry. If the user only says `B`, respond briefly that B is selected and invite a structural instruction; do not generate and do not mention automatic coloring.

### Combine options

Support requests such as `保留 B 的主体，换成 D 的尾划` or `使用 A 的紧凑结构和 C 的连笔`. Use the designated base as the edit target and other named images only as donor references. Produce a new flat-white-on-black revision before any rendering.

### Revision loop

- Edit the current black-and-white base rather than regenerating from scratch.
- Apply only requested changes. Preserve every unmentioned contour, glyph, spacing relationship, position, and composition.
- Parse each request into `MUST CHANGE`, `MUST PRESERVE`, and `MUST AVOID` before writing the edit prompt.
- Honor locks such as `锁定 A 和 X，只修改 C9` or `保留字距和倾斜，只改尾划`.
- Structural controls include overall proportions, slant, weight, stroke contrast, specific glyphs, spacing, ligatures, overlap, counters, terminals, baseline, swash, scale, centering, and safe margins.
- Generate one revised image by default. If the user asks for comparisons, generate two or three separate micro-variants varying only the requested property.
- Name revisions from their source, for example `B-r1`, `B-r2`, and `B-r3`, so later references remain unambiguous.
- Continue the black-and-white loop without a fixed revision limit until the user explicitly locks a version.

After every revision say only:

`可以继续修改，也可以回复“结构确认”锁定当前版本。`

Do not suggest coloring while the user is dissatisfied or revising.

## Lock — structure approval

Before locking, inspect the chosen image against the black-and-white approval checks in `references/style-system.md`. If it is misspelled, ambiguous, cropped, colored, or otherwise invalid, correct that defect before accepting the lock.

When the user locks without asking to render, preserve the exact image as the immutable geometry source and say:

`结构已锁定。可直接回复“默认上色”，或指定配色、材质和背景。`

Do not generate a color image until the user requests it.

## Render — locked-geometry color and material

Edit the locked black-and-white image; do not redraw the lettering.

- The locked image is the primary edit target and takes priority over bundled references.
- Preserve every glyph contour, stroke width, terminal, slant, counter, spacing, ligature, baseline, swash, scale, position, crop, and composition.
- Default wordmark rendering: one continuous left-to-right blue → cyan → green → yellow → orange → red-orange gradient across the whole mark, restrained upper-left highlights, lower-right dark edges, subtle bevel depth, candy-glaze gloss, and a very soft grounding shadow.
- Allow explicit user changes to palette, gradient direction, saturation, lighting, gloss, depth, outline, glow, and shadow. Preserve geometry.
- Background defaults to solid pure black (`#000000`) in every stage, regardless of reference images.
- Create a gradient or colored background only when the user explicitly requests a background change. `按参考图渲染` alone applies to the wordmark's color/material and still keeps a black background.
- Do not infer background color from an uploaded or bundled reference.

Compare the render with the locked image. If geometry changes, retry once with the drift-correction prompt. If it still changes materially, state that geometry lock was unreliable rather than claiming an exact match.

After rendering say only:

`已完成渲染。可继续调整色彩、材质或背景；如需改字形，将先返回黑白结构稿。`
