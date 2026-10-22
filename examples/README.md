# Client configuration examples

Ready-to-copy configurations for the hosted TraderWAI MCP server.

- **URL:** `https://mcp.traderwai.com`
- **Transport:** Streamable HTTP (SSE-only clients are not supported)
- **Authentication:** OAuth 2.1 with dynamic client registration. There is no API key: the first connection opens a browser window to sign in to TraderWAI (with Google) and approve access. If you don't have a TraderWAI account yet, it is created at that step.

| Client | File in this folder | Where it goes |
|---|---|---|
| Cursor | [`cursor/.cursor/mcp.json`](cursor/.cursor/mcp.json) | `.cursor/mcp.json` in your project, or `~/.cursor/mcp.json` for all projects |
| VS Code (GitHub Copilot) | [`vscode/.vscode/mcp.json`](vscode/.vscode/mcp.json) | `.vscode/mcp.json` in your workspace |
| OpenAI Codex | [`codex/config.toml`](codex/config.toml) | `~/.codex/config.toml` (or `.codex/config.toml` in a trusted project) |
| Gemini CLI | [`gemini-cli/settings.json`](gemini-cli/settings.json) | `~/.gemini/settings.json`, or `.gemini/settings.json` in your project |
| Claude Code | [`claude-code/.mcp.json`](claude-code/.mcp.json) | `.mcp.json` at your project root (or use the command below) |

If a file already exists, merge the `traderwai` entry into it instead of replacing the file.

## Cursor

```json
{
  "mcpServers": {
    "traderwai": {
      "url": "https://mcp.traderwai.com"
    }
  }
}
```

1. Paste the configuration into `.cursor/mcp.json` (project) or `~/.cursor/mcp.json` (global), or go to Settings → Tools & MCP → Add new MCP server.
2. Click **Login** / **Connect** next to `traderwai` and sign in.
3. Use the chat in Agent mode.

## VS Code (GitHub Copilot)

```json
{
  "servers": {
    "traderwai": {
      "type": "http",
      "url": "https://mcp.traderwai.com"
    }
  }
}
```

1. Paste the configuration into `.vscode/mcp.json`, or run **MCP: Add Server** from the command palette, choose **HTTP** and enter the URL.
2. Sign in when VS Code asks.
3. Open Copilot Chat in Agent mode and enable the TraderWAI tools.

## OpenAI Codex

```toml
[mcp_servers.traderwai]
url = "https://mcp.traderwai.com"
```

Or from the terminal:

```bash
codex mcp add traderwai --url https://mcp.traderwai.com
codex mcp login traderwai
```

`codex mcp login traderwai` opens the browser to sign in.

## Gemini CLI

```json
{
  "mcpServers": {
    "traderwai": {
      "httpUrl": "https://mcp.traderwai.com"
    }
  }
}
```

Gemini CLI uses `httpUrl` for Streamable HTTP (`url` is for SSE). Or from the terminal:

```bash
gemini mcp add --transport http traderwai https://mcp.traderwai.com
```

Then, inside Gemini CLI, run `/mcp auth traderwai` to sign in, and `/mcp` to check that TraderWAI is connected.

## Claude Code

```bash
claude mcp add --transport http traderwai https://mcp.traderwai.com
```

Then run `/mcp` inside Claude Code, choose `traderwai` and authenticate in the browser. To share the server with a project instead, use [`claude-code/.mcp.json`](claude-code/.mcp.json).

## Claude (claude.ai, desktop and mobile)

Works on the free Claude plan.

1. Go to **Settings → Connectors**.
2. Click **Add custom connector**.
3. Name: `TraderWAI`. URL: `https://mcp.traderwai.com`.
4. Click **Add**, then **Connect**, sign in and authorize access.
5. In a chat, enable TraderWAI from the tools button.

## ChatGPT

Requires a paid ChatGPT plan (Plus, Pro, Business or Enterprise) with developer mode.

1. On chatgpt.com go to **Settings → Apps & Connectors → Advanced settings** and turn on **Developer mode**.
2. Back in **Apps & Connectors**, click **Create**.
3. Name: `TraderWAI`. URL: `https://mcp.traderwai.com`. Authentication: **OAuth**.
4. Click **Create**, sign in and authorize access.
5. In a new chat, enable TraderWAI from the **+** menu → Developer mode.

## Grok

Uses Grok's custom connectors (if you don't see the option, your plan or region may not have it yet).

1. Open [grok.com/connectors](https://grok.com/connectors) (or Settings → Connectors in the app).
2. Click **New Connector** and choose **Custom**.
3. Name: `TraderWAI`. Server URL: `https://mcp.traderwai.com`.
4. Save, sign in and authorize access.
5. In a new chat, ask Grok to use TraderWAI, e.g. *"Show me the EUR/USD H1 chart"*.

## Perplexity (beta)

Requires Perplexity Pro, Max or Enterprise, on the web or desktop app.

1. Go to **Settings → Connectors** ([perplexity.ai/account/connectors](https://www.perplexity.ai/account/connectors)).
2. Click **+ Custom connector** and choose **Remote**.
3. Name: `TraderWAI`. MCP server URL: `https://mcp.traderwai.com`. Authentication: **OAuth**.
4. Add it, sign in and authorize access.

## Check the connection

Ask your AI *"List the TraderWAI symbols"* or *"Show me EUR/USD on H1"*. If the tools respond, you are connected. To trade, add a broker account from the TraderWAI dashboard or ask the AI to create one.

Guides with screenshots for every AI and platform: [traderwai.com/en/connect](https://traderwai.com/en/connect).
