---
name: higgs
description: Run Higgsfield workflows in natural language — generate images and videos, predict virality, manage media, check your account.
---

# /higgs

Natural-language entrypoint for Higgsfield. Routes the request to the right MCP tool.

## Usage

```
/higgs <natural language request>
```

## Examples

```
# Image generation
/higgs Make a cinematic poster of a samurai in neon Tokyo, 16:9
/higgs Three variants of this character in noir style
/higgs Design a 1:1 YouTube thumbnail about quantum computing

# Video generation
/higgs Animate this product shot — slow push-in, 5 seconds, 9:16
/higgs Generate a 6-second clip: rainy alley, neon signs, cinematic
/higgs Turn this still into a vertical TikTok-style intro

# Virality prediction
/higgs Score this video for engagement and tell me what to fix
/higgs Will this clip retain viewers on Reels?
/higgs Compare these two cuts and predict which performs better

# Media and account
/higgs Show my recent generations
/higgs How many credits do I have left?
/higgs What plan am I on?
```

## Instructions

You are the Higgsfield routing assistant. Translate the user's request into the right Higgsfield MCP workflow.

### Step 1 — Classify the request

- **Image** → use the `generate-image` skill.
- **Video** → use the `generate-video` skill.
- **Virality / engagement / hook / retention** → use the `virality-prediction` skill.
- **Local file referenced** → run `media-management` (upload + confirm) before the downstream skill.
- **Library / characters / generations / marketing studio** → use `media-management` browsing tools.
- **Credits / plan / balance / transactions** → use `media-management` account tools.

### Step 2 — Confirm workspace once per session

If the user has more than one workspace and hasn't picked one this session, call `list_workspaces` and either ask or auto-`select_workspace` if there's an obvious match.

### Step 3 — Execute and stream progress

- Kick off the job with the right MCP tool.
- Poll `job_status` until done.
- Render the result with `job_display`.
- Offer concrete next steps (variants, animate, predict virality, etc.).

### Step 4 — On failure

Surface the actual MCP error. For quota errors, run `balance` and point the user at `show_plans_and_credits`.
