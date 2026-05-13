---
name: generate-video
description: Generate videos with Higgsfield. Use when the user asks to create, generate, animate, or render a video, clip, ad, or motion piece — from a prompt or from an existing image.
---

# Generate video

Use the Higgsfield MCP server to generate video from text prompts, image references, or uploaded media.

## When to use

- The user asks to "generate", "create", "render", "animate", or "make" a video, clip, ad, reel, or motion piece.
- The user wants to bring a still image to life — animate, add motion, camera movement, etc.
- The user wants to extend or remix an existing video clip.

## How to use

1. **Confirm the workspace** with `list_workspaces` / `select_workspace` if not already selected.
2. **If the user provided a local file**, run `media-management` first to upload and confirm it. Pass the resulting media reference into `generate_video`.
3. **Explore models** with `models_explore` when the request is ambiguous about style (cinematic, animation, talking-head, motion-graphics, etc.). Pick a sensible default otherwise.
4. **Call `generate_video`** with the prompt, model, duration, aspect ratio, and any reference media or character IDs.
5. **Poll with `job_status`** and render the result with `job_display` when ready.
6. **Offer follow-ups**: predict virality with `virality_predictor`, generate variants, or hand off to marketing studio (`show_marketing_studio`).

## Defaults and guardrails

- Video jobs take longer than images. Tell the user it may take a while; do not spam `job_status` more often than every few seconds.
- Don't invent model names, durations, or aspect ratios not returned by `models_explore`.
- Surface the actual failure reason from `job_status` instead of retrying silently.
- Check `balance` before kicking off long jobs if the user has hit quota errors recently.

## Examples

```
Animate this product shot — slow push-in, soft studio light, 5 seconds, 9:16
Generate a 6-second cinematic clip: a samurai walking through neon Tokyo rain
Take this still and turn it into a vertical TikTok-style intro
```
