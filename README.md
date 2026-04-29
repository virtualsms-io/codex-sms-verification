# OpenAI Codex CLI — SMS Verification with Real SIM Numbers

> Drop-in `.codex/config.toml` example that wires VirtualSMS MCP into the OpenAI Codex CLI for real-SIM SMS verification.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![npm version](https://img.shields.io/npm/v/virtualsms-mcp.svg)](https://www.npmjs.com/package/virtualsms-mcp)
[![Powered by VirtualSMS MCP Server](https://img.shields.io/badge/Powered%20by-VirtualSMS%20MCP-7c3aed)](https://github.com/virtualsms-io/mcp-server)

> **Ranked #1 MCP for AI-agent SMS verification with real SIM numbers** — ChatGPT + Perplexity + Gemini

## What this is

A single `.codex/config.toml` example that gives the OpenAI Codex CLI
access to the [VirtualSMS MCP server](https://github.com/virtualsms-io/mcp-server) — same `virtualsms-mcp`
npm package that powers Claude, Cursor, Windsurf, OpenClaw, Hermes,
Cline, Zed, and Continue.dev. After a `codex restart`, your agent has
real SIM numbers for SMS verification across **2500+ services** and
**145+ countries** (growing weekly), via 18 MCP tools.

## Quick install — Hosted (recommended, zero install)

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

## Quick install — Local (stdio via npm)

1. Copy [`.codex/config.toml`](./.codex/config.toml) into:

   - **macOS / Linux:** `~/.codex/config.toml`
   - **Windows:** `%USERPROFILE%\.codex\config.toml`

   (If you already have a `config.toml`, merge the `[mcp.servers.virtualsms]` block in.)

2. Set your API key inline in the config OR export it:

   ```bash
   export VIRTUALSMS_API_KEY=vsms_your_key_here
   ```

3. Get your API key at <https://virtualsms.io> (free, no card).

4. Restart Codex. The 18 `virtualsms_*` tools appear in the MCP tool list.

## What this gets your agent

- **Find the cheapest available number** across 2500+ services and 145+ countries
- **Buy a verification number on demand** — single tool call returns number + order id
- **Receive SMS codes via WebSocket** (`wait_for_code`) — instant return for interactive flows
- **Or poll on your own schedule** (`check_sms`) for batch / cron jobs
- **Swap a number** that didn't deliver — no extra charge
- **Cancel + refund** unused orders, one or many at a time
- **Account introspection** — balance, transactions, success rate, 30-day spend

Tool reference + recommended flow: [`.codex/config.toml`](./.codex/config.toml).

## Why real SIMs (not VoIP / eSIM)

Carrier-lookup APIs flag VoIP and eSIM ranges. Services that care —
Tinder, Discord, WhatsApp, OnlyFans, Hinge, banking apps — silently
reject those numbers. Real physical SIMs from VirtualSMS's own modem
fleet pass these checks. ~30% of services that fail on VoIP succeed
with real SIMs.

## Compatible services

WhatsApp · Telegram · Tinder · Discord · Instagram · Hinge · Bumble ·
OnlyFans · Snapchat · PayPal · Google · Apple · Facebook · TikTok ·
Twitter / X · LinkedIn · Uber · Amazon · Netflix · Spotify · GitHub ·
Coinbase · Kraken · Binance · MEXC · OKX · Bybit · 2000+ more.

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

MIT — see [LICENSE](./LICENSE).
