# dejaview-mcp

Persistent knowledge graph memory for AI agents — an [MCP](https://modelcontextprotocol.io) server backed by [DejaView](https://dejaview.io).

Connect Claude Desktop, Cursor, Windsurf, or any MCP-compatible host to a live knowledge graph. Your AI remembers people, projects, decisions, and relationships across every session.

## Install

```bash
pip install dejaview-mcp
```

Get a free API key at **[dejaview.io](https://dejaview.io)**.

## Quick start

```bash
DEJAVIEW_API_KEY=dv_your_key_here dejaview-mcp
```

## Configure Claude Desktop

Edit your Claude Desktop config file:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Linux:** `~/.config/claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

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

Restart Claude Desktop. DejaView will appear in the tools panel.

## Configure Cursor / Windsurf

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

## What it does

DejaView gives your AI a persistent knowledge graph it can read from and write to across sessions. Unlike flat context windows that reset every chat, the graph grows over time.

| Tool | What it does |
|------|-------------|
| `agent_context()` | Load a full memory summary at session start |
| `remember(subject, predicate, object)` | Store a fact |
| `remember_many(facts)` | Store multiple facts at once |
| `recall(entity)` | Get everything known about an entity |
| `search(query)` | Find entities by name |
| `ask(question)` | Natural language Q&A over the graph |
| `timeline()` | See recently stored facts |
| `graph_stats()` | Entity/relationship counts |
| `share(entity)` | Generate a public shareable link |
| `forget(subject, predicate, object)` | Remove a specific fact |
| `forget_entity(name)` | Remove an entity and all its connections |

## Example

Once connected, just chat naturally:

> "Remember that Alice is the lead on Project Atlas and prefers async communication."

The agent calls `remember()` automatically. Next session:

> "What do I know about Alice?"

The agent calls `recall("Alice")` and tells you everything — including things you told it months ago.

## Self-hosting

Want to run your own DejaView instance? The API is open source:
[github.com/JakeC77/DejaView](https://github.com/JakeC77/DejaView)

Set `DEJAVIEW_ENDPOINT` to point at your instance:

```bash
DEJAVIEW_API_KEY=dv_... DEJAVIEW_ENDPOINT=https://your-instance.com dejaview-mcp
```

## Links

- **Website:** [dejaview.io](https://dejaview.io)
- **API:** [api.dejaview.io](https://api.dejaview.io/docs)
- **GitHub:** [github.com/JakeC77/DejaView](https://github.com/JakeC77/DejaView)
