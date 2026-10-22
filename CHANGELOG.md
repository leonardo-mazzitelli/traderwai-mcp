# Changelog

Notable changes to the hosted TraderWAI MCP server (`https://mcp.traderwai.com`) and to this repository. Versions match the entry `com.traderwai/traderwai` in the [official MCP Registry](https://registry.modelcontextprotocol.io). The server is updated continuously; the registry version changes when its public listing changes.

## [Unreleased]

### Repository

- Ready-to-copy client configurations in [examples/](examples/): Cursor, VS Code, OpenAI Codex, Gemini CLI and Claude Code, plus step lists for Claude, ChatGPT, Grok and Perplexity.
- README: Glama badge, hosted/closed-source note, supported AIs and a "Plans and limits" section.
- Documentation licensed under CC BY 4.0; trademark note kept.
- Added `SECURITY.md` and this changelog.

## [1.4.0] - 2026-10-18

- Perplexity (beta) supported as an MCP client through its custom remote connectors.
- Capital.com (beta) added as a broker platform.

## [1.3.0] - 2026-10-16

- `draw_chart`: the AI draws its analysis (levels, zones, trendlines, Fibonacci, structure labels and the trade plan) on a live chart.
- Exit rules on open positions: close the position or move the stop to break-even when a rule is met, checked every minute.

## [1.2.0] - 2026-10-11

- `backtest_strategy`: strategy backtests on 1-minute history with indicators (SMA, EMA, RSI, ATR), session and previous-day levels.
- `get_quote`: current bid/ask from the broker of each account.
- New platforms: MetaTrader 4/5, Binance, Bybit and DXtrade.
- Grok supported as an MCP client.
- Per-account risk limits and account groups (replicate orders across several accounts).

## [1.0.1] - 2026-04-14

- Registry remote URL changed to `https://mcp.traderwai.com`.

## [1.0.0] - 2026-04-14

- First listing of `com.traderwai/traderwai` in the official MCP Registry: live charts and trade execution for forex, gold, indices and crypto.
