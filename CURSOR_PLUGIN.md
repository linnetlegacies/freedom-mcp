# Freedom OS — Cursor plugin

Installable Cursor Marketplace packaging for the hosted FreedomOS MCP (`com.getfreedomos/freedom-mcp`).

## For users

**OAuth Connect (Claude, ChatGPT, Claude Code):** add [`https://getfreedomos.com/api/mcp`](https://getfreedomos.com/api/mcp). The server advertises RFC 9728 OAuth discovery; the host sends you to sign in. No personal key.

**Cursor (this plugin) is a static-header host** — use a personal key:

1. Install **Freedom OS** from the Cursor Marketplace (or Grok Bot connectors).
2. Create a personal key at [getfreedomos.com/mcp](https://getfreedomos.com/mcp).
3. In **Plugins → Configure**, set **Freedom OS personal key** (`FREEDOMOS_API_KEY`).

Endpoint (already wired in `mcp.json`):

```
https://getfreedomos.com/api/mcp
Authorization: Bearer <your key>   # Cursor / static-header fallback
```

## For maintainers

Submit this repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) after merging plugin files.

Local test: copy the plugin root (this repo) to `~/.cursor/plugins/local/freedom-os`, then reload Cursor.
