# Avant Watch

Read-only monitoring data on [Avant Protocol](https://docs.avantprotocol.com)'s strategies, for Avant team members' AI agents (Grok Bot, Cursor, Claude, ChatGPT and other MCP clients).

## Who can use it

Avant team members. The server sits behind Cloudflare Access: you sign in with your `@avantprotocol.com` address (a one-time code by email) the first time your agent connects. Anyone else is refused before any data is read.

## What it answers

| Tool | Question |
|---|---|
| `get_overview` | Are we OK? A briefing across products: equity, ROE, open alerts, weakest health factors, markets near their kink, borrow cost, data freshness. |
| `find` | Which strategy, market, wallet or protocol is this name? |
| `what_changed` | What changed since a time: equity and ROE moves, new strategies, alerts, rate moves, large transactions. |
| `list_strategies`, `get_strategy` | Strategies and one strategy in detail: positions, legs, yield components and their sources, health factor vs baseline, history, open alerts. |
| `get_rates`, `get_risk` | Borrow costs and utilization vs kink; health factors and distance to liquidation. |
| `list_alerts` | Alerts raised, open or resolved, and whether they were delivered. |
| `get_nav_reconciliation` | Our NAV vs Avant's published NAV, and what explains the gap. |
| `search_transactions`, `get_transaction` | The tracked wallets' transactions by what they did, and one transaction in full. |
| `get_data_status` | Is the data fresh and complete right now? |
| `list_event_types`, `list_events` | An event log (alerts, wallet activity, rate moves, snapshot runs, pipeline health) for agents that react to changes. |

Every tool only reads. The data is rebuilt from chain reads and DeBank twice a day (positions, strategies, NAV), borrow rates every 10 minutes, health factors every 10 minutes and transactions hourly. It is monitoring data, not accounting.

## Privacy and data handling

- The plugin itself holds no data and no credentials: it points your agent at the server URL, and sign-in goes through Cloudflare Access.
- The server logs, per request: who (your email and which agent harness), which tool, how long it took and whether it worked. It never logs tool arguments or results.
- Everything the tools return is derived from public on-chain data and Avant's public documentation.

## Contact

Open an issue in this repository.
