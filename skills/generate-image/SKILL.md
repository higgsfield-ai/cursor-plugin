---
name: generate-image
description: Generate images with Higgsfield. Use when the user asks to create, generate, render, or design an image, illustration, poster, character, scene, or visual concept.
---

# Generate image

Use the Higgsfield MCP server to generate images from natural-language prompts.

## When to use

- The user asks to "generate", "create", "render", "make", or "design" an image, illustration, poster, character, scene, thumbnail, or visual.
- The user references styling like "cinematic", "photorealistic", "3D", "anime", "studio lighting", etc.
- The user wants variants of an existing image (pass the source via `media_upload` first — see `media-management`).

## How to use

1. **Confirm the workspace** if the user hasn't picked one. Call `list_workspaces`; if more than one, call `select_workspace`.
2. **Explore models** with `models_explore` when the user is unsure which model fits the request (photoreal vs. illustrative, fast vs. high-fidelity, character-consistent, etc.). Pick a sensible default if the user doesn't care.
3. **Call `generate_image`** with the user's prompt. Pass aspect ratio, model, and any reference media the user supplied.
4. **Poll the job** with `job_status` until the result is ready. Use `job_display` to surface the generated image inline.
5. **Offer next steps** — variants, upscales, animating the image into a video (`generate_video`), or a virality forecast (`virality_predictor`) once it's a video.

## Defaults and guardrails

- Don't invent model names or parameters not returned by `models_explore`.
- If a generation fails, surface the actual error from `job_status` rather than re-prompting blindly.
- Before any generation, confirm the user has credits via `balance` if they ask "can I run this" or hit a quota error.
- Keep prompts under ~400 characters unless the user has provided a longer brief.

## Examples

```
Generate a cinematic poster of a lone astronaut on a red dune at sunset, 16:9, photorealistic
Make me three variations of this character but in a noir style
Design a square YouTube thumbnail for a video about quantum computing — bold, high contrast
```
