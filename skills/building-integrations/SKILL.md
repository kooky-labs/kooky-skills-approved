---
name: building-integrations
description: Builds MCP server integrations that connect agents to external services -- defines tool schemas, implements handlers, and applies security standards. Use when agents need programmatic access to an external API or service.
---

# MCP Integration Development

Build reliable MCP (Model Context Protocol) servers that give agents access to external services. Covers tool design, schema definition, handler implementation, error handling, and security.

## When to Use

- Connecting agents to a new external API or service
- Defining MCP tool schemas and handlers
- Reviewing or improving an existing MCP integration

## Process

1. Identify the external service, required actions, consuming agents, and authentication method.
2. Design each tool with:
   - Name: lowercase-hyphens
   - Description: clear enough for an agent to know when to use it
   - inputSchema: strict JSON Schema
   - Handler function
3. Implement error handling: catch all external API errors, return structured messages, retry transient failures with exponential backoff (1s, 2s, 4s, max 3 retries). Default timeout: 30s.
4. Apply security standards: credentials in environment variables, input validation, least-privilege access, audit logging (tool name + timestamp + success/failure, not input data).
5. Write tests: unit tests per handler, integration tests with mocks, error case coverage.
6. Document deployment and configuration.

## Project Structure

```
server.py         # Main server
tools/            # One file per tool or tool group
schemas/          # Tool parameter schemas
tests/            # Test files
```

## Constraints

- All external URLs must be documented and allow-listed.
- Never expose raw API errors or stack traces to agents.
- Error messages must help agents self-correct (e.g., "Missing required parameter: platform. Expected one of: x, linkedin, tiktok").
- All tools should be idempotent where possible.
- Never allow tools to modify agent configurations.
- Never build arbitrary URL fetching without an allowlist.
- All new MCP tools require security review before production deployment.
