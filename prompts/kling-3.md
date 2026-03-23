# kling 3 prompting

Use this guide when routing to Kling 3 endpoints such as `fal-ai/kling-video/v3/pro/image-to-video`, `fal-ai/kling-video/v3/standard/text-to-video`, `fal-ai/kling-video/o3/standard/image-to-video`, or related Kling motion workflows.

This is the dedicated cinematic prompting guide for Kling based on fal's own guidance.

## Core idea

Kling understands cinematic intent better than bag-of-tags prompts.

Write prompts like scene direction.

## Core rules

1. Think in shots, not clips.
2. Anchor subjects early for consistency.
3. Describe motion explicitly.
4. Use native audio intentionally.
5. Use longer duration for beat progression, not filler.
6. In image-to-video, treat the source frame as the anchor and describe how it evolves.

## Best prompt structure

```text
[Scene setup]
[Subject anchor]
[Shot or camera instruction]
[Action progression]
[Environmental motion]
[Dialogue or sound cues if needed]
[Ending beat]
```

## Subject anchoring

Define key subjects early and keep naming consistent.

Good:

```text
Character A: exhausted partner
Character B: defensive partner
```

Bad:

```text
the woman, then she, then the partner
```

Consistency matters more than poetic variation.

## Motion guidance

Be explicit about both subject motion and camera motion.

Useful camera verbs:

- tracks alongside
- slowly dollies in
- holds in a medium shot
- freezes as the subject pauses
- pans right to reveal
- pushes past foreground objects

Useful subject motion cues:

- turns sharply
- exhales shakily
- coat flutters in wind
- slides the folder across the table
- pauses, then looks up

## Multi-shot prompting

Kling handles multi-shot sequences better when each shot is labeled.

Template:

```text
Shot 1: [framing, subject, motion]
Shot 2: [framing, subject, motion]
Shot 3: [framing, subject, motion]
```

For each shot, specify:

- framing
- who or what is in focus
- what changes over time
- how the camera behaves

## High-quality multishot pattern

One strong community pattern is to let Kling 3 solve continuity and shot flow first, then do only light finishing after generation.

Good sequence:

1. write one multishot prompt with recurring subject and location anchors
2. generate the sequence in Kling 3 multishot mode
3. do only light enhancement or upscale after motion is already good
4. add ambient sound separately if needed

This usually works better than overcomplicating the base prompt or heavily reprocessing the clip.

### Continuity anchors to repeat

- same subject identity
- same wardrobe
- same lighting palette
- same location
- same time of day
- same emotional tone

### Minimal-post rule

If the base multishot result already has strong motion and continuity, do not suggest extra edit hops by default. Prefer:

- light enhancement
- upscale
- subtle sound design

over major regeneration.

## Dialogue and audio prompting

When using native audio, establish who is speaking and when the switch happens.

Best pattern:

```text
[Character A: Lead Detective, controlled serious voice]: "Let's stop pretending."
Immediately, [Character B: Prime Suspect, sharp defensive voice]: "I already told you everything."
```

## Audio rules

- use unique character labels
- put the action before the dialogue when it helps identify the speaker
- add tone labels such as `voice cracking`, `sleepy amused voice`, or `sharp defensive voice`
- use timing words like `immediately`, `after a pause`, `silence`, or `suddenly`

## Image-to-video guidance

Treat the input image as the lock.

Focus the prompt on how the scene changes from the still:

- subtle character motion
- light shifts
- camera push or pan
- atmosphere entering the frame
- object interaction

Do not rewrite the entire scene from scratch if the input image already defines it.

## Good prompt patterns

### Single-shot cinematic beat

```text
A medium close-up of a boxer alone in a locker room after a fight. Character A: exhausted fighter, bruised but composed. Camera slowly dollies in while he wraps and unwraps his hand tape, staring at the floor. Fluorescent locker-room lighting, soft flicker overhead, distant crowd noise fading in memory. The bench creaks as he leans forward. End on him looking directly into camera, breathing steady. Avoid chaotic motion or extra people entering frame.
```

### Dialogue scene

```text
A dim kitchen late at night. Only the refrigerator hum fills the silence.

Character A: exhausted partner.
Character B: defensive partner.

Shot 1: medium two-shot across the kitchen island. Character A sets a plate down too hard. Ceramic clinks sharply.
[Character A: exhausted partner, trembling frustrated voice]: "You never listen to me."

Immediately, Shot 2: over-the-shoulder on Character B turning around, eyes wide.
[Character B: defensive partner, shouting loudly]: "Because you never stop blaming!"

Shot 3: closer on Character A as the anger breaks into pleading.
[Character A, voice cracking]: "I'm not blaming... I'm begging."

Silence. Low sad piano enters quietly.
```

