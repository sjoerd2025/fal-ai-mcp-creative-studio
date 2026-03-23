# AGENTS

This repository contains a reusable `fal-ai-mcp-creative-studio` skill for AI assistants. The project is documentation-first: the main job is to improve the skill's instructions, routing, model guidance, and workflow examples without drifting away from real fal MCP behavior.

## What this project contains

- `SKILL.md`: the main skill entrypoint with frontmatter and execution rules
- `prompts/`: task-specific and model-specific prompting guides
- `reference/`: routing logic, model tradeoffs, and specialist notes
- `workflows/`: reusable creative pipelines and orchestration patterns

## Contribution goals

When contributing, optimize for:

- accurate fal MCP usage
- current model routing
- practical prompting guidance
- fal-native workflows over external-tool stacks
- clear, reusable instructions for AI agents

## Source quality rules

- Prefer primary sources first: fal docs, fal model schemas, fal blog posts, and official model-maker documentation.
- Use community sources such as Reddit, X, or shared workflows as secondary signals, not as the only source of truth.
- If a model catalog or workflow may have changed, write guidance that tells the agent to re-check live availability with fal MCP.
- Do not present uncertain model guidance as hard fact.

## Editing rules

- Preserve the skill's focus on using the fal MCP server.
- Keep default recommendations inside fal-supported models and utilities unless a change explicitly documents an optional external reference.
- Prefer additive, modular updates over rewriting the whole skill.
- Keep examples practical and reusable.
- Maintain the distinction between routing, prompting, and workflows.
- Keep frontmatter descriptions focused on when the agent should load the skill.

## File-specific guidance

### `SKILL.md`

- Keep the frontmatter concise and auto-load friendly.
- The skill must instruct the agent to verify fal MCP access before trying to use fal tools.
- Keep setup guidance generic unless it is specifically about Alter behavior already documented in the repo.

### `prompts/`

- Each file should teach a distinct prompting pattern.
- Model-specific guides should be based on official guidance whenever possible.
- Prefer concrete prompt templates and examples over abstract advice alone.

### `reference/`

- Treat routing recommendations as defaults, not guarantees.
- Bias toward live discovery with `recommend_model`, `search_models`, `get_model_schema`, and `get_pricing`.
- Keep tradeoffs explicit: speed, quality, control, cost, and workflow fit.

### `workflows/`

- Keep workflows fal-native by default.
- Prefer sequences the agent can actually execute through fal MCP.
- Document why a workflow works, not just the step list.

## Commit rules

- Use semantic git commits.
- Prefer Conventional Commit style such as:
  - `feat: add qwen image 2 prompting guide`
  - `fix: correct fal model routing defaults`
  - `docs: clarify alter mcp enablement step`
  - `refactor: reorganize workflow examples`

## Good contribution examples

- adding a new model-specific prompt guide from an official source
- correcting outdated endpoint routing
- improving a workflow so it stays inside fal-supported tools
- tightening the frontmatter so the skill auto-loads more reliably

## Changes to avoid

- adding speculative model recommendations with no source basis
- introducing external-tool dependencies as the default workflow
- duplicating guidance that belongs in another file
- weakening the requirement to verify fal MCP access first
