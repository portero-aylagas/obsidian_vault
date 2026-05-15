# W3D5 MCP in LangChain Lab

**Source folder**
- `W3D5_MCP_in_LangChain`

**Main files**
- `mcp_langchain.py`
- `prompts.py`
- `documents/`
- `requirements.txt`
- `lab_summary.md`

**Lab type**
- Applied MCP + LangChain integration lab
- Main value: connect a LangChain agent to external tool servers through MCP

## What This Lab Teaches

This lab connects a LangChain v1 agent to MCP servers.

Default integrations:

- filesystem MCP server for files inside `documents/`
- Git MCP server for repository inspection
- optional Trello MCP server for real Trello card creation
- optional direct Trello REST API path for comparison

Pipeline:

```text
MCP server config
-> MultiServerMCPClient
-> loaded tools
-> LangChain agent
-> filesystem/Git/Trello tool calls
-> final answer or integration result
```

## Techniques Practiced

- `MultiServerMCPClient`
- filesystem MCP tools
- Git MCP tools
- optional third-party Trello MCP tools
- direct REST API comparison
- LangChain `create_agent`
- prompt builders
- environment configuration
- fail-fast checks for required services

## Important Architecture

```text
mcp_langchain.py
Main script that configures MCP servers, loads tools, builds the agent, and runs demos

prompts.py
Prompt templates and helper builders

documents/
Sandboxed filesystem content and Trello proof assets
```

## Important Code Patterns

### Load MCP tools

```python
client = MultiServerMCPClient(server_configs)
tools = await client.get_tools()
```

### Give tools to a LangChain agent

```python
agent = create_agent(
    model=model,
    tools=tools,
    system_prompt=system_prompt,
)
```

### Compare MCP with direct API access

```text
Trello REST API
-> explicit HTTP requests
-> direct control

Trello MCP server
-> exposed LangChain tools
-> standard agent interface
```

## What Was Provided

- A LangChain agent structure with MCP integration points.
- Filesystem/Git MCP examples and an optional Trello integration path.
- Lab guidance comparing direct API access with standardized MCP tools.

## Extra Concepts From Lab Source

- multi-server MCP integration
- MCP resources as context
- MCP vs direct API tradeoffs
- custom MCP tool wrappers
- resource-based agents
- MCP connection error handling
- MCP tool-call performance optimization

## What I Practiced

- Treating external systems as agent tools
- Understanding that MCP is a protocol layer, not the business logic itself
- Separating required integrations from optional live integrations
- Comparing standardized tool access with direct API calls
- Avoiding mock behavior for integrations that should be visibly real

## Improvement Ideas

- Add explicit MCP connection health checks.
- Record tool-call latency and failure modes.
- Keep direct API and MCP implementations side by side for clearer tradeoff testing.

## Links to Topic Notes

- [[../Frameworks/MCP]]
- [[../Frameworks/LangChain]]
- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Use a sandbox folder for filesystem MCP tools.
- Fail early when a required Git repository is missing.
- Keep live third-party writes optional.
- Use direct API calls when explicit control matters.
- Use MCP when many tools should be exposed through one consistent interface.

## Key Takeaway

MCP is most useful when an agent needs a standard way to access external systems. Direct APIs are still useful for small, explicit integrations where less indirection is better.
