# video director prompting

Use this guide when the user wants video generation with stronger storytelling, shot design, mood, pacing, or directorial intent.

## Core principle

Most generated videos improve when you think in shots, not in plots.

If the user wants a story, compress it into a single beat or split it into multiple clips. Do not ask one short clip to carry an entire narrative arc.

## Best model defaults

- Fast ideation: `fal-ai/ltx-2.3/text-to-video/fast`
- Faster still-to-motion iteration: `fal-ai/ltx-2.3/image-to-video`
- Premium cinematic still-to-video: `fal-ai/kling-video/v3/pro/image-to-video`
- Controlled start and end frame transitions: `fal-ai/kling-video/o3/standard/image-to-video`
- Premium reference-driven motion: `fal-ai/veo3.1/reference-to-video`
- Premium first-to-last frame transitions: `fal-ai/veo3.1/first-last-frame-to-video`
- Motion transfer: `fal-ai/kling-video/v3/pro/motion-control`

Use `submit_job` plus `check_job` for video.
Wait before polling again, typically about 30 seconds for long renders. In Alter, use the `wait` tool when available, directly or through Flow, before the next `check_job` call.

## Director framework

Build prompts in this order:

1. Story beat
2. Subject and action
3. Setting and atmosphere
4. Camera framing
5. Camera movement
6. Performance or motion style
7. Environmental motion
8. Lighting and palette
9. Sound or audio intent if supported
10. Ending state
11. Constraints

## Base template

```text
A [shot type] of [subject] in [setting].
The action is [single clear beat].
Camera [movement], with [lens or framing feel].
Lighting is [description], atmosphere is [mood], color palette is [palette].
Environmental motion includes [wind, rain, traffic, crowd, particles, reflections].
The clip should feel [genre or tone].
End on [ending frame or emotional beat].
Avoid [artifacts, identity drift, chaotic motion, extra subjects].
```

## Story-first prompting rules

- reduce the clip to one emotional beat
- define the protagonist's action clearly
- specify what the camera is doing
- include scene motion outside the subject so the world feels alive
- choose one pacing idea: slow reveal, urgent push-in, drifting observational, locked-off tension
- state the ending image if it matters

## Model-specific video guidance

### For Kling 3

- write prompts like scene direction, not keyword lists
- think in shots, not clips
- define the character or subject early and keep naming consistent
- include environmental motion and one clear camera move

### For Veo 3.1

- layer camera language, action, atmosphere, timing, and sound
- use reference or first/last-frame modes when you need tighter motion logic
- describe cause and effect clearly so the action feels physically coherent

### For LTX

- use it for fast iteration and workflow-friendly previs
- direct the camera and performance beats clearly
- treat it as the practical open-style workflow option, then upgrade to Kling or Veo for final hero shots if needed

## Good camera language

Prefer one clear movement:

- slow dolly in
- handheld follow
- locked-off wide shot
- crane down reveal
- lateral tracking shot
- low floating push past foreground objects

Avoid stacking many camera moves in a short clip.

## Good environmental motion cues

- curtains moving in window light
- rain streaking across glass
- drifting smoke or dust
- traffic reflections sliding over wet pavement
- hair or fabric reacting to wind
- distant crowd flow behind the subject

## Example prompts

### Cinematic character beat

```text
A medium close-up of a young violinist standing alone on a rooftop at blue hour above a glowing city. The action is a quiet inhale before she begins to play, her coat moving lightly in the wind. Camera slowly dollies in, intimate lens feel, shallow depth of field. Cool twilight tones with warm city bokeh below, faint fog in the air, reflective rooftop textures. The clip should feel wistful and cinematic, ending on her eyes lifting toward the skyline. Avoid abrupt body motion, duplicate limbs, extra characters, or chaotic camera shake.
```

### Product motion hero

```text
A macro product shot of a luxury perfume bottle on black stone in a dark studio. The action is a slow turn of the bottle as thin mist rolls across the surface and specular highlights travel across the glass. Camera executes a subtle circular move, premium commercial lens feel. Controlled rim lighting, black and amber palette, rich reflections, elegant pacing. End on the logo facing camera. Avoid label distortion, warped bottle shape, or messy particle motion.
```

### Start and end frame planning

For `fal-ai/kling-video/o3/standard/image-to-video`, define:

- first frame: what the shot opens on
- last frame: what emotional or visual state it lands on
- motion bridge: how the scene transitions between them

## Recommended workflow

### Best practice for polished video

1. Generate or refine a strong still image first.
2. Choose image-to-video over text-to-video if character or product continuity matters.
3. Use one shot per clip.
4. Iterate motion and camera behavior before changing the whole concept.

### For longer narratives

Break into shot list form:

```text
Shot 1: establish world
Shot 2: reveal protagonist
Shot 3: action beat
Shot 4: closing image
```

Generate each shot separately, then assemble downstream.

## Native audio guidance

If the selected video model supports audio, specify only a few essential sound cues:

- soft city ambience
- distant thunder
- fabric rustle
- subtle mechanical hum

Do not overload the prompt with a full sound design sheet.

## Output pattern

Provide:

- recommended endpoint
- a single production-ready prompt
- a shot-list version if the request implies a longer sequence
- guidance on whether to start from a generated still first
