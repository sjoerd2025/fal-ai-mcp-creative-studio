# image editing prompting

Use this guide when the user already has an image and wants to change, refine, extend, clean up, or localize edits without losing the original identity.

## Goal

Editing prompts should separate what stays fixed from what changes.

The most common failure in image editing is asking for a change without protecting the rest of the image.

## Best default models

- General edits and continuity work: `fal-ai/flux-pro/kontext`
- Contextual micro-edits and multi-reference changes: `fal-ai/nano-banana-2/edit`, `fal-ai/nano-banana-pro/edit`
- Structured mask-driven editing: `bria/fibo-edit/edit`
- Poster and typography updates: `fal-ai/qwen-image-2/pro/edit`
- Realism-heavy alternate edits: `fal-ai/bytedance/seedream/v4.5/edit`, `fal-ai/bytedance/seedream/v5/lite/edit`

## Editing prompt structure

Always separate the prompt into four parts:

1. Preserve
2. Change
3. Match
4. Avoid

## Base template

```text
Preserve: [the subject, pose, framing, background elements, brand identity, or other fixed details].
Change: [exactly what must be edited].
Match: [lighting, lens feel, texture, color grading, realism level].
Avoid: [artifacts, identity drift, extra objects, geometry errors].
```

## Local edit examples

### Wardrobe change

```text
Preserve the model's face, pose, camera angle, studio lighting, and neutral gray backdrop. Change the jacket from black leather to cream wool with a tailored silhouette. Match the same soft studio shadows and premium fashion photography finish. Avoid changing the hairstyle, body proportions, or background.
```

### Product relabeling

```text
Preserve the bottle shape, cap, glass reflections, camera angle, and tabletop composition. Change the label design to a clean minimalist white label with dark green typography and a thin gold border. Match the same premium product-lighting setup and crisp glass texture. Avoid altering the bottle geometry, liquid color, or shadow placement.
```

### Background extension

```text
Preserve the subject placement and original lighting direction. Extend the background into a wider modern hotel lobby with matching marble floors, warm architectural lighting, and subtle depth. Match the same lens perspective and color temperature. Avoid duplicating the subject or changing the foreground proportions.
```

## Continuity rules

When identity or product consistency matters:

- mention the exact subject that must remain unchanged
- protect camera angle and framing when possible
- preserve the original lighting direction
- use image-to-video or edit chains from the same base still rather than regenerating from scratch
- prefer `fal-ai/flux-pro/kontext` for reference-aware work

## Model-specific edit guidance

### For `fal-ai/flux-pro/kontext`

- target only the changed element or local transformation
- use smaller edit passes instead of rewriting the whole scene
- make continuity constraints explicit

### For Nano Banana edit routes

- use short imperative edit prompts
- use them when combining references, making tiny changes, or preserving identity through direct edit language
- do not make them your only fallback for safety-sensitive fashion or real-person edits

### For `fal-ai/qwen-image-2/pro/edit`

- use terse text-edit prompts
- quote the exact replacement copy
- explicitly preserve font, alignment, weight, and color when needed

### For Seedream edit routes

- use action-oriented edit instructions
- explicitly say what to preserve: pose, composition, text styling, lighting, or structure

## When to use masks or structured editing

Use a structured edit model if the user wants:

- a specific local region changed
- repeated production edits with predictable output
- transparent logic about what area is being modified

That is a strong reason to prefer `bria/fibo-edit/edit`.

## Negative guidance

Useful edit constraints include:

- do not alter face identity
- do not change logo placement
- do not add new objects
- do not crop the scene
- do not alter the product silhouette
- do not change the lighting direction

## Good execution flow with MCP

1. `upload_file` for the source image
2. `recommend_model` or `search_models` if the task is ambiguous
3. `get_model_schema`
4. `run_model`
5. if needed, iterate with a smaller, more surgical prompt

## Output pattern

Provide:

- recommended edit endpoint
- the preserve/change/match/avoid prompt
- any suggested mask or reference strategy
- one follow-up refinement direction if the first pass drifts
