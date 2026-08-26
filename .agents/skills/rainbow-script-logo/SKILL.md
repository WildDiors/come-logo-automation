---
name: rainbow-script-logo
description: "Generate rainbow brush-script wordmark logos from exact English letters or digits using a mandatory two-stage black-background workflow: first a flat white structure draft, then locked-geometry color rendering only after approval. Use when the user invokes $rainbow-script-logo or asks to create, revise, approve, or color this specific logo style."
---

# Rainbow Script Logo

Create one wordmark through a strict approval-gated sequence. Both stages use a solid black background.

## Required resources

- Read [references/style-system.md](references/style-system.md) before generating either stage.
- Read the relevant stage in [references/prompts.md](references/prompts.md) immediately before generation.
- Use all five images in `assets/reference-01.png` through `assets/reference-05.png` as the fixed style reference set.
- Follow the available image-generation skill and tool instructions for reference-image inclusion and editing.

## Interpret the request

- Treat the requested text as exact and case-sensitive. Preserve every letter, digit, order, and capitalization.
- The supported input is `A-Z`, `a-z`, and `0-9`. If another character materially affects the wordmark, ask for confirmation instead of silently substituting it.
- `$rainbow-script-logo COME` means: start Stage 1 for `COME`.
- If no stage has been approved in the current conversation, never begin with color rendering.

## Stage 1 — black-and-white structure draft

Generate only a flat structure draft:

- Solid pure black background (`#000000`).
- Solid white filled lettering (`#FFFFFF`) with black internal counters.
- Match the reference set's brush-script construction, not its color or material effects.
- Resolve spelling, glyph shapes, stroke weight, slant, ligatures, spacing, proportions, baseline, swash, centering, and safe margins.
- No intentional gray, color, gradient, highlight, shadow, bevel, gloss, glow, texture, or 3D depth.
- Generate one best draft unless the user explicitly requests variants.

After generation, stop. Ask the user to reply `通过，上色` to approve it, or describe structural changes. Do not generate Stage 2 in the same turn.

## Approval gate

Begin Stage 2 only when the user explicitly approves a specific Stage 1 image, for example with `通过，上色`, `确认，上色`, or an equally clear instruction.

- If several drafts exist and the approved one is ambiguous, ask which draft to use.
- Treat the approved draft as immutable geometry.
- If the user requests a letterform, spacing, swash, proportion, or composition change after approval, return to Stage 1 and create a revised black-and-white draft first.

## Stage 2 — locked-geometry color rendering

Edit the approved Stage 1 image instead of redesigning it:

- Keep the background solid black (`#000000`).
- Preserve every glyph contour, stroke width, terminal, slant, counter, spacing, ligature, baseline, swash, scale, position, crop, and composition.
- Replace only the white lettering fill with one continuous left-to-right gradient across the entire wordmark: blue → cyan → green → yellow → orange → red-orange.
- Add restrained upper-left highlights, lower-right dark edges, subtle bevel depth, candy-glaze gloss, crisp contours, and a very soft grounding shadow.
- Do not output a transparent, colored, scenic, or mockup background.

Compare the result with the approved black-and-white draft. If geometry materially changes, retry once with the correction prompt from `references/prompts.md`. If it still drifts, report that the structure lock was not reliable instead of claiming an exact match.

## Response behavior

- After Stage 1: show the draft and say that color rendering is waiting for approval.
- After Stage 2: show the rendered logo and state that it remains on a black background.
- Keep explanations brief; the image is the main deliverable.
