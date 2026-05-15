# MCP

**Labs**
- `week-3/mcp_introduction.ipynb`
- `W3D5_MCP_in_LangChain`
- `W3D5_MCP_in_codex_and_claude_code`

## Main Techniques
- Connect to MCP servers
- Load MCP tools
- Load MCP resources
- Use MCP tools inside agents
- Middleware and interceptors
- Filesystem MCP tools
- Git MCP tools
- Optional app integrations through MCP

## Example
### MCP client setup
```python
client = MultiServerMCPClient(
    {
        "langchain_docs": {
            "transport": "streamable_http",
            "url": "https://example.com/mcp"
        }
    }
)
```

The real notebook connects to a documentation MCP server, then exposes its tools to a LangChain agent.

### Load tools
```python
tools = await mcp_client.get_tools()
agent = create_agent(model=llm, tools=tools)
```

Inspect loaded tools:

```python
for tool in tools:
    print(tool.name, tool.description)
```

### Load resources
```python
resources = await mcp_client.get_resources()
```

### Agent using MCP tools
```python
result = await agent.ainvoke({
    "messages": [HumanMessage(content="How do I create a LangChain agent with tools?")]
})

print(result["messages"][-1].content)
```

### Interceptor idea
- Log tool calls
- Inspect arguments
- Add custom behavior around tool execution

### Logging interceptor shape
```python
async def logging_interceptor(request, handler):
    print(f"Calling tool: {request.name}")
    result = await handler(request)
    print(f"Tool finished: {request.name}")
    return result
```

### Applied server pattern
The W3D5 lab connects one LangChain agent to multiple MCP-backed capabilities:

```text
filesystem MCP server
-> reads and lists files in documents/

Git MCP server
-> inspects repository status

optional Trello MCP server
-> creates real demo cards when credentials are configured
```

### MCP vs direct API
MCP is useful when a tool should be exposed through a standard agent interface.

Direct API calls are still useful when a small integration needs explicit control over HTTP requests, request payloads, and response handling.

## What the Notebook Teaches

- MCP servers expose tools and resources
- LangChain can load those tools through adapters
- Agents can use MCP tools as if they were regular LangChain tools
- Interceptors let you observe or customize tool behavior
- Filesystem and Git integrations show MCP as a practical local-tool interface
- The Trello comparison shows the tradeoff between MCP indirection and direct REST calls

## Key Idea
- MCP standardizes how AI systems access tools and external data sources.

## Progression
- Extends [[LangChain]]
- Applied in [[../Labs/W3D5 MCP in LangChain Lab]]
