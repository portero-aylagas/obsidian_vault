---
tags: [ai-integration, prompt-library, testing-audit]
type: audit-prompt
status: active
---

# AI Observability and LangSmith Testing Audit

## Prompt

```text
Audit observability for AI behavior in this project.

Check:
- Whether model calls are traced
- Whether tool calls are traced
- Whether intermediate model calls are visible
- Whether retrieval operations are visible
- Whether graph nodes/agent steps are visible
- Whether final outputs are linked to the complete trace
- Whether token usage is available
- Whether latency is available
- Whether errors are visible
- Whether model versions are recorded
- Whether prompt versions are identifiable
- Whether traces expose sensitive information
- Whether local logging duplicates tracing unnecessarily
- Whether production failures can be reproduced from traces

Return:
1. Current observability architecture
2. Missing trace information
3. Useful metadata/tags
4. Logging duplication
5. Sensitive-data risks
6. Metrics that should be monitored
7. Minimal LangSmith improvements
8. What would be unnecessary instrumentation

Rules:
- Do not edit files yet.
- Observability should help explain failures, not merely generate more logs.
- Distinguish local application logs from AI execution traces.
```

## Related notes

- [[Prompt Library]]
- [[02_Frameworks/LangSmith]]
- [[03_Quality/Tracing and Observability]]
