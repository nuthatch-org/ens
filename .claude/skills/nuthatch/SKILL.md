---
name: nuthatch
description: Query this self-hosted nuthatch nest on mainnet - decoded events, balances, and read-only SQL. Use when asked about on-chain activity for these contracts.
---

# Querying the nuthatch nest

Contracts indexed on mainnet:
- `c0` = 0x00000000000c2e074ec69a0dfb2997ba6c7d2e1e

Data is local - never call an external API for it.

## Preferred: MCP
If a `nuthatch` MCP server is configured, use its tools. Call `schema` first to learn the
data model, then `sql` / `entity` / `balance` / `top_balances`.

## Fallback: HTTP (a `nuthatch dev` must be running)
- Recent rows:  `curl localhost:8288/entities?limit=20`
- Read-only SQL: `curl -G localhost:8288/sql --data-urlencode 'q=SELECT count(*) FROM transfers'`

`sql` sees finalized data only; balances/entity cover the live tip.
