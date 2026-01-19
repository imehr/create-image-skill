# /create-image Help

## Commands

- `/create-image list`
  - List all templates from `templates/<topic>/<style>`.

- `/create-image generate "<prompt>" --template <topic/style> --output <file>`
  - Optional flags: `--type`, `--provider`, `--model`, `--style-grid`.

- `/create-image styles --template <topic/style>`
  - Show available style reference grids in the template.

- `/create-image style-reference`
  - Start the workflow to generate or select a 2x2 style reference grid.

- `/create-image providers`
  - Show provider selection rules and configuration.

- `/create-image help`
  - Print this help.

## CLI Mapping (image-generator)

All generation uses the image-generator CLI:

```bash
node scripts/generate.js \
  --template <topic/style> \
  --prompt "<description>" \
  --output <file> \
  [--type <image-type>] \
  [--provider gemini|openrouter|vertexai] \
  [--model <model-name>] \
  [--style-grid <path-or-name>]
```

List style references for a template:

```bash
node scripts/generate.js --template <topic/style> --styles
```

## Style Reference Requirement (Nano Banana Pro)

Gemini 3 Pro Image (Nano Banana Pro) **requires** a style reference grid.
If missing, generate it first using `/create-image style-reference`.

## Examples

```bash
# List templates
node scripts/generate.js --list

# List style references for a template
node scripts/generate.js --template sports/illustrative --styles

# Generate with named style grid
node scripts/generate.js \
  --template sports/illustrative \
  --prompt "Player serving the ball" \
  --output serve.png \
  --style-grid modern-minimalist-01

# Force provider (Vertex AI)
node scripts/generate.js \
  --template sports/illustrative \
  --prompt "Top-down court view" \
  --output court.png \
  --provider vertexai \
  --model gemini-3-pro-image-preview
```
