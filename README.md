# Veezco MCP server

Find local businesses to sell to — with their contacts, what's wrong with their website, and an opening line for the
call — from Claude, Cursor, VS Code or any MCP client.

Veezco is a lead-generation tool for agencies, freelancers and B2B sellers. You ask for a category and a city
("plumbers in New York", "estate agents in Bristol"); Veezco returns the businesses it found, checks each website
(SEO errors, missing Meta Pixel or Google Analytics, slow, not mobile-friendly, no SSL) and writes an opening line
built on what it measured.

This is a **remote** MCP server (Streamable HTTP). There is nothing to install.

- Endpoint: `https://www.veezco.com/api/mcp`
- Auth: `Authorization: Bearer <your Veezco API key>`
- Get a key: sign up at [veezco.com/en](https://www.veezco.com/en), then Dashboard → Integrations → API keys.

## Tools

| Tool | What it does | Cost |
|---|---|---|
| `search_companies` | Businesses in one city and one category, with contacts, website checks and an opening line. Optional filters (for example `no_meta_pixel`, `no_website`). If the city and category were never collected, a live collection starts and leads appear while it runs (a full collection usually takes 15–30 minutes). | 1 credit per **new** lead; leads you already received are free |
| `list_categories` | The categories already collected in a city, with the date of the latest collection. | Free |
| `get_credits` | Your credit balance and plan. | Free |

Filters only match what Veezco actually measured: a website it could not read never counts as "no Meta Pixel".

## Setup

### Claude Code

```bash
claude mcp add --transport http veezco https://www.veezco.com/api/mcp --header "Authorization: Bearer YOUR_KEY"
```

### Claude Desktop, Cursor, VS Code

```json
{
  "mcpServers": {
    "veezco": {
      "url": "https://www.veezco.com/api/mcp",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

(claude.ai in the browser needs OAuth, which this server does not offer yet.)

## Example prompts

- "Find 10 plumbers in New York without a Meta Pixel and write me a call script for the first three."
- "Which categories does Veezco already have in Dublin?"
- "Give me estate agents in Bristol with SEO errors, sorted by rating."

## Pricing

Free plan to start; paid plans from €19/month. See [veezco.com/en#pricing](https://www.veezco.com/en#pricing).

## Data and privacy

Veezco works from public business information. Contact details are shown only to signed-in users, and only for the
businesses they request.
