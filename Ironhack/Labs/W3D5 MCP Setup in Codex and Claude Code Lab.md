# W3D5 MCP Setup in Codex and Claude Code Lab

**Source folder**
- `W3D5_MCP_in_codex_and_claude_code`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- setup / validation lab
- Main value: understand MCP as a shared tool interface across coding assistants, not only inside LangChain code

## What This Lab Teaches

This lab moves MCP from application code into the coding environment.

```text
VS Code assistant
-> MCP server configuration
-> LangChain docs MCP endpoint
-> assistant can answer with external documentation context
```

The important concept is that MCP standardizes how assistants discover and use external tools or resources.

## Techniques Practiced

- MCP server configuration
- MCP endpoint validation
- editor-level assistant setup
- same-server testing across clients
- documentation-backed assistant queries
- tool availability verification

## Important Architecture

```text
Codex / Claude Code
-> local editor settings
-> remote MCP server
-> docs tools/resources
-> assistant response
```

The lab compares two clients against the same server, which separates MCP capability from one specific assistant.

## Important Code Patterns

This lab is mostly configuration, not application code. The reusable pattern is the server entry:

```text
https://docs.langchain.com/mcp
```

## What Was Provided

The lab source provides setup steps, official documentation links, and validation prompts. The workspace currently contains the HTML source but no settings export or screenshots.

## What I Practiced

- treating assistant integrations as configurable infrastructure
- validating tool access after setup
- comparing MCP behavior across assistant clients
- asking documentation questions through MCP instead of relying on memory

## Links to Topic Notes

- [[../Frameworks/MCP]]
- [[../Frameworks/LangChain]]
- [[../Agentic/Effective Context Engineering for AI Agents]]
- [[../Agentic/Agent Skills]]

## What To Reuse Later

- Validate every MCP server with a simple known-answer query.
- Test the same MCP server in multiple clients when portability matters.
- Prefer official documentation MCP servers for fast-moving libraries.
- Keep MCP setup reproducible in settings or documented config.

## Improvement Ideas

- Add a second MCP server and compare tool discovery.
- Document the exact Codex and Claude Code settings used.
- Test failure behavior when the MCP endpoint is unavailable.

## Key Takeaway

MCP is useful beyond app agents: it can turn coding assistants into documentation-aware tools when the server is configured and validated properly.
