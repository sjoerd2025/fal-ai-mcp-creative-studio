# qwen image 2 prompting

Use this guide when routing to Qwen Image 2 endpoints such as `fal-ai/qwen-image-2/pro/text-to-image`, `fal-ai/qwen-image-2/text-to-image`, `fal-ai/qwen-image-2/pro/edit`, and `fal-ai/qwen-image-2/edit`.

This guide is grounded in the official Qwen blog and official Qwen materials, especially:

- `https://qwen.ai/blog?id=qwen-image-2.0`
- `https://qwenlm.github.io/blog/qwen-image/`

## Core idea

Qwen Image 2 is strongest when you prompt it like a layout brief or exact editing instruction, not a loose mood board.

It is especially strong at:

- visible text rendering
- bilingual or multilingual text
- posters, slides, infographics, and comics
- structured layouts with many text regions
- text replacement and text-aware editing

## Best prompting style

Write literal, structured instructions.

For generation, describe:

1. asset type
2. exact text content
3. text placement
4. visual hierarchy
5. iconography or imagery
6. overall style

For editing, describe:

1. exact operation
2. exact replacement text or change
3. what must stay unchanged

## Rules for visible text

### Use exact quoted text

Put all intended visible text in quotes.

```text
Top title reads "FUTURE FORMS".
Bottom caption reads "Launching in August 2026".
```

### Specify where the text appears

Qwen performs better when you describe placement explicitly.

Useful phrases:

- title at the top center
- subtitle directly below the title
- left column contains
- bottom-right module reads
- handwritten text on the glass board
- shelf tag below the books reads

### Describe text style

Useful descriptors:

- bold sans-serif
- handwritten marker text
- calligraphy
- neon lettering
- chalk lettering
- elegant serif title

## Layout-first prompting

Qwen is a strong choice for posters, PPT-like slides, storefronts, signage, infographics, and other text-heavy assets.

When layout matters, structure the prompt by regions or modules.

Good pattern:

```text
An infographic poster.
At the center, the main title reads "Habits for Emotional Wellbeing".
Top left module reads "Practice Mindfulness" with a lotus icon.
Bottom right module reads "Prioritize Sleep" with a crescent moon icon.
Balanced editorial layout, clean spacing, elegant decorative border, readable typography.
```

## Multilingual prompting

Qwen handles multilingual text well when you keep each phrase literal.

### Rules

- provide exact text for each language
- do not ask it to infer or translate unless that is the task
- separate languages clearly in the prompt
- describe the physical surface carrying the text

Example:

```text
A woman writing on a glass board. The handwritten text on the glass reads "Meet Qwen-Image" and "欢迎了解Qwen-Image" with realistic black marker strokes.
```

## Edit prompting

Qwen edit prompts should be short, literal, and operation-based.

Good verbs:

- replace
- add
- remove
- change
- enhance
- adjust

### Good edit pattern

```text
Replace the text "SALE" with "GRAND OPENING", keeping the same sign position, perspective, and red sans-serif style.
```

### Preservation clauses

Useful constraints:

- keep the font weight unchanged
- keep alignment unchanged
- keep the same perspective
- keep the same background and lighting
- keep the character identity unchanged
- keep the current pose and expression

## Good prompt patterns

### Poster

```text
A movie poster. Top title reads "IMAGINATION UNLEASHED" in bold modern sans-serif lettering. Subtitle directly below reads "Enter a world beyond your imagination". Bottom text reads "Launching in the Cloud, August 2026". At the center, a futuristic computer erupts with radiant colors, surreal creatures, and swirling digital patterns. Sci-fi surrealism, concept-art energy, crisp poster layout, strong readability.
```

### Slide or PPT page

```text
Enterprise presentation slide with a dark blue technology background, glowing data lines, and subtle particle effects. Centered main title reads "Vision Foundation Model" in large white sans-serif type. Subtitle below reads "Native text, complex scenes, automatic layout" in elegant lighter-weight type. Three evenly spaced modules across the bottom, each with an icon, short heading, and two lines of supporting text. Premium enterprise PPT layout, highly readable, balanced spacing.
```

### Storefront or signage

```text
Bookstore window display. A hanging sign reads "New Arrivals This Week". A shelf tag below reads "Best-Selling Novels Here". A colorful poster on the right reads "Author Meet And Greet on Saturday". Warm window display lighting, realistic reflections on glass, crisp typography, believable retail styling.
```

### Text-aware edit

```text
Edit the input poster: replace the main headline with "SUMMER DROP" and keep the same font style, alignment, orange color, poster composition, and background artwork.
```

## When to choose Qwen over other models

- choose Qwen over Flux when text rendering and layout control are central to the task
- choose Qwen over Recraft when you want text-heavy or multilingual assets with stronger literal copy rendering
- choose Qwen over Nano Banana for text replacement, poster editing, slide generation, or infographic-like layouts

## What to avoid

- vague placeholders like `some text` or `title here`
- asking for many text blocks without specifying placement
- expecting the model to invent exact copy when the copy matters
- rewriting a whole image-edit prompt when only a text region needs changing

## Output pattern

When using Qwen, return:

- the final prompt with all visible text preserved exactly
- the quoted text strings listed separately for verification
- the intended layout structure in bullet form when the prompt is complex
- the preservation clauses separately for edit workflows
