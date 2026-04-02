# fal model routing

This file is the quick decision matrix for choosing fal endpoints. Treat it as a strong default map, then verify live availability and schema with fal MCP because the catalog changes quickly.

## Selection rules

- Use `recommend_model` when the user describes an outcome.
- Use `search_models` when you need a category-specific scan or fallback.
- Use `get_model_schema` before execution.
- Use `get_pricing` before premium runs or any batch workflow.

## Text-to-image

### General default

- Endpoint: `fal-ai/flux-2-flex`
- Use for: safest overall image-generation default, controllable iteration, typography-capable drafts, production-friendly prompt refinement
- Tradeoff: less opinionated than flashier single-shot models, so it benefits from better prompt craft

### Fast draft model

- Endpoint: `fal-ai/nano-banana-2`
- Use for: rapid drafts, reference-heavy ideation, and situations where you may later edit or animate the result
- Tradeoff: not the safest universal default for every still-image task

### Premium default

- Endpoint: `fal-ai/nano-banana-pro`
- Use for: polished stills, hero art, stronger composition, multi-reference generation, and visually rich final delivery
- Tradeoff: community sentiment likes the output but does not always trust it as the most operationally reliable editing default

### Typography and poster work

- Endpoint: `fal-ai/qwen-image-2/pro/text-to-image`
- Use for: posters, title cards, infographics, PPT-like slides, layouts with readable text, multilingual text-in-image, and text-aware campaign work
- Tradeoff: powerful but polarizing; use when text rendering or built-in style understanding matters more than a neutral default

### Brand-forward visual design

- Endpoint: `fal-ai/recraft/v4/pro/text-to-image`
- Use for: ad creative, design-led images, packaging, graphics, stylized brand visuals, and layout-driven output
- Tradeoff: best as a design-specific route rather than the general photoreal default

### Tunable control

- Endpoint: `fal-ai/flux-2-flex`
- Use for: users who want steps, guidance, repeatable seeds, and controllable iteration
- Tradeoff: requires more parameter judgment than opinionated models, but current community sentiment sees Flux as the safest broad default

### Strong prompt adherence

- Endpoint: `fal-ai/gpt-image-1.5`
- Use for: detail-sensitive requests where exact prompt following matters
- Tradeoff: pricing can be more complex than fixed-cost per-image models

## Image editing

### General edit default

- Endpoint: `fal-ai/flux-pro/kontext`
- Use for: reference-driven edits, targeted changes, continuity across iterations, and edits where preservation matters most
- Tradeoff: best results depend on clear constraints and structured edit language

### Contextual micro-edits and multi-reference edits

- Endpoints: `fal-ai/nano-banana-2/edit`, `fal-ai/nano-banana-pro/edit`
- Use for: contextual micro-edits, identity-preserving changes, product polish, multi-reference composition, and direct natural-language edits
- Tradeoff: community likes the output but frequently reports safety friction, so avoid making it the only fallback for sensitive real-person or fashion work

### Text and typography edits

- Endpoint: `fal-ai/qwen-image-2/pro/edit`
- Use for: text replacement, poster updates, local typography-aware changes, and preserving font/layout intent
- Tradeoff: stronger as a specialist editor than as a neutral general-purpose edit default

### Realism-first commercial editing alternate

- Endpoints: `fal-ai/bytedance/seedream/v4.5/edit`, `fal-ai/bytedance/seedream/v5/lite/edit`
- Use for: realism-first edits, looser-filter refinement, precision composition changes, and text-aware commercial assets
- Tradeoff: strong specialist route, but do not treat edit endpoints as general text-to-image defaults

### Structured edit pipelines

- Endpoint: `bria/fibo-edit/edit`
- Use for: mask-aware or JSON-guided edits, production workflows, enterprise-style control
- Tradeoff: more setup, but higher transparency and repeatability

## Text-to-video

### Fast iteration

- Endpoint: `fal-ai/ltx-2.3/text-to-video/fast`
- Use for: previs, concept clips, fast social tests, and local or open-style workflow thinking
- Tradeoff: workflow-friendly, but not the strongest final-quality hosted option

### Premium creative video

- Endpoint: `fal-ai/veo3.1/fast`
- Use for: higher-end clips when text-only generation is still acceptable and the user wants premium cinematic control
- Tradeoff: higher spend; community often prefers Veo when reference conditioning, inserts, lip sync, or controlled transitions matter

### Best-value hosted cinematic video

- Endpoint: `fal-ai/kling-video/v3/pro/image-to-video`
- Use for: motion-rich premium clips, natural acting, and cinematic image-to-video hero shots
- Tradeoff: better treated as the default hosted hero-video route than as a universal text-to-video answer

## Image-to-video

### Premium hero clip

- Endpoint: `fal-ai/kling-video/v3/pro/image-to-video`
- Use for: cinematic motion, polished hero shots, clips that need strong visual quality, strong performance, or natural motion
- Tradeoff: premium cost, longer runtimes, usually async, but current community sentiment often sees it as the best value hosted default

### Start-to-end frame control