### Multishot continuity scene

```text
Nighttime roadside diner with green fluorescent spill and wet pavement outside. Character A: young woman in a black leather jacket, short dark hair, tired but alert. Character B: man in a charcoal coat, late 30s, restrained expression. Maintain the same wardrobe, facial identity, and moody night lighting across all shots.

Shot 1: wide exterior through the rain-streaked window as the neon diner sign flickers. Camera slowly pushes toward the booth where both characters sit in silence.

Shot 2: medium profile shot inside the booth. Character A stirs untouched coffee and glances toward Character B without speaking. The camera holds steady while steam rises between them.

Shot 3: closer over-the-shoulder on Character B as he finally looks up. A truck passes outside, headlights briefly sweeping across both faces.

Shot 4: tight close-up on Character A as she exhales and makes a decision. End on her eyes locking forward while the diner hum continues.

Avoid identity drift, outfit changes, extra people entering the booth, or abrupt camera motion.
```

### Community-tested cyberpunk dialogue sequence

This is a strong reference pattern for Kling multishot dialogue scenes because it combines:

- fixed visual anchors
- explicit shot labels
- simple camera instructions
- controlled dialogue timing
- a clean emotional progression

```text
Cinematic cyberpunk dialogue scene, multishot sequence, 35mm film grain, shallow depth of field, rain-slicked industrial walkway, cyan-teal and warm amber neon atmosphere throughout.

SHOT 1 — HOLD ON ESTABLISH: A young woman with black hair and red lips in a black crop top and chain-belt plaid skirt stands close to a tall man in a dark coat on a wet industrial walkway, neon haze and bokeh behind them. She turns her chin slightly upward toward him and speaks: "They flagged your neural ID three blocks back. You've been burning a ghost signal this whole time." Camera holds static. Rain mist drifts through frame. No cut until she finishes speaking.

SHOT 2 — SLOW PUSH IN ON HIM: Cut to slow cinematic push-in toward the man's face from a slight low angle, rain-blurred neon bokeh behind him. He exhales slowly, jaw tightening, then speaks: "Ghost signal was for you. Didn't want the Syndicate knowing I was coming to find you." His eyes drop to meet hers. Camera settles close on his face.

SHOT 3 — WIDE PULL AS SHE MOVES: Cut to wide two-shot as she breaks eye contact and steps forward along the railing, back partly to him, chain belt catching neon light. She speaks over her shoulder: "The Syndicate already knows. They sent me." She stops walking. Camera holds wide. Rain falls softly.

SHOT 4 — TIGHT INTERCUT: Cut to tight close-up on her face as she slowly turns back — red lips, dark eyes unreadable, a faint almost-smile. Two beats of silence. Cut to tight close-up on his face, something unguarded crossing his expression for just a moment. He says quietly: "I told myself this was just a job. I stopped believing that when I met you." Intercut between both faces, slow and deliberate. Her expression softens almost imperceptibly.

SHOT 5 — FINAL WIDE FADE: Cut to wide shot from the far end of the walkway, both figures small against a towering brutalist cyberpunk cityscape, distant neon glowing blue and amber. She takes one slow step toward him. Camera completely still. He asks quietly: "You still working for them?" Hold on her face — she says nothing. Three beats of silence. Rain continues to fall.
```

Why it works:

- the visual world is locked once at the top
- each shot has one clear job
- camera moves are minimal and readable
- dialogue is attached to visible action beats
- silence is used intentionally instead of filling every moment with movement

### Image-to-video commercial extension

```text
The product remains locked in the same position as the source image. Camera performs a slow circular move around the bottle while thin mist rolls across the surface. Specular highlights travel across the glass, and the label remains crisp and readable. Subtle black-to-amber light shift. End on the logo facing camera.
```

## When to choose Kling over other video models

- choose Kling over LTX when you want stronger hosted cinematic motion and performance
- choose Kling over Veo when value and natural motion matter more than maximum premium control
- choose Kling for shot-based storytelling, dialogue scenes, and image-to-video hero passes

## What to avoid

- one giant paragraph trying to contain an entire story
- inconsistent character labels
- vague motion words like `cinematic movement` without specifics
- too many camera moves in one short shot
- dialogue with no speaker attribution

## Output pattern

When using Kling, return:

- the final shot-structured prompt
- a list of named characters if dialogue is present
- camera instructions separated from dialogue instructions when useful
- whether the job is better run as text-to-video, image-to-video, or start/end-frame animation
