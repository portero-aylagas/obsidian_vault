---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# LangChain Testing Audit

## Prompt

```text
Review testing for LangChain usage in this project.

Context:
Treat LangChain as an implementation framework, not automatically as an agent architecture.

Check:
- Models
- Messages
- Prompt templates
- Structured outputs
- Tools
- Retrievers
- Middleware
- Agents if present
- Callbacks/tracing

Determine:
- Which LangChain components wrap deterministic application logic
- Which components require integration tests
- Which components make real provider calls
- Whether framework abstractions are unnecessarily mocked
- Whether application logic is too tightly coupled to LangChain classes
- Whether prompts, tools, and schemas can be tested independently
- Whether LangChain-specific tests are duplicating lower-level tests
- Whether framework upgrades could break assumptions

Return:
1. LangChain components used
2. Testing responsibility of each component
3. Unit tests
4. Integration tests
5. Evaluation requirements
6. Framework-coupling risks
7. Minimal improvements
8. What should not be abstracted further

Rules:
- Do not edit files yet.
- Base recommendations on the actual architecture, not merely the use of LangChain.
- Avoid unnecessary wrappers created only to make tests easier.
```

## Related notes

- [[Prompt Library]]
- [[02_Frameworks/LangChain]]
