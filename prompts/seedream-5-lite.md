# seedream 5.0 lite prompting

Use this guide when routing to Seedream-style models, especially `fal-ai/bytedance/seedream/v5/lite/edit` and related Seedream endpoints.

This guide is based on fal's Seedream prompting guidance and should be treated as the specialist playbook for realism-heavy, layout-aware, text-capable commercial image work.

## Core idea

Seedream performs best when the prompt is written as a structured brief, not a loose aesthetic collage.

Best formula:

```text
Subject -> Setting -> Style -> Lighting -> Technical
```

## What Seedream is especially good at

- realism-heavy commercial visuals
- text rendering when the text is quoted
- exact color control with HEX values
- layout and placement-sensitive compositions
- structured multi-subject scenes
- context-aware editing that preserves most of the source image

## Prompt formula

### Subject

Describe the main thing first.

- what it is
- material or texture
- action or state

Good examples:

- a matte white skincare bottle with a brushed aluminum cap
- a rain-soaked cafe window with condensation and handwritten marker text
- a female architect reviewing blueprints on a concrete desk

### Setting

Describe where it happens and what supports the scene.

- environment
- time of day
- nearby props
- background cues

### Style

Describe the visual treatment.

- editorial product photography
- documentary street photography
- museum poster design
- cinematic matte painting

### Lighting

Seedream responds well to physical light descriptions.

- side light from the left
- soft north-window daylight
- hard noon sun with crisp shadows
- dramatic rim light with dark falloff

### Technical

Use technical language when it actually changes the result.

- lens and focal feel
- depth of field
- aspect ratio intent
- film or camera references
- macro, long exposure, overhead, isometric, and so on

## Seedream-specific rules

### Quote all intended visible text

Use quotation marks around exact text.

```text
A neon sign reading "OPEN 24 HOURS" in a rain-soaked alley.
```

Without quotes, the model is more likely to interpret text as description instead of rendered copy.

### Use explicit spatial language

Seedream is strong at spatial reasoning, so use that strength.

Useful phrases:

- on the left
- on the right
- in the foreground
- in the background
- between them
- lower right third
- upper left corner

### Use HEX colors for exact control

Pair HEX with a color name when possible.

```text
The label uses #0F766E deep teal with #F4D35E warm gold accents.
```

This is especially useful for brand and packaging work.

### Use JSON-like structure when layout matters

Seedream is a strong fit for structured scenes with many positioned elements.

Good use cases:

- product ads
- flat lays
- packaging comps
- poster layouts
- multi-object commercial images

## Editing guidance

Seedream edits respond well to action-oriented instructions plus preservation clauses.

Good pattern:

```text
Replace the current label with a minimalist cream label featuring "MINERAL SERUM" in dark green. Keep the bottle shape, reflections, camera angle, and background lighting unchanged.
```

Useful preservation clauses:

- keep the pose unchanged
- keep the bottle silhouette unchanged
- keep the current lighting direction
- keep the same composition
- keep the same text alignment

## Best prompt patterns

### Commercial product visual

```text
A matte white serum bottle with a brushed aluminum cap on a pale limestone plinth. Clean studio environment with soft daylight from the left and subtle shadow falloff. Premium editorial skincare photography. The label uses #0F766E deep teal and #F4D35E warm gold accents. Shot with an 85mm lens, shallow depth of field, luxury beauty campaign feel.
```

### Text-heavy campaign asset

```text
A modern exhibition poster pinned to a white gallery wall. Large clean title area at the top reading "FUTURE FORMS" in bold sans-serif lettering. Geometric shapes in #FFBE0B golden yellow, #FB5607 deep orange, and #8338EC rich purple arranged across the center. Museum poster design, crisp print-ready look, balanced negative space.
```

### Spatial multi-subject scene

```text
On the left side of a marble cafe table, a woman in a charcoal wool coat. On the right side, a man in a cream knit sweater. Two cappuccinos between them, steam rising. Rainy window in the background, blue-hour city light outside, warm cafe glow inside. Cinematic street photography, 50mm lens, natural reflections on the tabletop.
```

## When to choose Seedream over other models

- choose Seedream over Flux when realism, layout structure, quoted text, or exact color control matters more than being the broadest safe default
- choose Seedream over Nano Banana when you want a more structured commercial image or edit flow
- choose Seedream over Recraft when you want realism-first ads rather than graphic-design-first output

## What to avoid

- giant unordered adjective piles
- ambiguous multi-subject compositions
- unquoted text when the exact wording matters
- vague color language when brand fidelity matters
- under-specifying the lighting in high-polish product work

## Output pattern

When using Seedream, return:

- the final Seedream-formatted prompt
- any quoted text strings separately for verification
- any HEX values separately for verification
- any preservation clauses separately for verification in edit workflows
