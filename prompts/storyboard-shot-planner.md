# storyboard and shot planning

Use this guide when the user wants a sequence, ad spot, mini story, trailer beat, or any request that is too large for one clip.

## Core rule

Do not try to generate a whole story in one video prompt.

Instead:

1. reduce the idea to beats
2. turn beats into shots
3. generate one shot at a time
4. keep continuity through recurring visual anchors

## When to use this file

Use it for requests like:

- "make me a 30 second ad"
- "create a short cinematic story"
- "turn this concept into a trailer"
- "generate a sequence with rising tension"

## Shot planning format

Write the plan in five columns:

- shot number
- narrative function
- visual description
- camera language
- generation method

## Template

```text
Shot 1 - [narrative function]
Visual: [what we see]
Camera: [framing and movement]
Prompt focus: [emotion, action, atmosphere]
Method: [text-to-video or image-to-video]

Shot 2 - [narrative function]
Visual: [what we see]
Camera: [framing and movement]
Prompt focus: [emotion, action, atmosphere]
Method: [text-to-video or image-to-video]
```

## Good narrative functions

- establish world
- isolate protagonist
- introduce conflict
- reveal product
- emotional turn
- action beat
- closing image

## Continuity anchors

To make separate generations feel related, repeat:

- the same character wardrobe
- the same product design
- the same palette
- the same lens language
- one recurring environment cue
- one recurring emotional tone

## Recommended generation strategy

### For story or ad work

1. start with a shot list
2. choose 1 to 3 anchor stills that define the world
3. use those stills for image-to-video where consistency matters
4. only use text-to-video for establishing or experimental shots

### Suggested model split

- establishing or exploratory shots: `fal-ai/ltx-2.3/text-to-video/fast`
- continuity-heavy shots: `fal-ai/ltx-2.3/image-to-video`
- final hero shots: `fal-ai/kling-video/v3/pro/image-to-video`

## Example: 15-second perfume ad

```text
Shot 1 - establish mood
Visual: rain-dark city street at night, black sedan pulls to a stop, amber reflections across wet pavement
Camera: low wide shot, slow push in
Prompt focus: mystery, luxury, anticipation
Method: text-to-video

Shot 2 - reveal product world
Visual: a hand places a faceted perfume bottle on black stone, mist moving through rim light
Camera: macro close-up, subtle circular move
Prompt focus: elegance, texture, premium detail
Method: image-to-video

Shot 3 - emotional payoff
Visual: bottle hero shot isolated against black with moving highlights and drifting haze
Camera: locked hero framing with minimal motion
Prompt focus: prestige, clarity, logo readability
Method: image-to-video
```

## Output pattern

When helping the user, return:

- a shot list
- which shots should be text-to-video versus image-to-video
- which stills should be created first
- one continuity note to carry across the whole sequence
