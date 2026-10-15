# ScholarMuse MCP

![ScholarMuse](assets/logo.png)

Academic research tools for the AI agent you already use.

ScholarMuse connects AI agents to academic papers, reference verification, research datasets, grants, biological and chemical information, and scientific figure tools through one remote MCP endpoint. It provides access to 50+ research sources; upstream availability varies.

- **Website:** https://scholarmuse.ai
- **Remote MCP:** https://scholarmuse.ai/mcp
- **Transport:** Streamable HTTP
- **Authentication:** OAuth browser sign-in, with automatic discovery and dynamic client registration. No shared tokens or upstream API keys are included in this repository.
- **Docs:** https://scholarmuse.ai/docs
- **Setup guides:** https://scholarmuse.ai/connect
- **Privacy:** https://scholarmuse.ai/privacy
- **Terms:** https://scholarmuse.ai/terms
- **Support:** davie@daviechen.com

This repository contains public connection manifests, documentation and branding for the hosted service. The hosted service implementation is not included.

## Gemini CLI

```sh
gemini extensions install https://github.com/TopLocalAI/scholarmuse-mcp
```

Complete the browser sign-in when prompted. If needed, use `/mcp auth scholarmuse` to start authentication. The extension does not bypass tool confirmation.

## Cursor, Claude and other MCP clients

Add `https://scholarmuse.ai/mcp` as a remote Streamable HTTP MCP server and complete OAuth sign-in. See the [client-specific setup guides](https://scholarmuse.ai/connect) for exact steps. The root `plugin.json` and `mcp.json` implement Agent Plugins 1.0.0; `.cursor-plugin/plugin.json` and `.mcp.json` provide Cursor-compatible metadata.

## Example requests

- Find recent papers about CRISPR delivery and return their DOIs and source links.
- Check whether these references are real and flag retraction information when available.
- Find NIH or NSF grants related to solid-state batteries.
- Retrieve a protein structure or research dataset and cite its original source.

Start with `list_capabilities` to inspect available tools and `get_balance` to check credits. Both are free. Most research data tools are read-only; figure creation and editing create generated assets and consume credits. Ask for explicit user approval before paid figure work.

## Pricing and limits

ScholarMuse is a hosted freemium service. Data calls generally cost 1–2 credits; batch verification costs depend on item count. New accounts receive 300 trial credits valid for 30 days, and free accounts receive 30 credits per month. Figure generation costs 100 credits and requires a paid plan or credit pack. Check [current pricing](https://scholarmuse.ai/pricing) and the per-tool costs before use.

If credits are insufficient, the server returns structured details and a top-up link. Do not retry paid calls automatically. Upstream failures and partial results must be surfaced accurately with source attribution.

## REST API

Developers may also use the [REST API documentation](https://scholarmuse.ai/docs) and [OpenAPI schema](https://scholarmuse.ai/api/v1/openapi.json).
