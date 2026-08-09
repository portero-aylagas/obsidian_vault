---
tags: [langchain, framework]
type: framework
status: active
---

# LangChain

## Role

LangChain is an application framework offering abstractions for model calls, messages, tools, structured output, retrieval, agents, middleware, and tracing integrations.

It is **not** an architecture by itself.

A LangChain application may implement:

- [[Single LLM Call]]
- [[Multi-Call Pipeline]]
- [[RAG Systems]]
- [[AI Agents]]

## Testing rule

Test according to the architecture built with LangChain, not according to the library name.

## Useful abstraction boundaries

- Model interface
- Message construction
- Prompt templates
- Structured output
- Tool schemas
- Retrievers
- Agent execution
- Callbacks and tracing

## Common mistakes

- Treating LangChain as synonymous with agents
- Hiding too much application logic inside prompts
- Failing to validate model output
- Testing only the final response
- Ignoring intermediate messages and tool calls

## Related notes

- [[LangGraph]]
- [[LangSmith]]
- [[Architecture Classification]]

## Related audit prompts

- [[06_Prompts/LangChain Testing Audit|LangChain Testing Audit]]
