---
tags: [langgraph, framework]
type: framework
status: active
---

# LangGraph

## Role

LangGraph is suited to explicit, stateful graph execution. It can represent deterministic workflows, hybrid systems, and agents.

## Core concepts

- State
- Nodes
- Edges
- Conditional routing
- Persistence
- Interruptions
- Resume
- Termination

## Testing focus

- Node unit tests
- Edge and routing tests
- State transition tests
- Path coverage
- Persistence and resume
- Loop limits
- Human approval points

## Architectural relationship

LangGraph may implement:

- [[Branching AI Workflow]]
- [[Graph-Based Workflows]]
- [[AI Agents]]
- [[Human-in-the-Loop Systems]]

## Related notes

- [[LangChain]]
- [[LangSmith]]

## Related audit prompts

- [[06_Prompts/LangGraph Testing Audit|LangGraph Testing Audit]]
