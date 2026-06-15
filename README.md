# Russian Web Data Access for AI Agents

Remote **MCP server** + REST API to fetch content from Russian websites through a Russian IP.

- **Live service:** https://ruscrape.com
- **MCP endpoint (streamable-http):** https://ruscrape.com/mcp
- **Official MCP Registry:** `com.ruscrape/russia-access`

## What it does

Give a URL of **any Russian website or API** — get its content (HTML/JSON) back, fetched through a
Russia-based IP. Works on sites that block foreign traffic: **Wildberries, Ozon, Yandex Market,
government registries (EGRUL/FNS), banks**.

Built for **autonomous AI agents**: no human signup, pay-per-use via HTTP 402 (x402/USDC) or RUB.

## Flagship MCP tool

```
fetch_ru(agent_id, url, residential=false)   # URL in, content out
```
Set `residential=true` for sites that block datacenter IPs (Wildberries / Ozon / cbr.ru).

Other tools: `get_ru_proxy`, `check_domain`, `register_ru_domain`, `topup_balance`, `check_balance`.

## Connect

Add a remote MCP server pointing at `https://ruscrape.com/mcp` (transport: `streamable-http`).

## Machine-readable

| Resource | URL |
|---|---|
| MCP manifest | https://ruscrape.com/.well-known/mcp.json |
| llms.txt | https://ruscrape.com/llms.txt |
| OpenAPI | https://ruscrape.com/openapi.json |
| Pricing | https://ruscrape.com/pricing |
| Plugin manifest | https://ruscrape.com/.well-known/ai-plugin.json |

## Payment

On `HTTP 402 Payment Required`, pay (USDC via x402 or RUB), then retry. `Idempotency-Key` supported.
Top up: `POST /v1/balance/topup`. Check balance: `GET /v1/balance`.
