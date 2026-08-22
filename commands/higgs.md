---
name: higgs
description: Create, edit, analyze, and manage media with the current Higgsfield MCP tools and canonical workflows.
---

# /higgs

Natural-language entrypoint for Higgsfield. Interpret the request, preserve the user's constraints, and use the current Higgsfield MCP tool descriptions as the source of truth.

## Usage

```
/higgs <natural language request>
```

## Examples

```
/higgs Make a cinematic poster of a samurai in neon Tokyo, 16:9
/higgs Animate this product shot — slow push-in, 5s, 9:16
/higgs Make a 60-second faceless explainer about black holes
/higgs Score this video for engagement and tell me what to fix
/higgs Show my recent generations
/higgs How many credits do I have left?
```

## Routing

- **One image, video, or audio result** → use `generate_image`, `generate_video`, or `generate_audio` directly. Use `models_explore` when the model or its parameters are unclear.
- **Several independent generations** → use the matching batch generation tool and follow its `jobs_wait` and display protocol.
- **Specialized production** → call `get_workflow_instructions` with no workflow first to discover the current catalog, then load and follow the matching canonical workflow. This includes faceless videos, UGC formats, narration, subtitles, thumbnails, brand kits, and character sheets.
- **Edit an existing asset** → prefer the dedicated operation when available, including upscale, outpaint, reframe, background removal, motion control, voice change, or dubbing.
- **Virality or audience-response analysis** → use the MCP virality analysis tool selected by its current description.
- **Library, characters, workspaces, billing, and account requests** → use the matching MCP browse or account tool.

## Media inputs

- For an HTTP(S) media URL, import it before passing the returned media ID to another tool.
- For a local file, use the upload flow exposed by the current MCP client and confirm the upload when required.
- Preserve every supplied reference and its intended role.

Do not turn a generic generation request into a complex workflow. Do not invent tool names, model IDs, parameters, workflow steps, or defaults when MCP can provide them. Follow typed recovery guidance instead of retrying an unchanged failed call.
