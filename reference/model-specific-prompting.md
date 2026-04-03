# model-specific prompting

This file captures practical prompting patterns drawn from fal blog guides and release notes. Use it when a request targets a specific model family or when generic prompting is producing weak results.

## General rules across fal models

- put the core subject and action first
- add environment, composition, style, and lighting after the core ask
- prefer concrete spatial language over abstract adjectives
- use quoted text for visible typography
- for edits, clearly separate what must stay the same from what changes
- for multi-reference tasks, assign each reference a role

## FLUX family

Best structure:

```text
Subject -> Action -> Style -> Context
```

Use FLUX when you want controllability, repeatable seeds, stronger production iteration, or a reliable default for image generation and image editing.

### Best practices

- keep the core transformation obvious
- use JSON or structured prompting when the workflow supports it
- use HEX colors when exact brand colors matter
- use references deliberately instead of over-describing identity
- for editing, do not rewrite the whole image if only one element changes

### Good fit

- default image generation
- product visuals
- consistency-heavy edits
- LoRA-driven custom style or subject work

## FLUX Kontext

Use `fal-ai/flux-pro/kontext` for surgical edits and continuity work.

### Best practices

- prompt only the changed element or local transformation
- preserve the rest implicitly or explicitly
- iterate in smaller edit passes instead of one giant rewrite

### Good phrasing

```text
Preserve the composition and lighting. Replace the paper label with brushed aluminum while keeping the bottle shape unchanged.
```

## Seedream

Best structure:

```text
Subject -> Setting -> Style -> Lighting -> Technical
```

Use Seedream when realism, typography, layout control, multilingual prompting, or detailed structured composition matters.

### Best practices

- use explicit placement language such as foreground, left third, upper right
- quote visible text directly
- use HEX colors when precise color control matters
- include materials, surfaces, lens feel, and lighting direction when precision matters
- when supported, JSON prompting is strong for layout-driven scenes

### Good fit

- realism-first campaigns
- layout-sensitive ads
- poster work
- text-bearing product visuals

## Nano Banana

Use Nano Banana for contextual edits, multi-reference composition, product consistency, and identity-preserving changes.

### Best practices

- use direct, imperative edit language
- keep prompts short for small edits
- use multiple references for subject or product lock
- prefer it for combining images, turnarounds, and preserving recognizable identity

### Watchouts

- community reports stronger safety friction in some fashion, skin, or real-person cases
- do not rely on it as the only fallback for sensitive edits

## Wan 2.7

Use Wan 2.7 when readable visible text, posters, presentation slides, infographics, or text-aware edits are central to the output.

### Best practices

- use exact quoted text
- describe placement region by region
- define hierarchy explicitly: headline, subhead, modules, CTA, footer
- for edits, preserve font, alignment, size, color, and perspective when they matter
- use `pro` endpoints for final delivery and non-pro endpoints for draft passes or fallback runs

### Good fit

- posters and presentation slides
- dense text-heavy marketing assets
- multilingual layouts
- text replacement and copy updates

## Qwen Image and Qwen Image Edit

Use Qwen as a text-aware alternate when Wan 2.7 is unavailable or when Qwen's style understanding is the better fit.

Read `prompts/qwen-image-2.md` for the dedicated Qwen Image 2 playbook based on the official Qwen blog.

### Best practices

- use exact quoted text
- use named styles or art movements when style fidelity matters
- keep edit prompts terse when changing only text or one local detail
- use it for posters, title cards, packaging, and text-bearing creative assets when Wan is unavailable or not the best fit

### Example edit phrasing

```text
Replace the headline text with "SUMMER DROP" and keep the same font weight, alignment, and orange color.
```

## Recraft

Use Recraft for design-first outputs, graphics, packaging concepts, vector-like visuals, icons, and ad compositions.

### Best practices

- specify the graphic style directly
- provide exact brand colors
- call out whether the output should feel like packaging, poster, icon system, or social ad
- use custom styles or style IDs if the workflow already has them

## Kling 3

Write prompts like scene direction, not like a bag of tags.

### Best practices

- think in shots, not clips
- define the subject and action early
- choose one camera move
- include environmental motion
- include audio cues only if useful and supported
- for multi-shot work, label each shot explicitly

### Good structure

```text
Shot 1: [what the camera sees and how it moves]
Shot 2: [what changes]
```

### Good fit

- cinematic image-to-video
- performance and motion-rich scenes
- narrative clips where shot language matters

## Veo 3.1

Use Veo when you want premium reference-conditioned video, first/last-frame control, strong cinematic logic, or more physically coherent motion.

### Best practices

- layer camera language, narrative action, atmosphere, and sound
- describe timing and cause/effect clearly
- use reference or first/last-frame modes when transitions matter

### Good fit

- premium concept videos
- high-control transitions
- reference-conditioned motion

## LTX

Use LTX for open-style, iterative, workflow-friendly video generation.

### Best practices

- direct the camera clearly
- describe performance beats and pauses
- use it for fast iteration before spending on premium hosted models
- prefer stronger-quality variants over aggressive quantized ones when quality matters

### Good fit

- local-style workflows
- previs
- repeated revisions

## Reference role assignment

For multi-reference requests, assign roles explicitly:

```text
Use image 1 for the subject identity, image 2 for the background architecture, and image 3 for the color palette and styling.
```

## Preservation language

Useful clauses:

- keep the face recognizable
- keep the same lighting direction
- keep the bottle silhouette unchanged
- keep the current font and text alignment
- change only the jacket material
- do not alter the background