- Endpoint: `fal-ai/kling-video/o3/standard/image-to-video`
- Use for: a defined starting frame and ending frame, transitions, controlled scene movement
- Tradeoff: more setup, but stronger shot design when both endpoints of motion are known

### Premium reference-driven realism

- Endpoint: `fal-ai/veo3.1/reference-to-video`
- Use for: stronger realism, reference-based generation, premium inserts, and high-control motion
- Tradeoff: premium tier; use when reference conditioning or high-end control matters enough to justify the spend

### First and last frame control

- Endpoint: `fal-ai/veo3.1/first-last-frame-to-video`
- Use for: transitions, reveals, before-and-after beats, and emotionally controlled opening-to-ending shots
- Tradeoff: requires stronger planning up front, but gives cleaner transition logic

### Faster open iteration

- Endpoint: `fal-ai/ltx-2.3/image-to-video`
- Use for: repeated revisions, lower-cost animation from a still, and ComfyUI-style iterative workflows
- Tradeoff: practical and workflow-friendly, but not the top prestige visual choice

## Video control and utility

### Motion transfer

- Endpoint: `fal-ai/kling-video/v3/pro/motion-control`
- Use for: applying movement from a reference video to a character or still image

### Physics-driven movement

- Endpoint: `fal-ai/goal-force`
- Use for: physically plausible directional motion, controlled object movement

### Depth extraction

- Endpoint: `fal-ai/depth-anything-video`
- Use for: VFX, compositing, depth passes, scene understanding

## Utility image models

### Upscaling

- Endpoint: `fal-ai/seedvr/upscale/image`
- Use for: final output cleanup, print readiness, ecommerce detail improvement

### Background removal

- Endpoint: `pixelcut/background-removal`
- Use for: product cutouts, stickers, transparent-background assets

## Voice and speech

### Low-cost expressive narration

- Endpoint: `xai/tts/v1`
- Use for: quick voiceovers, inexpensive narration, iterative script testing

### Voice cloning

- Endpoint: `fal-ai/lux-tts`
- Use for: cloned narration from a reference sample
- Tradeoff: quality depends heavily on the reference audio

### High-control premium TTS

- Endpoint: `fal-ai/minimax/speech-02-hd`
- Use for: polished voice work when control is worth the spend

### Dialogue voice cloning

- Endpoint: `fal-ai/dia-tts/voice-clone`
- Use for: conversational or character voice cloning workflows

## Suggested defaults by user intent

### "Give me ideas quickly"

- Start with `fal-ai/flux-2-flex` or `fal-ai/nano-banana-2`
- For video concepts, start with `fal-ai/ltx-2.3/text-to-video/fast`

### "I need a final hero visual"

- Start with `fal-ai/nano-banana-pro` or `fal-ai/flux-2-flex` depending on whether polish or control matters more
- Escalate to `fal-ai/recraft/v4/pro/text-to-image` or `fal-ai/qwen-image-2/pro/text-to-image` when typography or design polish matters

### "I need a poster, slide, infographic, or text-heavy layout"

- Start with `fal-ai/qwen-image-2/pro/text-to-image`
- Use exact quoted copy, explicit module placement, and layout hierarchy

### "I need multilingual text rendered inside the image"

- Start with `fal-ai/qwen-image-2/pro/text-to-image`
- Keep each language literal and specify where each text block appears

### "Make this still move"

- Start with `fal-ai/ltx-2.3/image-to-video` for iteration
- Upgrade to `fal-ai/kling-video/v3/pro/image-to-video` for the final hero pass

### "Keep this subject consistent while editing"

- Start with `fal-ai/flux-pro/kontext`

### "I need text replacement, signage edits, or poster copy changes"

- Start with `fal-ai/qwen-image-2/pro/edit`
- Use exact quoted replacement text and preserve font, alignment, color, and perspective unless the user wants them changed

### "I need a product asset for commerce"

- Generate or edit with `fal-ai/flux-2-flex`, `fal-ai/flux-pro/kontext`, or `fal-ai/nano-banana-pro`
- Then run `pixelcut/background-removal`
- Finish with `fal-ai/seedvr/upscale/image`

### "I want a cinematic short clip with a story sense"

- Create a strong keyframe still first
- Animate with `fal-ai/kling-video/v3/pro/image-to-video`
- Use `fal-ai/kling-video/o3/standard/image-to-video` or `fal-ai/veo3.1/first-last-frame-to-video` when you can define both first and last frame

### "I want the safest broad default based on current community usage"

- Start with the Flux family for image tasks
- Use Nano Banana as a specialist edit or reference-heavy option, not the only default
- Use Kling for value-heavy premium video and Veo for high-control premium transitions or reference-conditioned video

## Execution advice

- Use `run_model` for still images, edits, background removal, and upscaling.
- Use `submit_job` plus `check_job` for video and other long-running jobs.
- Wait between `check_job` calls instead of polling continuously; about 30 seconds is a good default for long-running jobs.
- In Alter, prefer the `wait` tool when available, directly or through Flow, before polling again.
- Upload source assets with `upload_file` instead of relying on local paths.
- If a premium endpoint is unavailable or too expensive, fall back one tier rather than blocking the workflow.
