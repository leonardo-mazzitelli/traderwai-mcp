# Security policy

TraderWAI is a hosted MCP server (`https://mcp.traderwai.com`). This repository holds documentation and client configurations only; the server's source code is not published. Security reports therefore concern the hosted service: the MCP endpoint, its OAuth authorization flow, the TraderWAI website and dashboard, and how broker accounts connected to TraderWAI are handled.

## Reporting a vulnerability

Email **info@traderwai.com** with the subject line `Security report`. Please include:

- what is affected (endpoint, tool name, page or OAuth step);
- steps to reproduce, and the impact you observed or expect;
- your contact details if you would like us to follow up or credit you.

Please do not open a public GitHub issue for security problems, and do not include real broker credentials, API keys or other people's data in your report.

We will acknowledge your report, keep you informed while we investigate, and let you know when it is fixed.

## Testing guidelines

- Use your own TraderWAI account and **demo** broker accounts only.
- Do not access, modify or delete data that is not yours, and stop as soon as you reach someone else's data.
- Do not run denial-of-service, load or spam tests, and do not place orders on live accounts you do not own.
- Give us reasonable time to fix an issue before disclosing it publicly.

## Supported versions

Only the current hosted version of the server is supported; there are no self-hosted releases. The version listed in the [official MCP Registry](https://registry.modelcontextprotocol.io) (`com.traderwai/traderwai`) is the one in production.
