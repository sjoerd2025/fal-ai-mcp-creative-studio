# wan 2.7 prompting

Use this guide when routing to Wan 2.7 endpoints such as `fal-ai/wan/v2.7/pro/text-to-image`, `fal-ai/wan/v2.7/text-to-image`, `fal-ai/wan/v2.7/pro/edit`, and `fal-ai/wan/v2.7/edit`.

Within this skill, Wan 2.7 is the preferred route for text-heavy image generation and editing such as posters, presentation slides, infographics, title cards, and other assets with a lot of visible copy.

## Core idea

Prompt Wan 2.7 like a layout brief, not a loose mood board.

It works best when you specify:

1. asset type
2. exact quoted text
3. where each text block appears
4. visual hierarchy
5. supporting imagery or icons
6. overall style and finish level

## Best prompting style

Use literal, structured instructions.

For generation, describe:

1. asset type
2. exact copy
3. placement by region or module
4. typographic hierarchy
5. imagery or background treatment
6. final design tone

For editing, describe:

1. exact change
2. exact replacement text
3. what must stay unchanged

## Rules for visible text

### Quote the copy exactly

Put all visible text in quotes.

```text
Top headline reads "SPRING LAUNCH".
Bottom CTA reads "Register by April 30".
```

### Define placement explicitly

Useful phrases:

- title at the top center
- subtitle directly below the title
- left column contains
- three modules along the bottom
- badge in the upper-right corner reads
- footer line at the bottom edge

### Describe hierarchy, not just content

Useful descriptors:

- large bold sans-serif headline
- smaller supporting subhead
- compact all-caps CTA button text
- three equal info cards with icons
- clean presentation slide spacing

## Good prompt patterns

### Poster

```text
Launch poster for a developer conference. Top headline reads "BUILD FASTER" in large bold white sans-serif type. Subtitle directly below reads "Agent workflows for modern teams" in smaller light-weight text. Bottom footer reads "San Francisco, June 2026". Dark graphite background, electric blue accent lines, centered product illustration, premium event-poster layout, strong readability.
```

### Presentation slide

```text
Enterprise presentation slide. Main title at the top center reads "Platform Overview" in large white sans-serif text. Subtitle below reads "Reliable image, video, and audio pipelines". Three horizontal modules across the lower half, each with an icon, short heading, and two lines of body text. Deep navy background, subtle grid, premium keynote-style spacing, very readable text.
```

### Text-aware edit

```text
Replace the main poster headline with "SUMMER DROP". Keep the same font weight, center alignment, orange color, poster composition, and background artwork.
```

## Editing rules

- keep edit prompts short and literal
- quote replacement copy exactly
- preserve font, alignment, size, color, and perspective when they matter
- prefer `pro` for final delivery or sensitive poster revisions
- use the non-pro endpoints for cheaper drafts or fallback passes

## When to choose Wan 2.7

- choose Wan over Nano Banana when the image needs a lot of visible text
- choose Wan for posters, presentations, slides, infographics, signage, and title cards
- choose Wan edit routes for text replacement, poster revisions, and slide copy updates

## What to avoid

- vague placeholders like `headline here`
- asking for many text blocks without placement
- mixing conflicting layout instructions in one pass
- rewriting the entire image when only one text region needs to change

## Output pattern

When using Wan 2.7, return:

- the final prompt with all quoted copy preserved exactly
- the chosen endpoint and why `pro` or non-pro fits the run
- the text strings listed separately for verification
- preservation clauses separately for edit workflows
