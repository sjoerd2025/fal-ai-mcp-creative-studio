---
name: fal-ai-mcp-creative-studio
description: Load this skill before using the fal MCP server for model discovery, endpoint selection, schema or pricing checks, asset uploads, image/video/audio generation, or workflow chaining such as image-to-video, poster generation, text-aware editing, product cutouts, multishot cinematic sequences, voice-led assets, and other fal creative pipelines.
---

# Skill: fal-ai-mcp-creative-studio

Use this skill when a user wants to generate, edit, or iterate on image, video, audio, or multi-step creative assets with fal.ai through the hosted MCP server.

This skill is built for practical execution, not just model lookup. It covers model selection, pricing awareness, schema checking, asset uploads, prompt construction, and workflow design.

## What this skill does well

- Routes a request to the right fal MCP tool flow.
- Chooses strong default models by task, quality tier, and control needs.
- Writes better prompts for image, video, editing, and voice generation.
- Breaks ambitious requests into reusable creative pipelines.
- Pushes toward consistent, production-friendly outputs instead of one-off toy prompts.

## Required MCP context

The first thing this skill must do is check whether the AI assistant already has access to fal MCP tools.

- If fal MCP tools are available, continue normally.
- If fal MCP tools are not available and the assistant is Alter, ask the user to enable the MCP by going to the Remote MCP server section in the Tools Manager.
- If fal MCP tools are not available and the assistant is not Alter, tell the user to check the fal MCP documentation for setup instructions.

The hosted fal MCP server is:

```text
https://mcp.fal.ai/mcp
```

Authentication uses:

```text
Authorization: Bearer YOUR_FAL_KEY
```

Notes:

- fal MCP currently works with Alter and other Streamable HTTP MCP clients.
- The server is stateless. The API key is sent per request and is not stored.

## fal MCP tools you should use

### Discovery

- `recommend_model`: use when the user describes an outcome and the skill does not already provide a clear recommended endpoint.
- `search_models`: use when you need category, endpoint, or fallback exploration beyond the recommendations already documented in this skill.
- `get_model_schema`: always use before first-time execution on a chosen endpoint.
- `search_docs`: use for workflows, parameter explanations, examples, and edge cases.
- `get_pricing`: check this before expensive video, audio, or premium image runs.

### Execution

- `run_model`: use for short jobs such as most image generation, image editing, background removal, upscaling, and some TTS.
- `submit_job`: use for long-running jobs such as video, 3D, training, or anything likely to time out. For video generation, always use `submit_job` instead of `run_model`.
- `check_job`: poll status, fetch results, or cancel when using async generation. Do not call it in a tight loop; wait before polling again so the agent does not waste calls or fill context with redundant status checks.

### Utility

- `upload_file`: upload user images, video, or audio to fal CDN before generation.

## Workflow examples to look for

When using `search_docs`, `search_models`, or `recommend_model`, actively look for workflow patterns such as:

- text-to-image -> upscale
- image generation -> background removal -> product cutout delivery
- concept still -> image-to-video hero clip
- first-frame + last-frame -> transition shot
- multishot cinematic dialogue or trailer-style sequence
- poster or PPT-style layout generation -> text-aware edit pass
- reference image -> continuity-preserving edit -> video animation
- narration or voice clone -> animated character or promo asset
- motion-control or reference-to-video workflows
- JSON-structured or mask-aware editing workflows

If fal exposes a workflow endpoint or documented chain that fits the request, prefer that over inventing a custom stack from scratch.

## Routing

Choose the most relevant support file first, then come back to this file for execution rules.

- Image creation, key art, editorial, posters: `prompts/image-art-director.md`
- Image editing, local changes, continuity work: `prompts/image-editing.md`
- Product visuals, ads, ecommerce assets: `prompts/product-marketing.md`
- Story-first video, cinematic prompting, shot design: `prompts/video-director.md`
- Longer narrative planning and shot breakdowns: `prompts/storyboard-shot-planner.md`
- Seedream-specific prompting and commercial layouts: `prompts/seedream-5-lite.md`
- Wan 2.7 text-heavy layout and poster prompting: `prompts/wan-2.7.md`
- Qwen Image 2 text, layout, and edit prompting: `prompts/qwen-image-2.md`
- Kling-specific cinematic and dialogue prompting: `prompts/kling-3.md`
- Voice, narration, cloned voices, spoken assets: `prompts/voice-audio.md`
- Pipelines, orchestration, multi-step delivery: `workflows/creative-pipelines.md`
- Endpoint selection and tradeoffs: `reference/model-routing.md`
- Model-specific prompting from fal blog guidance: `reference/model-specific-prompting.md`

