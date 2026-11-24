# mcp-web3-agent-starter

Lightweight AI Agent & MCP (Model Context Protocol) tool starter for Web3 & on-chain workflows 🤖⚡

## Overview
`mcp-web3-agent-starter` provides a robust, lightweight foundation for building autonomous AI agents and Model Context Protocol (MCP) servers tailored for Web3 environments and on-chain interactions.

## MCP Integration Details
This project implements standard Model Context Protocol (MCP) specs to expose blockchain read/write capabilities, wallet management, smart contract queries, and automated workflow triggers directly to LLM-powered agents.

- **Server Architecture**: Exposes endpoints via stdio/SSE for seamless MCP client connection.
- **Web3 Capabilities**: Supports Ethereum/EVM RPC operations, token transfers, contract interactions, and event monitoring.
- **Security & Safety**: Encapsulates private keys securely with strict policy checks prior to transaction execution.

## Tool Schema Example (Python / JSON)

### JSON Tool Definition
```json
{
  "name": "get_wallet_balance",
  "description": "Fetch native or ERC-20 token balance for a specified Web3 wallet address",
  "inputSchema": {
    "type": "object",
    "properties": {
      "address": {
        "type": "string",
        "description": "The target Ethereum address (0x...)"
      },
      "token_address": {
        "type": "string",
        "description": "Optional ERC-20 token contract address"
      }
    },
    "required": ["address"]
  }
}
```

### Python Implementation
```python
from mcp.server import Server

app = Server("web3-agent-starter")

@app.call_tool()
async def get_wallet_balance(name: str, arguments: dict) -> list:
    if name == "get_wallet_balance":
        address = arguments["address"]
        return [{"type": "text", "text": f"Balance for {address}: 1.5 ETH"}]
```
