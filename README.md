# dartpoint-mcp
MCP Server for public disclosure information of Korean companies, powered by the dartpoint.ai API. https://dartpoint.ai

## Features and Key Functions
*Provision of refined corporate information*
- Provides information based on electronic disclosures from the Financial Supervisory Service (FSS)
- Provides key corporate information including company overview, main products, competitor/subsidiary information, sales/profitability, and financial statements.
- Refer to the MCP server protocol's tool list for detailed information provided.

*Diverse utilization of corporate information*
- Enables corporate comparison and corporate report generation through LLM linkage.
- Allows monitoring of key events for interested companies, such as major disclosures, stock prices, and positive/negative evaluations.

*MCP Protocol Support*
- Supports MCP protocol for use with various LLM services like Claude and Cursor.
- Extensible through linkage with new AI models or analysis tools via a standardized protocol.

## Prompts
- 

## How to Run

It can be used with simple configuration in MCP clients (Claude, Cursor-ai, etc.).
Perform the setup using the DartPoint AI MCP Server address and your issued API Key.

- MCP URL Path: `https://dartpoint.ai/mcp-sse/mcp`
- DARTPOINT_API_KEY: APIKey can be issued after signing up for the dartpoint.ai service
- Using stdio mode: Configure using [SuperGateway](https://github.com/supercorp-ai/supergateway)

### Claude Desktop Standard (SSE)
```json
{
  "mcpServers": {
    "dartpoint-local": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:8000/mcp-sse/mcp",
        "--header",
        "DARTPOINT_API_KEY:<API Key from https://dartpoint.ai>"
      ]
    }
  }
}
```

### Claude Desktop Standard (stdio via supergateway)
```json
{
  "dartpoint": {
    "command": "npx",
    "args": [
      "-y",
      "supergateway",
      "--sse",
      "https://dartpoint.ai/mcp-sse/mcp",
      "--header",
      "DARTPOINT_API_KEY:<API Key from https://dartpoint.ai>"
    ]
  }
}
```

### Cursor-AI (SSE)
```json
{
  "mcpServers": {
    "dartpoint": {
      "url": "https://dartpoint.ai/mcp-sse/mcp",
      "headers": {
        "DARTPOINT_API_KEY": "<API Key from https://dartpoint.ai>"
      }
    }
  }
}
```

## Star History
[![Star History Chart](https://api.star-history.com/svg?repos=dartpointai/dartpoint-mcp&type=Date)](https://www.star-history.com/#dartpointai/dartpoint-mcp&Date)
