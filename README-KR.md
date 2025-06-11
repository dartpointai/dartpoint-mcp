# dartpoint-mcp
dartpoint.ai API 기반의 한국 기업 공시 정보 제공 MCP 서버입니다. https://dartpoint.ai  
영문 설명: [README.md](https://github.com/dartpointai/dartpoint-mcp)

## 특징 및 주요 기능
*정제된 기업 정보 제공*
- 금융감독원(FSS) 전자공시 기반 정보 제공
- 기업 개요, 주요 제품, 경쟁사/계열사 정보, 매출/수익성, 재무제표 등 핵심 기업 정보 제공
  
*기업 정보의 다양한 활용*
- LLM 연동을 통해 기업 비교 및 기업 리포트 생성 가능
- 관심 기업의 주요 공시, 주가, 긍정/부정 평가 등 핵심 이벤트 모니터링 가능

*MCP 프로토콜 지원*
- Claude, Cursor 등 다양한 LLM 서비스에서 사용할 수 있도록 MCP 프로토콜 지원
- 표준화된 프로토콜을 통해 새로운 AI 모델이나 분석 도구와 연동하여 확장 가능

## 프롬프트 예시
*DartPoint AI MCP 서버의 기업 정보 기능을 활용하여 질문할 수 있는 4가지 프롬프트 예시입니다:*
- "삼성전자의 최근 1년간 재무 성과를 분석해 줘."
(get_financial_summary_by_date 또는 get_financial_info_by_date, 그리고 잠재적으로 get_dividends를 사용할 것입니다.)
- "LG전자의 주요 경쟁사는 누구이고, 그들의 주요 제품은 무엇이야?"
(get_competitors를 사용하고, 도구가 지원한다면 경쟁사의 제품 정보를 위해 get_corp_products_info를 사용할 수 있습니다.)
- "현대자동차에 대한 뉴스 기사를 바탕으로 현재 시장 분위기를 요약해 줘."
(get_news_sentiments를 직접 사용할 것입니다.)
- "SK하이닉스가 제공하는 주요 제품과 서비스는 무엇이고, 그들의 사업에 대해 간략하게 설명해 줘."
(get_corp_products_info와 get_corp_bsns_summary를 사용할 것입니다.)

## DartPoint AI에서 APIKEY 발급받는 방법

API 키는 https://dartpoint.ai 가입 후, 계정 페이지(마이페이지)에서 발급받을 수 있습니다.

## 실행 방법

MCP 클라이언트(Claude, Cursor-ai 등)에서 간단한 설정으로 사용할 수 있습니다.
DartPoint AI MCP 서버 주소와 발급받은 API 키를 사용하여 설정하세요.

- MCP URL 경로: `https://dartpoint.ai/mcp-sse/mcp`
- DARTPOINT_API_KEY: API 키는 dartpoint.ai 서비스 가입 후 발급받을 수 있습니다.
- stdio 모드 사용: [SuperGateway](https://github.com/supercorp-ai/supergateway)를 사용하여 설정하세요.

### Claude 데스크톱 (SSE)
```json
{
  "mcpServers": {
    "dartpoint": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://dartpoint.ai/mcp-sse/mcp",
        "--header",
        "DARTPOINT_API_KEY:<[https://dartpoint.ai](https://dartpoint.ai) 에서 발급받은 API 키>"
      ]
    }
  }
}
```

### Claude 데스크톱 (stdio via supergateway)
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
