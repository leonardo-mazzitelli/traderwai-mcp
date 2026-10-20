# Installing the TraderWAI MCP server

TraderWAI is a **hosted remote MCP server**. There is nothing to clone, build or run locally, and no API key to paste.

## Configuration

Add a remote server with Streamable HTTP transport:

```json
{
  "mcpServers": {
    "traderwai": {
      "url": "https://mcp.traderwai.com"
    }
  }
}
```

If the client asks for a transport type, use `streamableHttp` (HTTP). Do not use stdio.

## Authentication

The server uses OAuth 2.1 with dynamic client registration. The first time a tool is called, the client opens a browser window where the user signs in to TraderWAI (free account at https://traderwai.com) and approves access. No token needs to be copied manually.

## Verify

Ask: "List the TraderWAI symbols" or "Show me EUR/USD on H1". If the tools respond, the connection works. To trade, the user adds a broker account from the TraderWAI dashboard or by asking the AI to create one.

## Notes for the assistant

- Orders on a live account are real: confirm symbol, side, size, stop loss and take profit with the user before calling `execute_trade`.
- Use `get_quote` before placing or proposing an order; use `get_chart`, `draw_chart` or `get_ohlc` for analysis.
- Backtests (`backtest_strategy`) use historical data only and never place orders.
