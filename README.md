# fal-ai-mcp-creative-studio

A comprehensive skill for using the fal MCP server to discover models, route creative tasks, and run image, video, audio, and multi-step generation workflows with strong prompting, model-specific guidance, and fal-native pipelines.

## What this repo contains

- `SKILL.md`: main skill entrypoint and loading instructions
- `prompts/`: model-specific and task-specific prompt guides
- `reference/`: routing defaults and model tradeoffs
- `workflows/`: reusable fal-native creative pipelines
- `AGENTS.md`: contribution guidance for AI assistants

## What the skill helps with

- verifying fal MCP access before use
- discovering models and choosing the right endpoint
- checking schemas and pricing before generation
- uploading assets and running image, video, and audio jobs
- using better prompt patterns for models like Kling, Wan 2.7, Qwen Image 2, and Seedream
- chaining multi-step workflows like product cutouts, poster generation, still-to-video, and multishot cinematic sequences

## Project principles

- fal MCP first
- fal-native workflows by default
- primary sources over speculation
- routing as defaults, not guarantees
- practical prompts over vague advice

## Contributing

See `AGENTS.md` for project-specific contribution rules.

Important rule:

- use semantic git commits, preferably Conventional Commits such as `feat:`, `fix:`, `docs:`, or `refactor:`
