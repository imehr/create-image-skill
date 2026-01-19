---
name: create-image
description: Generate AI images with templates and style references. Use when creating images/illustrations/diagrams, managing templates or style references, choosing image providers (Gemini, OpenRouter, VertexAI), or when the user mentions /create-image (including /create-image help).
---

# Create Image

Generate consistent, branded images using templates and style reference grids.

## Quick Start

```bash
cd /Users/mehran/Documents/github/image-generator
node scripts/generate.js --list

node scripts/generate.js \
  --template sports/illustrative \
  --prompt "Top-down view showing service courts" \
  --output output.png \
  --style-grid modern-minimalist-01
```

## Available Style References (sports/illustrative)

These are pre-generated 2x2 grids:

- `modern-minimalist-01`
- `modern-minimalist-02`
- `modern-minimalist-young-athletes-01`
- `modern-minimalist-young-athletes-02-social-creator`
- `neo-editorial-01`
- `premium-luxury-02`

Use them with `--style-grid <name>`.

**Company style grids:** Save grids with the company name (e.g., `acme.png`) and
use `--style-grid acme` to apply that brand style for a batch.

## Commands

- `/create-image list`
  - List available templates (maps to `node scripts/generate.js --list`).

- `/create-image generate "<prompt>" --template <topic/style> --output <file>`
  - Optional flags: `--type`, `--provider`, `--model`, `--style-grid`.

- `/create-image styles --template <topic/style>`
  - List available style reference grids in `templates/<topic>/<style>/style-references/`.

- `/create-image style-reference`
  - Start the style reference workflow (see below). Use when a style grid is missing.

- `/create-image providers`
  - Show provider configuration and selection rules (see references/provider-config.md).

- `/create-image help`
  - Print the full help documentation (use references/help.md).

## Hard Requirement: Style Reference for Gemini 3 Pro Image (Nano Banana Pro)

If you are using Gemini 3 Pro Image (Gemini API, OpenRouter, or VertexAI), a style
reference grid is mandatory. If a style grid does not exist, generate it first
using the style reference workflow below.

## Style Reference Workflow (High Level)

1. Identify target audience, brand style, and imagery scope.
2. Choose a grid prompt from `references/style-reference-prompts.md` and customize it.
3. Generate a 2x2 grid image with your chosen provider.
4. Save the grid as `templates/<topic>/<style>/style-references/<name>.png`.
5. Use `--style-grid <name>` for all future images to lock in style consistency.

## References

- Full help: `references/help.md`
- Style grid prompts: `references/style-reference-prompts.md`
- Provider selection and config: `references/provider-config.md`
