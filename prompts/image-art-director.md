# image art director prompting

Use this guide when the user wants an original still image, poster, key art frame, concept image, editorial visual, or branded campaign image.

## Goal

Write prompts like an art director, not like a keyword dump.

Strong image prompts usually contain:

- the subject
- the setting
- the composition
- the light
- the material or texture language
- the emotional tone
- the intended output format

## Core structure

Build the prompt in this order:

1. Primary subject and action
2. Environment and world details
3. Framing and composition
4. Camera or lens feel if relevant
5. Lighting and time of day
6. Color palette
7. Texture and material cues
8. Mood or emotional read
9. Output intent such as poster, editorial, ad, still frame, lookbook image
10. Constraints about what to avoid

## Base template

```text
[subject and action], in [environment], framed as [composition or shot type].
[lighting description], [color palette], [material and texture cues].
The mood is [tone]. Designed as [output intent].
Avoid [specific failure modes].
```

## Better prompt ingredients

### Composition language

Use concrete framing language such as:

- centered hero composition
- asymmetrical editorial framing
- wide cinematic landscape
- close-up product macro
- low-angle monument shot
- portrait with negative space for headline

### Lighting language

Prefer physical lighting cues over vague adjectives:

- golden hour side light
- overcast soft daylight
- neon spill with wet reflections
- hard noon sunlight with crisp shadows
- volumetric backlight through haze
- studio softbox with subtle rim light

### Texture language

Texture helps images feel intentional:

- brushed aluminum
- matte ceramic
- worn leather
- foggy glass
- damp asphalt
- raw paper grain
- polished chrome

## Prompt patterns by use case

### Editorial key art

Focus on mood, composition, silhouette, and color story.

```text
A lone cyclist crossing a flooded old town square at dawn, framed in a wide cinematic composition with the rider small against the architecture. Pale blue morning haze, warm amber window light, reflective cobblestones, soft fog drifting through the street. Quiet, melancholic, elegant. Designed as premium editorial key art with clean negative space. Avoid clutter, distorted wheels, extra riders, and random signage.
```

### Poster or title card

If text quality matters, lean toward Qwen Image 2 Pro and make the visual composition leave room for typography.

```text
A dramatic sci-fi observatory on a cliff above a stormy ocean, vertical poster composition with strong central silhouette and large clean sky area for title placement. Electric blue storm light, silver mist, wet stone textures, cinematic scale, premium theatrical poster mood. Avoid busy foreground details, muddy lighting, and unreadable composition.
```

### Product hero shot

Describe the product, material accuracy, selling angle, and background simplicity.

```text
A premium stainless steel travel mug standing on a pale limestone plinth, three-quarter product hero shot, minimalist studio setting with soft directional morning light and faint shadow falloff. Crisp brushed metal texture, subtle condensation, neutral warm-gray palette, premium lifestyle ad mood. Designed for ecommerce and ad creative. Avoid warped geometry, extra accessories, fingerprints, and noisy backgrounds.
```

## Model-specific advice

### For `fal-ai/flux-2-flex`

- Use a `subject -> action -> style -> context` structure.
- It is the safest broad default when you want controllability and cleaner iteration.
- Use HEX colors and structured prompting when exact brand control matters.

### For `fal-ai/nano-banana-2`

- Keep prompts concise but visual.
- Use it for fast exploration and variations.

### For `fal-ai/nano-banana-pro`

- Give richer scene context and composition intent.
- Use when you already know the direction.

### For `fal-ai/qwen-image-2/pro/text-to-image`

- Call out text zones, poster layout, or typography needs clearly.
- State whether you want room for copy or actual visible text.

### For Seedream-style routes

- Use `subject -> setting -> style -> lighting -> technical`.
- Prefer explicit placement language and quoted text.
- Add lighting direction, material language, and lens feel when precision matters.

### For `fal-ai/recraft/v4/pro/text-to-image`

- Emphasize art direction, brand character, and graphic polish.

### For `fal-ai/flux-2-flex`

- Use when you want to tune steps, guidance, seeds, or reproducibility.

## Iteration strategy

When the first result is close but not right:

- tighten composition before adding more style words
- simplify the palette if the image looks muddy
- describe one camera choice, not three
- state what to preserve in the next iteration
- add one negative constraint for the dominant failure mode

## Output pattern

When helping a user, provide:

- a recommended endpoint
- one primary prompt
- two shorter alternate directions
- a sentence explaining why the model fits the job
