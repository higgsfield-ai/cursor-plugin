# Higgsfield for Cursor

Generate images, videos, and more using Higgsfield MCP from Cursor.

## Installation

### Cursor Marketplace

In Cursor, type `/add-plugin` in chat, search for **Higgsfield**, and install it.

You can also install directly from [Cursor Marketplace](https://cursor.com/marketplace/higgsfield).

### From source (local development)

Cursor scans `~/.cursor/plugins/local/<plugin-name>/` for local plugins. Copy this repo into that directory:

```bash
git clone https://github.com/higgsfield-ai/cursor-plugin.git
mkdir -p ~/.cursor/plugins/local
rsync -a --delete --exclude='.git' cursor-plugin/ ~/.cursor/plugins/local/higgsfield/
```

Reload Cursor: `Cmd-Shift-P → Developer: Reload Window`.

Verify:

- `Cursor Settings → Plugins` lists **Higgsfield**.
- `Cursor Settings → Tools & MCPs` shows `higgsfield` with a green dot. The first connection prompts authentication.

> **Note**: use a real directory copy; symlinks may not load.

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

## License

See [LICENSE](./LICENSE).

## Support

- Issues: [github.com/higgsfield-ai/cursor-plugin/issues](https://github.com/higgsfield-ai/cursor-plugin/issues)
- Contact: support@higgsfield.ai
