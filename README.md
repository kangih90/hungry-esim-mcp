# Hungry eSIM — MCP Server

Buy and manage travel eSIMs from AI assistants like Claude, Cursor, and VS Code via the [Model Context Protocol](https://modelcontextprotocol.io).

**Endpoint:** `https://api.hungry-esim.com/mcp` (remote, streamable HTTP — no install, no API key)

Unlimited data plans where you pick your days, top-ups for eSIMs you already own, and plain credit-card checkout on [hungry-esim.com](https://hungry-esim.com). No crypto wallet, no prepaid balance, no API key required.

> This repository is the public home of the server: docs, manifest, and setup guides. The server itself is a hosted remote service.

## What you can do

| Tool | What it does | Auth |
|---|---|---|
| `search_esim_plans` | Search travel eSIM data plans by destination, data amount, and validity | — |
| `check_destination_coverage` | "Does it work in …?" — coverage check for a destination with representative plans | — |
| `find_cheapest_plan` | Cheapest plan(s) for a destination and trip length (total-trip cost ranking) | — |
| `get_plan_details` | Full details for one plan (coverage, speed, top-up support) | — |
| `create_checkout` | Create a card checkout link for a plan — for unlimited plans, choose how many days | — |
| `get_order_status` | Check an order and eSIM installation status | — |
| `my_esims` | List eSIMs on your account with status and usage | OAuth |
| `my_orders` | List your past orders | OAuth |
| `list_esim_topups` | Top-up options for an eSIM you already own | OAuth |
| `topup_esim` | Buy a top-up for an existing eSIM — no new QR code needed | OAuth |

Public tools work immediately with no sign-in. Account tools use OAuth: the assistant sends you to hungry-esim.com to sign in once, then can see your eSIMs and orders.

Payment always happens on hungry-esim.com in a normal browser checkout with a credit card. The assistant never touches your payment details.

## Setup

### Claude (claude.ai / Claude Desktop)

Settings → Connectors → **Add custom connector** → paste:

```
https://api.hungry-esim.com/mcp
```

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "hungry-esim": {
      "url": "https://api.hungry-esim.com/mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)

Add to your `mcp.json` (Command Palette → “MCP: Add Server” → HTTP):

```json
{
  "servers": {
    "hungry-esim": {
      "type": "http",
      "url": "https://api.hungry-esim.com/mcp"
    }
  }
}
```

Then ask things like:

- *“I’m going to Japan for 10 days — find me an eSIM with unlimited data.”*
- *“What’s the cheapest data plan for France?”*
- *“Top up the eSIM I bought last month.”*

## Registry listings

- Official MCP Registry: `com.hungry-esim/esim`
- [Smithery](https://smithery.ai)

The manifest in this repo ([`server.json`](./server.json)) mirrors the official registry entry.

## Support

- Guides for agents and humans: [hungry-esim.com/for-agents](https://hungry-esim.com/for-agents)
- Email: support@hungryesim.com (24/7 intake, replies usually within 24 hours)

## License

Docs in this repository are released under the [MIT License](./LICENSE).
