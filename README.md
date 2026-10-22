<p align="center"><img src="assets/logo.png" width="96" alt="TraderWAI"></p>

<h1 align="center">TraderWAI · MCP server</h1>

<p align="center"><b>Backtest, automate and trade from ChatGPT, Claude or Grok.</b><br>
A remote MCP server that connects the AI you already use to your own trading account.</p>

<p align="center">
<a href="https://traderwai.com">Website</a> ·
<a href="https://traderwai.com/en/docs">Docs</a> ·
<a href="https://traderwai.com/en/connect">Setup guides</a>
</p>

<p align="center">
<a href="https://glama.ai/mcp/connectors/com.traderwai/traderwai"><img src="https://glama.ai/mcp/connectors/com.traderwai/traderwai/badges/score.svg" alt="TraderWAI MCP connector on Glama"></a>
<a href="https://registry.modelcontextprotocol.io/v0.1/servers?search=com.traderwai/traderwai"><img src="https://img.shields.io/badge/MCP%20Registry-com.traderwai%2Ftraderwai-blue" alt="MCP Registry: com.traderwai/traderwai"></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/docs%20license-CC%20BY%204.0-lightgrey" alt="Docs license: CC BY 4.0"></a>
</p>

---

**Server URL:** `https://mcp.traderwai.com` (Streamable HTTP, OAuth 2.1 with dynamic client registration)
**Registry:** `com.traderwai/traderwai` in the [official MCP Registry](https://registry.modelcontextprotocol.io)

> **Hosted, closed-source server; this repository holds documentation and client configs.**
> The TraderWAI MCP server runs as a hosted service at `https://mcp.traderwai.com` and its source code is not published. This repository contains the connection instructions, ready-to-copy client configurations ([examples/](examples/)), the tool list and brand assets. There is nothing to install or run locally, and no API key: you sign in with OAuth.

## What your AI can do with it

- **Read live charts** for forex, gold, indices, oil and crypto, on any timeframe from M1 to D1.
- **Draw its analysis on the chart**: levels, zones, structure, Fibonacci and the trade idea, rendered on real candles.
- **Backtest a strategy in plain English** on 1-minute history and get every trade, the win rate, the total in R and the drawdown in seconds.
- **Place orders on your own broker account**, sized by the risk you choose, with stop loss and take profit. You approve, or you set the rules.
- **Leave rules running**: conditional orders and exit rules (break-even, close on a structure break) checked every minute on your broker's own price, even with the chat closed.

![The AI draws its analysis on a live chart](assets/ai-draws-on-your-chart.png)

## Supported platforms

MetaTrader 4 and 5, cTrader, TradeLocker, Match-Trader, DXtrade (beta), Capital.com (beta), Binance and Bybit. Demo and live accounts, including prop-firm accounts. MetaTrader requires the Trader or Max plan (see [Plans and limits](#plans-and-limits)).

## Supported AIs

Claude, ChatGPT, Grok, Gemini (Gemini CLI), Perplexity (beta), Cursor and any MCP client that supports remote Streamable HTTP servers with OAuth (VS Code with GitHub Copilot, Claude Code, OpenAI Codex and others).

## Connect it

You need a free TraderWAI account ([sign up](https://traderwai.com)); the first connection opens a login and consent screen (sign in with Google), and the account is created there if you don't have one.

| AI | How |
|---|---|
| **Claude** (web, desktop, mobile) | Settings → Connectors → Add custom connector → URL `https://mcp.traderwai.com` |
| **ChatGPT** (paid plans, developer mode) | Settings → Apps & Connectors → Advanced → Developer mode → Create → URL `https://mcp.traderwai.com`, authentication OAuth |
| **Grok** | grok.com/connectors → New connector → Custom → URL `https://mcp.traderwai.com` |
| **Perplexity** (beta; Pro, Max or Enterprise) | Settings → Connectors → Add custom remote connector → URL `https://mcp.traderwai.com` |
| **Claude Code** | `claude mcp add --transport http traderwai https://mcp.traderwai.com`, then `/mcp` to sign in |
| **Gemini CLI** | `gemini mcp add --transport http traderwai https://mcp.traderwai.com`, then `/mcp auth traderwai` · [settings.json](examples/gemini-cli/settings.json) |
| **OpenAI Codex** | `codex mcp add traderwai --url https://mcp.traderwai.com`, then `codex mcp login traderwai` · [config.toml](examples/codex/config.toml) |
| **Cursor** | [`.cursor/mcp.json`](examples/cursor/.cursor/mcp.json) |
| **VS Code** (GitHub Copilot) | [`.vscode/mcp.json`](examples/vscode/.vscode/mcp.json) |
| **Any other MCP client** | Add a remote Streamable HTTP server with the URL above, or use the JSON below |

```json
{
  "mcpServers": {
    "traderwai": {
      "url": "https://mcp.traderwai.com"
    }
  }
}
```

Every config file and step list is in [examples/](examples/). Step-by-step guides with screenshots for every AI and platform: [traderwai.com/en/connect](https://traderwai.com/en/connect).

## Try it

After connecting, ask your AI for example:

- *"Show me gold on H1 and draw the key levels and your trade idea on the chart."*
- *"Backtest gold for the last 30 days: buy when the price drops below yesterday's low and comes back up, stop just under the dip, target 2R."*
- *"Sell 0.10 gold at market, risk 0.5% of my balance, stop above the last swing high, target 2R."*
- *"On my NAS100 long: move the stop to break-even at +1R and close it if there is a bearish CHoCH on M15."*

![Backtest in seconds](assets/backtest-in-seconds.png)

## Tools

| Area | Tools |
|---|---|
| Market data and charts | `get_chart`, `draw_chart`, `get_ohlc`, `get_quote`, `list_symbols`, `list_timeframes` |
| Backtesting | `backtest_strategy` |
| Accounts | `get_account_info`, `get_broker_accounts`, `get_broker_account_state`, `create_broker_account`, `update_broker_account`, `delete_broker_account`, `test_broker_account`, `connect_ctrader`, `get_account_groups`, `set_account_group`, `delete_account_group` |
| Orders and positions | `execute_trade`, `execute_trade_multi`, `get_positions`, `modify_position`, `close_position`, `modify_broker_order`, `cancel_broker_order`, `get_trade_results` |
| Suggested orders | `suggest_order`, `get_suggested_orders`, `cancel_suggested_order` |
| Conditional orders and exit rules | `create_conditional_order`, `get_conditional_orders`, `get_conditional_order`, `update_conditional_order`, `run_conditional_order`, `cancel_conditional_order`, `delete_conditional_order` |
| Automation and risk | `get_auto_execution_config`, `set_auto_execution_config`, `delete_auto_execution_config`, `set_global_auto_execution`, `get_risk_limits` |
| Plan | `get_upgrade_url` |

Every tool carries MCP annotations (`readOnlyHint` / `destructiveHint`), so your AI client can ask for confirmation before anything that changes your account.

![Orders sized by risk](assets/orders-sized-by-risk.png)

## Security

- OAuth 2.1 with PKCE and dynamic client registration; you can revoke access from your TraderWAI dashboard at any time.
- Broker credentials are encrypted at rest and never shared with the AI.
- Risk limits per account on paid plans (max lot, open positions, trades per day and daily loss; on Max also drawdown, risk per trade, hours and symbols) are enforced by TraderWAI, not by the AI.
- To report a vulnerability, see [SECURITY.md](SECURITY.md).
- [Privacy policy](https://traderwai.com/en/privacy) · [Terms](https://traderwai.com/en/terms)

## Plans and limits

Charts and live market data are unlimited on every plan. What is limited is acting on the account. Prices in USD; taxes may apply.

| | Free | Plus | Trader | Max |
|---|---|---|---|---|
| Price | $0 | $9.90/month or $69/year (7-day free trial) | $29/month or $199/year | $79/month or $549/year |
| Broker accounts | 2 | 3 | 5 | 10 |
| MetaTrader 4/5 accounts | **Not included** | **Not included** | 1 | 3 |
| Order executions per day | 5 | 25 | Unlimited | Unlimited |
| Auto-execution of suggested orders | No (you approve each one) | Yes | Yes | Yes |
| Active conditional orders | 2 | 5 | 10 | 30 |
| Charts marked by the AI (`draw_chart`) per day | 5 | Unlimited | Unlimited | Unlimited |
| Backtests per day | 5 | 20 | 50 | Unlimited |
| Backtest history | 7 days | 45 days | 90 days | Full |
| Risk limits | No | Basic | Basic | Full (prop-firm rules) |

- The Free plan covers cTrader, TradeLocker, Match-Trader, DXtrade (beta), Capital.com (beta), Binance and Bybit; **MetaTrader needs Trader or Max**.
- An execution is each order placed on your broker (by your AI, by an order you approved or by a conditional order). Charts, market data and checking positions don't count.
- When a limit is reached, tools return a `PLAN_LIMIT` error; `get_account_info` shows your plan, usage and limits.

Current prices and details: [traderwai.com/en/pricing](https://traderwai.com/en/pricing).

## Support

[traderwai.com/en/contact](https://traderwai.com/en/contact) · info@traderwai.com · [Service status](https://traderwai.com/en/status) · [Changelog](CHANGELOG.md)

## License

The documentation and example configurations in this repository are licensed under [CC BY 4.0](LICENSE). The TraderWAI name and logo are not covered by that license; see [NOTICE](NOTICE). The hosted server is proprietary.

---

<sub>Trading leveraged products such as CFDs, forex and futures carries a high risk of losing money. TraderWAI is a technology tool: it does not provide investment advice or manage funds, and analyses or proposals from the AI are not recommendations. Past results, including backtests, do not guarantee future results. TraderWAI is operated by FLEXIN AGILE LTD (England and Wales, 16134800).</sub>
