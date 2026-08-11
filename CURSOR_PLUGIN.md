# Freedom OS — Cursor plugin

Installable Cursor Marketplace packaging for the hosted FreedomOS MCP (`com.getfreedomos/freedom-mcp`).

## For users

1. Install **Freedom OS** from the Cursor Marketplace (or Grok Bot connectors).
2. Create a personal key at [getfreedomos.com/mcp](https://getfreedomos.com/mcp).
3. In **Plugins → Configure**, set **Freedom OS personal key** (`FREEDOMOS_API_KEY`).

Endpoint (already wired in `mcp.json`):

```
https://twuluxmoognlwtmaoqgo.supabase.co/functions/v1/freedom-mcp
Authorization: Bearer <your key>
```

## For maintainers

Submit this repository at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) after merging plugin files.

Local test: copy the plugin root (this repo) to `~/.cursor/plugins/local/freedom-os`, then reload Cursor.
