---
name: media-management
description: Upload local media to Higgsfield and browse existing generations, characters, and media. Use this BEFORE generate-video or virality-prediction whenever the user references a local image or video file.
---

# Media management

Handle the data plumbing between local files and Higgsfield: uploading, confirming, and browsing.

## When to use

- The user references a local file path or attaches an image/video and wants to use it as input to `generate_video`, `generate_image` (as reference), or `virality_predictor`.
- The user asks to see their existing generations, characters, uploaded media, or marketing studio assets.
- The user asks about their plan, credits, balance, or transaction history.

## Uploading a local file

1. Call `media_upload` with the local path. This returns an upload handle.
2. Call `media_confirm` with that handle to finalize. This returns a Higgsfield media reference.
3. Pass that reference into the downstream tool (`generate_video`, `virality_predictor`, etc.).

Always do both steps — `media_upload` alone does not produce a usable reference.

## Browsing

- `show_generations` — past image/video generations.
- `show_medias` — uploaded media library.
- `show_characters` — saved characters.
- `show_marketing_studio` — marketing studio assets.
- `list_workspaces` / `select_workspace` — switch context if the user has multiple workspaces.

## Account / billing

- `balance` — current credit balance.
- `show_plans_and_credits` — plan info and credit packs.
- `transactions` — billing history.

Use these when the user asks "how many credits do I have", "what plan am I on", "did the last job get charged", or hits a quota error.

## Guardrails

- Don't assume a local path is accessible — if `media_upload` fails, surface the error and ask the user to re-share or check the path.
- Don't browse the entire library when the user asks for a specific item. Filter by name or recency first.
