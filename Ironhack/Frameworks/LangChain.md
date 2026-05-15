# LangChain

**Labs**
- `week-3/langchain_integration.ipynb`
- `W3D3_NormalObjects_Creative_Complaint_Handler_LangChain`
- `W3D5_MCP_in_LangChain`
- `W4D1_langchain_guardrails`

## Main Techniques
- Unified model abstraction
- `invoke`
- `stream`
- `batch`
- Message objects
- Tools
- Tool binding
- Manual tool execution
- Multiple tool calls
- Agents
- Agent streaming
- MCP-loaded tools

## Examples

### Setup pattern
Load environment variables first, then initialize the model.

```python
import os
from dotenv import load_dotenv
from langchain.chat_models import init_chat_model

load_dotenv()

if not os.getenv("OPENAI_API_KEY"):
    raise ValueError("OPENAI_API_KEY not found")
```

### Model abstraction
The lab shows two ways to create models. The unified interface is useful when switching providers.

```python
model = init_chat_model(
    model="gpt-4o-mini",
    model_provider="openai",
    temperature=0.7
)
```

Direct model classes are more explicit.

```python
from langchain_openai import ChatOpenAI

chat_model = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0.7
)
```

### Invoke
Use `invoke` when you want one complete response.

```python
response = model.invoke("Explain what LangChain is in one sentence.")
print(response.content)
```

### Stream
Use `stream` when you want partial output as it is generated.

```python
for chunk in model.stream("Tell me a short story about AI in 3 sentences."):
    print(chunk.content, end="")
```

This is useful for chat apps because the user sees output immediately instead of waiting for the full answer.

### Batch
Use `batch` to send several independent requests.

```python
questions = [
    "What is machine learning?",
    "What is deep learning?",
    "What is natural language processing?"
]

responses = model.batch(questions)
```

Control concurrency when you want to avoid sending too many requests at once.

```python
responses = model.batch(
    questions,
    config={"max_concurrency": 2}
)
```

### Messages
Messages are the unit of conversation context.

```python
from langchain_core.messages import SystemMessage, HumanMessage, AIMessage

messages = [
    SystemMessage(content="You are a helpful assistant."),
    HumanMessage(content="What is LangChain?")
]
```

### Multi-turn conversation
The conversation is just a list that grows over time.

```python
conversation = [
    SystemMessage(content="You are a helpful AI tutor."),
    HumanMessage(content="What is a variable in programming?")
]

response1 = model.invoke(conversation)
conversation.append(AIMessage(content=response1.content))

conversation.append(HumanMessage(content="Can you give an example?"))
response2 = model.invoke(conversation)
```

### Tool
Tools are normal Python functions with schemas that the model can decide to call.

```python
from langchain_core.tools import tool

@tool
def get_current_time(timezone: str = "UTC") -> str:
    return "..."
```

### Tool with arguments
The docstring matters because the model uses it to decide when the tool is relevant.

```python
@tool
def calculate_sum(a: int, b: int) -> int:
    """Add two integers and return the total."""
    return a + b
```

### Tool with a Pydantic schema
Use Pydantic when the tool has more structured inputs.

```python
from pydantic import BaseModel, Field

class SearchInput(BaseModel):
    query: str = Field(description="The search query")
    max_results: int = Field(default=5, description="Maximum number of results")
```

### Tool binding
Binding tools gives the model permission to request tool calls.

```python
tools = [get_current_time, calculate_sum]
model_with_tools = model.bind_tools(tools)
```

### Manual tool execution
The model can request a tool call, but your code still needs to execute it unless an agent is handling the loop.

```python
response = model_with_tools.invoke("What's 25 + 37?")

if response.tool_calls:
    for tool_call in response.tool_calls:
        print(tool_call["name"])
        print(tool_call["args"])
```

Manual execution pattern:

```python
tool_map = {
    "calculate_sum": calculate_sum,
    "get_current_time": get_current_time
}

for tool_call in response.tool_calls:
    selected_tool = tool_map[tool_call["name"]]
    result = selected_tool.invoke(tool_call["args"])
    print(result)
```

### Multiple tool calls
A single model response can request more than one tool.

```python
response = model_with_tools.invoke(
    "What's the weather in Paris and what's the sum of 15 and 28?"
)

for tool_call in response.tool_calls:
    print(tool_call["name"], tool_call["args"])
```

### Agent
An agent runs the loop for you: model response, tool call, tool result, final answer.

```python
agent = create_agent(
    model=model,
    tools=tools,
    system_prompt="You are a helpful assistant."
)
```

### Running an agent
```python
from langchain_core.messages import HumanMessage

result = agent.invoke({
    "messages": [HumanMessage(content="What's 42 + 58?")]
})

print(result["messages"][-1].content)
```

### Agent with several steps
```python
result = agent.invoke({
    "messages": [
        HumanMessage(content="What's the weather in London? Also, what's the current time?")
    ]
})

for message in result["messages"]:
    print(type(message).__name__, message.content)
```

### Streaming an agent
Use this when you want to inspect intermediate steps or show progress in the UI.

```python
for chunk in agent.stream({
    "messages": [HumanMessage(content="Calculate 100 + 250, then explain it.")]
}):
    print(chunk)
```

## When to Use Each Operation

- `invoke`: one input, one complete response
- `stream`: one input, response arrives progressively
- `batch`: many independent inputs
- `bind_tools`: model may request tool calls, but you manage execution
- `agent`: model and tools run in a loop until final answer

## Common Mental Model

```text
Model = answer generator
Messages = conversation state
Tools = external abilities
Agent = model + tools + loop
```

## Key Idea
- LangChain provides abstractions for building larger LLM systems.
- The notebook moves from simple model calls to messages, tools, and finally autonomous agent loops.

## Progression
- Builds on [[../Prompting/Dynamic Prompting]]
- Connects to [[MCP]]
- Connects to [[LangGraph]]
- Connects to [[../RAG/RAG Basics]]
