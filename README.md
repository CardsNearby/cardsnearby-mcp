# CardsNearby MCP Server

Connect Claude, Cursor, and other [Model Context Protocol](https://modelcontextprotocol.io) agents to **[CardsNearby](https://www.cardsnearby.com)** — the directory of every local card shop and card show in the United States (sports cards, Pokémon, Magic: The Gathering, Yu-Gi-Oh!, and other TCGs).

Ask your AI assistant for card shops or card shows near any US location and it queries CardsNearby's live data directly.

- **Endpoint:** `https://www.cardsnearby.com/api/mcp`
- **Transport:** Streamable HTTP (JSON-RPC 2.0)
- **Auth:** none — free, read-only
- **Homepage:** https://www.cardsnearby.com
- **Docs:** https://www.cardsnearby.com/mcp

## Tools

| Tool | What it does |
| --- | --- |
| `find_card_shops` | Find local card shops near a location (by `latitude`+`longitude` or US `city`+`state`). Returns shops sorted by distance with address, games, services, rating, phone, and link. |
| `find_card_shows` | Find upcoming card shows/conventions near a location. Returns shows with venue, next date, games, and link. |
| `list_coverage` | List the US states covered and how many card shops are in each. |

## Setup

### Cursor (and other clients with native remote MCP)

Add to your `mcp.json`:

```json
{
  "mcpServers": {
    "cardsnearby": {
      "url": "https://www.cardsnearby.com/api/mcp"
    }
  }
}
```

### Claude Desktop (bridge a remote server over stdio)

```json
{
  "mcpServers": {
    "cardsnearby": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://www.cardsnearby.com/api/mcp"]
    }
  }
}
```

## Example prompts

- "Find card shops near Charlotte, NC that buy collections."
- "Are there any card shows within 50 miles of Dallas this month?"
- "Which states does CardsNearby cover, and where are the most shops?"

## About

Built by [CardsNearby](https://www.cardsnearby.com) — find every US card shop and card show, with hours, games carried, buylists, grading drop-offs, and show dates. Data is read-only and refreshed continuously.

## License

MIT
