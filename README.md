# QIE Wallet MCP

QIE Wallet is a read-only, non-custodial [Model Context Protocol](https://modelcontextprotocol.io/) connector for public QIE blockchain data. It does not take private keys, seed phrases or passwords, and it does not sign or send transactions. Signing stays in the QIE Wallet app on the user's device. No sign-in or API key is required.

- **Remote endpoint:** https://mcp.qie.digital/mcp (Streamable HTTP)
- **Official MCP Registry name:** `digital.qie/wallet` (v0.1.0)
- **Docs, privacy, terms and support:** https://mcp.qie.digital/
- **Provider:** QIE Wallet (Pty) Ltd · info@qie.digital

This repository is a public listing pack (docs, install config and plugin manifests). The connector itself is the hosted server at the URL above.

## What it does

The server exposes six read-only tools for QIE mainnet (chain 1990) and QIE testnet (chain 1983):

| Tool | What it does |
| --- | --- |
| `qie_get_balances` | Native QIE and token balances for a hex address, or a `.qie` name (QIE ID) on mainnet |
| `qie_get_network_info` | Chain ID, RPC URLs, explorer and native currency |
| `qie_get_tx_status` | Pending, success, failed or not found, with block, confirmations and explorer link |
| `qie_list_tokens` | Tokens on the selected network, with optional search |
| `qie_resolve_name` | QIE ID (`yourname.qie`) to address on mainnet |
| `qie_reverse_lookup` | Address to QIE ID on mainnet |

QIE ID lookups work on mainnet only. The server returns chain data only. It does not give price, APY or investment advice.

## Install

Add the remote URL in any MCP client that supports Streamable HTTP. Authentication: none.

### Cursor

Settings → MCP → New MCP Server, or save this as `.cursor/mcp.json` (or merge it into your existing MCP config):

```json
{
  "mcpServers": {
    "qie-wallet": {
      "url": "https://mcp.qie.digital/mcp"
    }
  }
}
```

This repository also includes a root `.mcp.json` and `.cursor-plugin/plugin.json` for cursor.directory and the Cursor Marketplace.

### Claude

Claude Code:

```bash
claude mcp add --transport http qie-wallet https://mcp.qie.digital/mcp
```

Claude (custom connector): add https://mcp.qie.digital/mcp as a custom connector. No sign-in.

### VS Code

Save this as `.vscode/mcp.json` in a workspace, or add it under MCP settings:

```json
{
  "servers": {
    "qie-wallet": {
      "type": "http",
      "url": "https://mcp.qie.digital/mcp"
    }
  }
}
```

## Listings

- GitHub listing pack: https://github.com/qieadmin/qie-wallet-mcp-listing
- Official MCP Registry: [`digital.qie/wallet`](https://registry.modelcontextprotocol.io/v0.1/servers?search=digital.qie/wallet)
- Glama: https://glama.ai/mcp/connectors/digital.qie/wallet
- Website: https://mcp.qie.digital/

## License

MIT. Copyright (c) 2026 VortX Capital.
