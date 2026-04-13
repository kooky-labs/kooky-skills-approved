---
name: mcp-integration
description: Build MCP server tools, define schemas, connect external services
version: 1.0.0
author: kooky-labs
category: pre-installed
agent: jarvis
requires: []
---

# MCP Integration

Build reliable MCP (Model Context Protocol) integrations that give KOOKY agents access to external services. Use this skill when JARVIS needs to build MCP server tools, define tool schemas, or connect external services to the agent system.

## Usage

**Input:**
- `service` (string) — What external service or API needs connecting
- `tools_needed` (string) — What actions agents should be able to perform
- `target_agents` (string) — Which agents will use these tools
- `authentication` (string) — How the service authenticates (API key, OAuth, token)
- `rate_limits` (string, optional) — Known rate limits or usage constraints

**Output:**
- Tool catalog with names, descriptions, and input schemas
- Architecture showing MCP server to external service connection
- Authentication flow documentation
- Error handling map for common errors
- Implementation code (working server)
- Test plan
- Deployment notes

## Behavior

1. Receive service details and tool requirements
2. Design the MCP server structure:
   - `server.py` — Main server implementation
   - `tools/` — One file per tool or tool group
   - `schemas/` — Tool parameter schemas
   - `tests/` — Test files
3. Define each tool with: name (lowercase-hyphens), description (clear enough for agent to know when to use), inputSchema (strict JSON Schema), handler function
4. Implement error handling: catch all external API errors, return structured messages, retry with exponential backoff (1s, 2s, 4s, max 3 retries)
5. Apply security standards: environment variables for credentials, input validation, least-privilege access, audit logging
6. Write tests: unit tests per handler, integration tests with mocks, error case tests
7. Document deployment and configuration

## Network

External APIs as specified by the integration target. All external URLs must be documented and allow-listed.

## Error handling

- Catch all external API errors and return structured error messages
- Never expose raw API errors or stack traces to agents
- Return actionable messages: what went wrong + how to fix it
- Implement retry with exponential backoff for transient failures
- Timeout on external API calls: 30s default

## Notes

- Tool descriptions must be clear enough for agents to decide when to use them
- Schemas must be strict enough to prevent misuse but flexible enough for legitimate use
- Error messages must help agents self-correct (e.g., "Missing required parameter: platform. Expected one of: x, linkedin, tiktok")
- All tools should be idempotent where possible
- Never expose internal system details through tool responses
- Never allow tools to modify agent configurations
- Never build tools that could exfiltrate data (no arbitrary URL fetching without allowlist)
- Always log tool invocations (tool name, timestamp, success/failure — not input data)
- WATSON must audit all new MCP tools before deployment to production agents
