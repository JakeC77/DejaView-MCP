# dejaview-mcp

Persistent knowledge graph memory for AI agents — an [MCP](https://modelcontextprotocol.io) server backed by [DejaView](https://dejaview.io).

Connect Claude Desktop, Cursor, Windsurf, or any MCP-compatible host to a live knowledge graph. Your AI remembers people, projects, decisions, and relationships across every session.

Get your free API key at **[dejaview.io](https://dejaview.io)**.

---

## Option 1: Cloud (no install required) ⚡

The fastest way to get started — no `pip install`, no local process.

```json
{
  "mcpServers": {
    "dejaview": {
      "type": "streamable-http",
      "url": "https://api.dejaview.io/mcp",
      "headers": {
        "Authorization": "Bearer dv_your_key_here"
      }
    }
  }
}
```

Paste this into your Claude Desktop, Cursor, or Windsurf MCP config. Done.

---

## Option 2: Local (pip install)

If you prefer to run the server locally:

```bash
pip install dejaview-mcp
```

Add to your config:

```json
{
  "mcpServers": {
    "dejaview": {
      "command": "dejaview-mcp",
      "env": {
        "DEJAVIEW_API_KEY": "dv_your_key_here"
      }
    }
  }
}
```

Config file locations:
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Linux:** `~/.config/claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

---

## What it does

DejaView gives your AI a persistent knowledge graph it can read from and write to across sessions. Unlike flat context windows that reset every chat, the graph grows over time.

| Tool | What it does |
|------|-------------|
| `agent_context` | Load a full memory summary at session start |
| `remember` | Store a fact (subject, predicate, object) |
| `remember_many` | Store multiple facts at once |
| `recall` | Get everything known about an entity |
| `search` | Find entities by name |
| `ask` | Natural language Q&A over the graph with citations |
| `timeline` | See recently stored facts |
| `graph_stats` | Entity and relationship counts |
| `share` | Generate a public shareable link for any entity |
| `forget` | Remove a specific fact |
| `forget_entity` | Remove an entity and all its connections |

## Example

Once connected, just chat naturally:

> "Remember that Alice is the lead on Project Atlas and prefers async communication."

The agent calls `remember()` automatically. Next session:

> "What do I know about Alice?"

The agent calls `recall("Alice")` and tells you everything — including things you told it months ago.

---

## Self-hosting

Want to run your own DejaView instance? The API is open source:
[github.com/JakeC77/DejaView](https://github.com/JakeC77/DejaView)

Set `DEJAVIEW_ENDPOINT` to point at your instance:

```bash
DEJAVIEW_API_KEY=dv_... DEJAVIEW_ENDPOINT=https://your-instance.com dejaview-mcp
```

## Links

- **Website:** [dejaview.io](https://dejaview.io)
- **API:** [api.dejaview.io/docs](https://api.dejaview.io/docs)
- **GitHub:** [github.com/JakeC77/DejaView-MCP](https://github.com/JakeC77/DejaView-MCP)
