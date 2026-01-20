# Provider Selection and Configuration

This skill uses the image-generator repository at:
`/Users/mehran/Documents/github/image-generator`

## Supported Providers (Current)

### 1) Gemini API (Direct)
- **Provider flag:** `--provider gemini`
- **Default model:** `gemini-3-pro-image-preview` (Nano Banana Pro)
- **Env var:** `GOOGLE_API_KEY` (or `GOOGLE_GENERATIVE_AI_API_KEY`)

### 2) OpenRouter
- **Provider flag:** `--provider openrouter`
- **Default model:** `google/gemini-3-pro-image-preview` (Nano Banana Pro)
- **Env var:** `OPENROUTER_API_KEY`

### 3) VertexAI (Gemini 3 Pro Image)
- **Provider flag:** `--provider vertexai`
- **Default model:** `gemini-3-pro-image-preview` (Nano Banana Pro)
- **Env vars:**
  - `GOOGLE_CLOUD_PROJECT` (required)
  - `GOOGLE_CLOUD_LOCATION` (optional, default: `global`)
- **Auth:** Application Default Credentials or `GOOGLE_APPLICATION_CREDENTIALS`

## Recommended Defaults (Nano Banana Pro)

Set one of the following for Nano Banana Pro:

- Gemini API:
  - `GOOGLE_API_KEY=<key>`
  - Optional model override: `GEMINI_MODEL=gemini-3-pro-image-preview`

- OpenRouter:
  - `OPENROUTER_API_KEY=<key>`
  - Optional model override: `OPENROUTER_MODEL=google/gemini-3-pro-image-preview`

- VertexAI:
  - `GOOGLE_CLOUD_PROJECT=<project>`
  - `GOOGLE_CLOUD_LOCATION=global`
  - Optional model override: `VERTEX_MODEL=gemini-3-pro-image-preview`

## Provider Selection Rules

1. If `--provider` is specified, use that provider.
2. Otherwise, auto-select based on available environment variables:
   - Gemini (`GOOGLE_API_KEY`)
   - VertexAI (`GOOGLE_CLOUD_PROJECT`)
   - OpenRouter (`OPENROUTER_API_KEY`)

## Hard Requirement

Gemini 3 Pro Image (Nano Banana Pro) requires a **style reference grid**. If not present,
run the style reference workflow first and supply `--style-grid`.
