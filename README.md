# Vacay Directory MCP servers

Free, read-only [Model Context Protocol](https://modelcontextprotocol.io) servers for four curated local directories. No API key or sign-in is required. Responses contain public listing data only.

| Directory | Coverage | MCP endpoint (Streamable HTTP) | OpenAPI |
|---|---|---|---|
| [VailVacay](https://www.vailvacay.com) | Vail Valley, Colorado: restaurants, hotels, bars and nightlife, activities, shopping, services, wellness | `https://vailvacay-connector.michael-b38.workers.dev/mcp` | [openapi.json](https://vailvacay-connector.michael-b38.workers.dev/v1/openapi.json) |
| [BangkokVacay](https://www.bangkokvacay.com) | Bangkok, Thailand: tours, activities, hotels, restaurants, nightlife, shopping, spas | `https://bangkokvacay-connector.michael-b38.workers.dev/mcp` | [openapi.json](https://bangkokvacay-connector.michael-b38.workers.dev/v1/openapi.json) |
| [BostonVacay](https://www.bostonvacay.com) | Boston, Massachusetts: tours, activities, hotels, restaurants, nightlife, shopping | `https://bostonvacay-connector.michael-b38.workers.dev/mcp` | [openapi.json](https://bostonvacay-connector.michael-b38.workers.dev/v1/openapi.json) |
| [1-800Deals](https://1-800deals.com) | US directory of 1-800 / toll-free / vanity-number home service and other businesses | `https://1800deals-connector.michael-b38.workers.dev/mcp` | [openapi.json](https://1800deals-connector.michael-b38.workers.dev/v1/openapi.json) |

## Tools

Every server exposes the same two tools:

- `search_listings`: keyword and category search over the directory's listings.
- `list_categories`: the categories available to filter by.

Each record includes public fields such as name, description, address, coordinates, phone, website, business hours, FAQs, photos and booking links. Only active listings with real descriptions, photos and locations are served.

## Use it

**Claude:** Settings, Integrations, add a custom MCP server, paste the endpoint URL.

**Any MCP client:** point it at the endpoint above using the Streamable HTTP transport.

**Quick test:**

```bash
curl -s -X POST https://vailvacay-connector.michael-b38.workers.dev/mcp \
  -H "content-type: application/json" -H "accept: application/json, text/event-stream" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list"}'
```

**REST:** each server also serves an OpenAPI 3.0 description at `/v1/openapi.json`.

## Registry

Published in the [Official MCP Registry](https://registry.modelcontextprotocol.io) as `io.github.cloudalien2025/vailvacay-directory`, `bangkokvacay-directory`, `bostonvacay-directory` and `1800deals-directory`. The `server.json` files are in [`registry/`](registry).

## About the data

Listings are written from each business's own website and public sources. The directories are independent and not affiliated with the businesses they list. Check hours and prices with the business before you go.
