# Higgsfield for Cursor

Generate images and videos, predict virality, and manage Higgsfield media from your editor.

This plugin wires the [Higgsfield MCP](https://higgsfield.ai/mcp) into Cursor and ships opinionated skills so the agent knows _when_ and _how_ to use it.

## What you can do

**Generate images** — cinematic posters, characters, thumbnails, illustrations.

```
Make a cinematic poster of a lone astronaut on a red dune, 16:9, photorealistic
Three variants of this character in a noir style
Design a 1:1 YouTube thumbnail about quantum computing
```

**Generate videos** — from a prompt, an image, or an uploaded clip.

```
Animate this product shot — slow push-in, 5 seconds, 9:16
Generate a 6-second cinematic clip: rainy alley, neon signs
Turn this still into a vertical TikTok-style intro
```

**Predict virality** — hook strength, retention, audience response.

```
/higgs Score this video for engagement and tell me what to fix
/higgs Will this clip retain viewers on Reels?
```

**Manage media and account** — uploads, library, characters, credits.

```
/higgs Show my recent generations
/higgs How many credits do I have left?
```

## Installation

### Cursor Marketplace

Search for **Higgsfield** in `Cursor Settings → Plugins` and click install.

### From source (local install)

Cursor scans `~/.cursor/plugins/local/<plugin-name>/` for user-installed plugins. Copy this repo into that directory:

```bash
git clone https://github.com/higgsfield-ai/cursor-plugin.git
mkdir -p ~/.cursor/plugins/local
rsync -a --delete --exclude='.git' cursor-plugin/ ~/.cursor/plugins/local/higgsfield/
```

Reload Cursor: `Cmd-Shift-P → Developer: Reload Window`.

Verify:

- `Cursor Settings → Plugins` lists **Higgsfield**.
- `Cursor Settings → MCP & Integrations` shows `higgsfield` with a green dot. The first connection prompts OAuth at `mcp.higgsfield.ai`.

> **Note**: a `ln -s` symlink into `~/.cursor/plugins/local/` is not picked up reliably by current Cursor builds — use a real directory copy.

#### Updating

After pulling new commits, re-run the rsync and reload Cursor:

```bash
cd cursor-plugin && git pull
rsync -a --delete --exclude='.git' ./ ~/.cursor/plugins/local/higgsfield/
```

#### Uninstall

```bash
rm -rf ~/.cursor/plugins/local/higgsfield
```

then reload Cursor.

## What's in this plugin

- **MCP server** (`mcp.json`) — remote HTTP MCP at `https://mcp.higgsfield.ai/mcp` (see [higgsfield.ai/mcp](https://higgsfield.ai/mcp) for details). Authentication is handled by the server.
- **Skills** (`skills/`) — `generate-image`, `generate-video`, `virality-prediction`, `media-management`. Each tells the agent _when_ to use the MCP tools and _how_ to chain them.
- **Rule** (`rules/higgsfield-usage.mdc`) — agent guardrails: prefer MCP tools, upload local media first, poll jobs, surface real errors.
- **Command** (`commands/higgs.md`) — `/higgs` natural-language entrypoint that routes to the right skill.

## MCP tools exposed

`generate_image`, `generate_video`, `virality_predictor`, `media_upload`, `media_confirm`, `job_status`, `job_display`, `list_workspaces`, `select_workspace`, `models_explore`, `show_generations`, `show_medias`, `show_characters`, `show_marketing_studio`, `show_plans_and_credits`, `balance`, `transactions`.

## Authentication

The MCP server handles auth. The first request will walk you through sign-in. After that, the session is persisted by the server.

## Repository layout

```
.cursor-plugin/plugin.json     # plugin manifest (schema-validated)
mcp.json                       # remote HTTP MCP config
skills/<name>/SKILL.md         # agent skills
rules/higgsfield-usage.mdc     # agent guardrails
commands/higgs.md              # /higgs slash command
assets/logo.png                # marketplace logo
```

## License

MIT — see [LICENSE](./LICENSE).

## Support

- Issues: [github.com/higgsfield-ai/cursor-plugin/issues](https://github.com/higgsfield-ai/cursor-plugin/issues)
- Contact: support@higgsfield.ai
