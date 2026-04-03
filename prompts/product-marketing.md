# product and marketing generation

Use this guide for ecommerce, ads, launch creative, packaging, social assets, premium product stills, and campaign-style visuals.

## Goal

Make assets that sell the product, not just look pretty.

This means prioritizing:

- product readability
- believable materials
- intentional negative space
- copy-friendly composition
- easy downstream cleanup

## Recommended stacks

### Fast product concepting

- Generate with `fal-ai/nano-banana-2`
- Remove background with `pixelcut/background-removal` if needed; if it fails or the cutout is not good enough, retry with `fal-ai/bria/background/remove`
- Upscale with `fal-ai/seedvr/upscale/image`

### Premium hero asset

- Generate with `fal-ai/nano-banana-pro`
- Edit/refine with `fal-ai/flux-pro/kontext`
- Remove background if needed
- Upscale with `fal-ai/seedvr/upscale/image`

### Layout or poster-heavy campaign work

- Generate with `fal-ai/wan/v2.7/pro/text-to-image`
- Use `fal-ai/wan/v2.7/text-to-image` for cheaper draft passes when the copy and layout still need iteration

## Prompt structure

```text
[product] presented as [asset type], shown in [camera angle or framing].
[environment or backdrop], [lighting], [material and surface accuracy].
Designed to feel [brand adjectives].
Leave [negative space or layout zone] for copy if needed.
Avoid [specific errors].
```

## Common modes

### Clean ecommerce packshot

```text
A premium vitamin bottle presented as a clean ecommerce hero image, front three-quarter angle on a pure off-white backdrop. Soft directional studio light, crisp label legibility, realistic matte plastic texture, subtle grounded shadow. Designed for a modern wellness brand. Avoid warped bottle geometry, noisy reflections, extra props, and unreadable label areas.
```

### Lifestyle ad image

```text
A luxury running shoe placed on a rain-dark city step at dawn, low-angle hero framing with the shoe dominant in frame. Cool ambient blue light with warm storefront reflections, visible mesh and rubber textures, premium sports campaign mood. Leave negative space in the upper left for headline placement. Avoid extra shoes, messy crowd elements, and distorted proportions.
```

### Beauty or skincare premium still life

```text
A glass skincare serum bottle on sculpted travertine forms, tight editorial still-life composition. Soft warm daylight, natural stone texture, subtle condensation, pale sand and cream palette, modern luxury beauty campaign feel. Clean background with room for typography. Avoid clutter, label distortion, and unrealistic liquid behavior.
```

## Product prompting rules

- call out the exact product category and material fidelity
- specify the commercial context: packshot, launch poster, social ad, beauty still life, app store visual, billboard frame
- mention negative space intentionally if copy or logo placement is needed
- describe lighting with studio realism rather than broad adjectives
- avoid over-styling when clarity matters more than mood

## Recommended workflow patterns

### Product cutout pipeline

1. generate or edit the product hero
2. remove background with `pixelcut/background-removal`
3. if Pixelcut fails or the result is not good enough, retry with `fal-ai/bria/background/remove`
4. upscale with `fal-ai/seedvr/upscale/image`

### Campaign pipeline

1. create a master hero still
2. derive alternate crops or edit variants
3. if motion is needed, animate the hero still with image-to-video

## Output pattern

Provide:

- recommended endpoint or stack
- one primary campaign prompt
- one cleaner ecommerce variant
- one more emotional lifestyle variant
