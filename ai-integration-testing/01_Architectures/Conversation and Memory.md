---
tags: [ai-integration, memory, conversation]
type: architecture
complexity: intermediate
---

# Conversation and Memory

## Purpose

Preserve useful information across turns or sessions.

## Memory types

- Full message history
- Summarized conversation
- Structured user facts
- Task or workflow state
- Long-term semantic memory
- External records

## What to test

- Correct retention
- Corrections and contradictions
- Stale information
- Forgetting and deletion
- Cross-user isolation
- Context growth
- Summary accuracy
- Restart and persistence
- Multi-turn prompt injection

## Sequence example

```text
Turn 1: state introduced
Turn 2: state referenced
Turn 3: state corrected
Turn 4: prior value must no longer be used
```

## Main failure modes

- False memory
- Lost constraint
- Old data overrides new data
- Information leaks between users
- Compressed summaries remove important facts
- Persistent malicious instructions

## Related notes

- [[Graph-Based Workflows]]
- [[AI Agents]]
- [[Security Testing]]

## Related audit prompts

- [[06_Prompts/Conversational State and Memory Testing Audit|Conversational State and Memory Testing Audit]]