## Operating rules

1. Start from the user's outcome, not the model name.
2. Use the recommended endpoints already documented in this skill when they clearly fit; call `recommend_model` or `search_models` only when the task is ambiguous, needs a fallback, or may require a newer option.
3. Always call `get_model_schema` before first use of a model in a session.
4. Call `get_pricing` for premium models or any task that may require retries.
5. Prefer image-to-video when consistency matters; prefer text-to-video when ideating.
6. For long narrative work, break a story into shots instead of asking one model for a full film.
7. For edits, describe what must stay unchanged as clearly as what must change.
8. For product work, optimize for legibility, composition control, and post-processing, not only style.
9. Use `submit_job` plus `check_job` for video generation and other long-running tasks.
10. When polling async jobs, wait about 30 seconds between `check_job` calls unless the job is expected to finish sooner or the API returns a better cadence.
11. If running in Alter, use the `wait` tool when available, directly or through Flow, before the next `check_job` call.
12. If fal's catalog has changed, treat `reference/model-routing.md` as a starting point, then re-check live availability.
13. Keep the recommended tool stack inside fal-supported models and MCP-accessible utilities unless the user explicitly asks for external tools.

## Default workflow

### 1. Triage the request

Classify the user's need as one of:

- `text-to-image`
- `image-editing`
- `text-to-video`
- `image-to-video`
- `audio` or `tts`
- `utility` such as upscaling or background removal
- `pipeline` when more than one step is clearly needed

### 2. Decide quality mode

Use these rough modes unless the user specifies otherwise:

- `fast`: rapid iteration, lower cost, concepting
- `pro`: higher visual quality, better final delivery
- `control`: stronger editability, consistency, or structured behavior

### 3. Discover and verify

Use this sequence:

1. choose a recommended endpoint from this skill, or call `recommend_model` or `search_models` if discovery is actually needed
2. `get_pricing`
3. `get_model_schema`
4. `upload_file` if input assets are needed
5. `run_model` for short still-image, edit, utility, or lightweight audio tasks; `submit_job` for video and other long-running tasks
6. wait before polling, ideally around 30 seconds for long-running jobs
7. `check_job` for async tasks submitted with `submit_job`, then repeat the wait-plus-poll cycle as needed

### 4. Prompt properly

Use the task-specific guide file. Do not write flat prompts when the task needs structure.

### 5. Return useful output

When reporting back, include:

- chosen model endpoint
- why it was selected
- final prompt or prompt summary
- key parameters such as aspect ratio, duration, seed, guidance, or image size
- result URLs or job status
- the best next iteration if the user wants refinement

## Default task map

These are strong defaults. Use them directly when they clearly fit the task, and use live discovery only when you need a fallback, category scan, or a newer option.

