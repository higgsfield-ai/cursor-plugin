---
name: higgs
description: Run Higgsfield workflows in natural language — generate images and videos, predict virality, manage media, check your account.
---

# /higgs

Natural-language entrypoint for Higgsfield. Routes to the right MCP tool.

## Usage

```
/higgs <natural language request>
```

## Examples

```
/higgs Make a cinematic poster of a samurai in neon Tokyo, 16:9
/higgs Animate this product shot — slow push-in, 5s, 9:16
/higgs Score this video for engagement and tell me what to fix
/higgs Show my recent generations
/higgs How many credits do I have left?
```

## What's available

- **Images / video** → `generate_image`, `generate_video`
- **Virality** → `virality_predictor`
- **Local files** → `media_upload` + `media_confirm` first
- **Library / account** → `show_generations`, `show_characters`, `balance`, `show_plans_and_credits`
- **More** → marketing studio, personal clipper, characters, workspaces, transactions, and other Higgsfield MCP tools
