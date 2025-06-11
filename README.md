# dartpoint-mcp
MCP Server for public disclosure information of Korean companies, powered by the dartpoint.ai API. https://dartpoint.ai  
README in Korean: [README-KR.md](https://github.com/dartpointai/dartpoint-mcp/blob/master/README-KR.md)

## Features and Key Functions
*Refined Corporate Data*
- Provides structured corporate data sourced from DART by the FSS(Financial Supervisory Service) of Korea.
- Includes key information such as company overview, main products&services, competitor&subsidiary data, revenue and profit margins, and financial statstrongents, etc.

*Versatile Use of Corporate Data*
- Enables advanced tasks like comparative company analysis and automated report generation through LLM integration.
- Supports monitoring of key events such as major disclosures, stock price movstrongent, and sentiment analysis.

*MCP Protocol Support*
- Supports the MCP protocol for integration with various LLM services like Claude, Cursor, and more.
- Expandable through integration with new AI models or analytical tools via standarized protocols.

## Prompts
*Here are 4 prompts you could ask the DartPoint AI MCP server, leveraging its corporate information capabilities:*
- "Analyze the recent financial performance of Samsung Electronics for the past year."
(This would likely use get_financial_summary_by_date or get_financial_info_by_date and potentially get_dividends.)
- "Who are the main competitors of LG Electronics and what are their primary products?"
(This would use get_competitors and possibly get_corp_products_info for the competitor's products if the tool supports it.)
- "Provide a summary of the current market sentiment from news articles regarding Hyundai Motor Company."
(This would directly use get_news_sentiments.)
- "What are the key products and services offered by SK Hynix, and what is a brief overview of their business?"
(This would use get_corp_products_info and get_corp_bsns_summary.)

## How to get APIKEY from DartPoint AI

The API key can be issued on your account page after registering at https://dartpoint.ai.

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
    "dartpoint": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://dartpoint.ai/mcp-sse/mcp",
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