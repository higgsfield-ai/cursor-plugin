---
name: virality-prediction
description: Predict virality and analyze engagement, hook strength, retention risk, and audience response of a video using Higgsfield's virality predictor. Use when the user asks "will this go viral", "score this video", "analyze engagement", or wants creative performance feedback.
---

# Virality prediction

Use the Higgsfield MCP `virality_predictor` to forecast how a video will perform — hook strength, retention, attention curves, and audience response.

## When to use

- The user asks to predict or score virality, engagement, attention, audience response, retention, hook strength, or creative performance of a video.
- The user wants feedback before posting to TikTok, Reels, Shorts, YouTube, etc.
- The user wants to compare two cuts of the same video.

## How to use

1. **Get the video into Higgsfield first.**
   - If the video was just generated via `generate_video`, reuse the resulting media reference.
   - If it's a local file, run `media-management` to `media_upload` → `media_confirm` first.
2. **Call `virality_predictor`** with the confirmed media reference.
3. **Render the result** with `job_display` and explain the key signals:
   - Overall virality score
   - Hook strength (first ~3 seconds)
   - Retention risk and where viewers are likely to drop off
   - Audience match and platform suitability
4. **Recommend concrete edits** — re-cut the hook, change the thumbnail frame, adjust pacing, regenerate with a different model — and offer to run those changes via `generate_video`.

## Guardrails

- Don't predict virality without the video actually being uploaded/generated through Higgsfield first. The predictor needs a Higgsfield media reference.
- Report scores as forecasts, not guarantees. Frame recommendations as "likely to improve hook" not "will go viral".
- If the predictor returns low confidence, say so — don't oversell weak signals.

## Examples

```
Will this clip do well on TikTok?
Score this video for engagement and tell me what to fix
Compare these two cuts and predict which one will retain more viewers
```