- General image generation default: `fal-ai/flux-2-flex`
- Fast image generation drafts: `fal-ai/nano-banana-2`
- Premium image generation or polished hero stills: `fal-ai/nano-banana-pro`
- Typography-heavy images, posters, PPT-like slides, infographics, and multilingual text-in-image: `fal-ai/wan/v2.7/pro/text-to-image` or `fal-ai/wan/v2.7/text-to-image`
- Design-led brand graphics and layout-heavy ads: `fal-ai/recraft/v4/pro/text-to-image`
- General image editing default: `fal-ai/flux-pro/kontext`
- Tiny contextual edits or multi-reference identity-preserving edits: `fal-ai/nano-banana-2/edit` or `fal-ai/nano-banana-pro/edit`
- Text replacement and typography-aware editing: `fal-ai/wan/v2.7/pro/edit` or `fal-ai/wan/v2.7/edit`
- Realism-first commercial image-editing alternate: `fal-ai/bytedance/seedream/v4.5/edit` or `fal-ai/bytedance/seedream/v5/lite/edit`
- Structured image editing with masks or JSON: `bria/fibo-edit/edit`
- Fast local or open-style text-to-video iteration: `fal-ai/ltx-2.3/text-to-video/fast`
- Best-value hosted cinematic video: `fal-ai/kling-video/v3/pro/image-to-video`
- Start/end frame video transitions: `fal-ai/kling-video/o3/standard/image-to-video`
- Premium reference-driven video and high-end transitions: `fal-ai/veo3.1/reference-to-video` or `fal-ai/veo3.1/first-last-frame-to-video`
- Faster open workflow image-to-video iteration: `fal-ai/ltx-2.3/image-to-video`
- Motion transfer: `fal-ai/kling-video/v3/pro/motion-control`
- Physics-guided motion: `fal-ai/goal-force`
- Upscaling: `fal-ai/seedvr/upscale/image`
- Background removal: `pixelcut/background-removal`; if it fails or the user is not happy with the cutout, fall back to `fal-ai/bria/background/remove`
- Low-cost expressive TTS: `xai/tts/v1`
- Voice cloning: `fal-ai/lux-tts`

## Quality heuristics

### When to prefer fast models

- ideation
- prompt exploration
- generating base stills for later video animation
- generating many options before selecting one
- local or ComfyUI-style workflows where open-ish model behavior matters

### When to prefer premium models

- hero images
- final ad creative
- cinematic clips
- typography-sensitive layouts
- outputs where one strong take matters more than five draft takes

### When to prefer control-oriented models

- local edits
- character or product continuity
- workflows with masks, references, or structured constraints
- repeatable production tasks
- cases where community consensus favors controllability over flashier one-shot outputs

## Model-specific prompting

Do not assume every model responds best to the same prompt style.

- For FLUX family, prefer `subject -> action -> style -> context`.
- For Seedream, prefer `subject -> setting -> style -> lighting -> technical`.
- For Nano Banana, Wan 2.7, and Qwen Edit, keep edit prompts short and imperative.
- For Kling, think in shots and write scene directions.
- For Veo and LTX, layer camera, action, atmosphere, timing, and audio cues.
- For text-heavy or color-accurate assets, use quoted text, explicit placement, and HEX colors when supported.

Read `reference/model-specific-prompting.md` before prompting a specialist model.
If the chosen model is Seedream, Wan, Qwen, or Kling, also read the dedicated guide in `prompts/seedream-5-lite.md`, `prompts/wan-2.7.md`, `prompts/qwen-image-2.md`, or `prompts/kling-3.md`.

## Prompting standards

### Always specify

- subject
- environment
- framing or shot type
- lighting
- mood
- material or texture cues when relevant
- output intent such as ad, cinematic clip, poster, product page, or narration

### Avoid

- vague style piles
- contradictory camera instructions
- asking for long stories in a single short clip
- changing the whole image when the task only needs a local edit
- omitting what must remain consistent

## Workflow thinking

Use workflows when the request is obviously multi-step. fal workflow endpoints can emit intermediate `submit`, `completion`, `output`, and `error` events, which makes them a strong fit for stepwise creative jobs.

Good examples:

- generate key art -> remove background -> upscale
- generate concept still -> animate to video
- create character stills -> generate voice -> animate a talking asset
- produce a sticker or cutout asset from a prompted image

See `workflows/creative-pipelines.md` for concrete patterns.

## If the user is vague

Infer reasonable defaults and move forward. Use these defaults unless the user signals otherwise:

- image aspect ratio: match likely use case, usually square for concepts, portrait for posters, landscape for cinematic scenes
- video duration: short, focused clips
- image-to-video over text-to-video when a stable visual identity matters
- one strong concept prompt plus two lighter variants

Only ask a question if the ambiguity materially changes the output.

## Success criteria

This skill succeeds when you do all of the following:

- pick a model family that matches the task and budget
- use fal MCP in the right order
- produce prompts that are structured enough to be reusable
- split multi-step requests into workable stages
- give the user a result and a clean next move
