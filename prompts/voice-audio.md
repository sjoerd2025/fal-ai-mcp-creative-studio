# voice and audio generation

Use this guide when the user wants narration, spoken dialog, voice cloning, or voice-led creative assets.

## Best defaults

- Fast low-cost narration: `xai/tts/v1`
- Voice cloning from reference audio: `fal-ai/lux-tts`
- Premium control: `fal-ai/minimax/speech-02-hd`
- Dialogue cloning: `fal-ai/dia-tts/voice-clone`

## Goal

Write scripts and voice directions that are performable.

The best TTS prompts and scripts usually define:

- speaker identity
- emotional tone
- pace
- emphasis
- audience or use case
- pronunciation-sensitive terms

## Script template

```text
Speaker: [who is speaking]
Audience: [who they are speaking to]
Tone: [calm, assured, intimate, energetic, playful, cinematic]
Pace: [slow, medium, brisk]
Performance notes: [where to pause, emphasize, soften, or brighten]
Script: [final copy]
```

## Example narration brief

```text
Speaker: warm confident female narrator in her 30s
Audience: premium skincare customer
Tone: intimate, trustworthy, elegant
Pace: slow-medium
Performance notes: brief pause after the first sentence, gently emphasize "visible calm"
Script: Your skin remembers every rushed morning. Give it one minute of visible calm with the new mineral recovery serum.
```

## Voice cloning rules

When cloning a voice:

- prefer clean reference audio with minimal room noise
- keep the requested performance aligned with the original voice's natural range
- do not expect a weak or noisy sample to produce premium output
- mention pronunciation or brand names explicitly when needed

## Voice directions that help

- grounded and conversational
- cinematic but restrained
- premium ad read, not announcer-like
- curious and lightly smiling
- calm instructional delivery
- emotionally contained, almost whispered

## Pairing audio with video

When the user wants a talking asset or voice-led video:

1. create or refine the visual still
2. generate narration or clone voice
3. if motion is needed, use a compatible video model or motion-control workflow

## Output pattern

Provide:

- recommended endpoint
- final script
- tone and pacing notes
- any pronunciation or reference-audio guidance
