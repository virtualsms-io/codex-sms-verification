# OpenAI Codex CLI: Account Verification with VirtualSMS

> Drop-in `.codex/config.toml` example that wires VirtualSMS MCP into the OpenAI Codex CLI for account verification, number rentals and proxies.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![npm version](https://img.shields.io/npm/v/virtualsms-mcp.svg)](https://www.npmjs.com/package/virtualsms-mcp)
[![Powered by VirtualSMS MCP Server](https://img.shields.io/badge/Powered%20by-VirtualSMS%20MCP-7c3aed)](https://github.com/virtualsms-io/mcp-server)

## What this is

VirtualSMS is an account verification platform for developers and AI agents. It combines one-time SMS verification, dedicated number rentals, matching-country proxies and private cloud browser sessions behind one API, one MCP server and one prepaid balance.

This repo is a single `.codex/config.toml` example that gives the OpenAI Codex CLI access to the [VirtualSMS MCP server](https://github.com/virtualsms-io/mcp-server), the same `virtualsms-mcp` npm package that powers Claude, Cursor, Windsurf, OpenClaw, Hermes, Cline, Zed, and Continue.dev. After a `codex restart`, your agent has 40 MCP tools across SMS verification, number rentals, proxies and browser sessions, covering **2500+ services** and **145+ countries** (growing weekly).

## Quick install: Hosted (recommended, zero install)

Paste this into your AI assistant's MCP config:

```json
{
  "mcpServers": {
    "virtualsms": {
      "type": "streamableHttp",
      "url": "https://mcp.virtualsms.io/mcp",
      "headers": { "x-api-key": "vsms_your_api_key_here" }
    }
  }
}
```

No `npm install`, no Node.js required on the client. The MCP server runs at [mcp.virtualsms.io](https://mcp.virtualsms.io).

Get your API key at <https://virtualsms.io>.

## Quick install: Local (stdio via npm)

1. Copy [`.codex/config.toml`](./.codex/config.toml) into:

   - **macOS / Linux:** `~/.codex/config.toml`
   - **Windows:** `%USERPROFILE%\.codex\config.toml`

   (If you already have a `config.toml`, merge the `[mcp.servers.virtualsms]` block in.)

2. Set your API key inline in the config OR export it:

   ```bash
   export VIRTUALSMS_API_KEY=vsms_your_key_here
   ```

3. Get your API key at <https://virtualsms.io> (free, no card).

4. Restart Codex. The 40 `virtualsms_*` tools appear in the MCP tool list.

## What this gets your agent

- **Receive one-time SMS codes** from $0.05: `create_order` returns number + order id, `wait_for_sms` returns instantly over WebSocket for interactive flows, or `get_sms` polls on your own schedule for batch / cron jobs
- **Rent dedicated numbers** from 1 to 30 days
- **Buy matching-country residential, mobile and datacenter proxies**
- **Launch private cloud browser sessions** that work alongside your number and proxy (beta)
- **Find the cheapest available number** across 2500+ services and 145+ countries
- **Swap a number** that did not deliver: no extra charge
- **Cancel + refund** unused orders, one or many at a time
- **Account introspection**: balance, transactions, success rate, 30-day spend

Tool reference + recommended flow: [`.codex/config.toml`](./.codex/config.toml).

## Numbers

VirtualSMS numbers are carrier-issued mobile numbers, backed by real physical SIM cards on operators like Vodafone, O2 and T-Mobile, not VoIP. Carrier-lookup APIs flag VoIP and eSIM ranges, and services that care, such as Tinder, Discord, WhatsApp, OnlyFans, Hinge and banking apps, can silently reject those numbers. Carrier-issued mobile numbers pass these checks more reliably.

## Compatible services

WhatsApp · Telegram · Tinder · Discord · Instagram · Hinge · Bumble ·
OnlyFans · Snapchat · PayPal · Google · Apple · Facebook · TikTok ·
Twitter / X · LinkedIn · Uber · Amazon · Netflix · Spotify · GitHub ·
Coinbase · Kraken · Binance · MEXC · OKX · Bybit · 2500+ more.

## Cross-references

- **Parent MCP server:** <https://github.com/virtualsms-io/mcp-server>
- **npm package:** [`virtualsms-mcp`](https://www.npmjs.com/package/virtualsms-mcp)
- **Project home:** <https://virtualsms.io>
- **MCP page (per-client setup):** <https://virtualsms.io/mcp>
- **Sister skill repos:**
  [claude-skill-sms-verification](https://github.com/virtualsms-io/claude-skill-sms-verification) ·
  [openclaw-skill-sms](https://github.com/virtualsms-io/openclaw-skill-sms) ·
  [cursor-rules-sms-verification](https://github.com/virtualsms-io/cursor-rules-sms-verification) ·
  [windsurf-workflow-sms](https://github.com/virtualsms-io/windsurf-workflow-sms)

## License

MIT: see [LICENSE](./LICENSE).
