---
tags: [ai-testing, moc]
type: map-of-content
status: active
---

# AI System Testing — Map of Content

## Testing pyramid

```text
Human review
LLM semantic evaluations
End-to-end AI evaluations
Integration tests
Deterministic unit and tool tests
```

Most tests should remain deterministic, fast, and inexpensive.

## Maturity ladder

1. Define correct behavior.
2. Unit-test ordinary code.
3. Test tools independently.
4. Smoke-test the model connection.
5. Test structured output or tool calling.
6. Test orchestration with controlled dependencies.
7. Inspect real traces.
8. Build [[Evaluation Datasets]].
9. Add deterministic evaluators.
10. Add calibrated semantic evaluators.
11. Compare experiments.
12. Add regression gates.
13. Test nondeterminism and repeated runs.
14. Inject failures.
15. Run [[Security Testing]].
16. Test state and multi-turn behavior.
17. Monitor production.

## What to test at every architecture layer

- Components
- Interfaces
- Intermediate states
- Complete execution paths
- Final output
- Failure behavior
- Security boundaries
- Latency and cost

## Architecture-specific emphasis

| Architecture | Additional focus |
|---|---|
| [[Single LLM Call]] | schema and semantic quality |
| [[Multi-Call Pipeline]] | intermediate contracts |
| [[RAG Systems]] | retrieval and groundedness |
| [[Graph-Based Workflows]] | paths and state |
| [[AI Agents]] | trajectory and stopping |
| [[Multi-Agent Systems]] | delegation and coordination |

## Related notes

- [[Evaluation Datasets]]
- [[Tracing and Observability]]
- [[Security Testing]]
- [[Failure Analysis]]

## Related audit prompts

- [[06_Prompts/AI Testing Strategy Audit|AI Testing Strategy Audit]]
- [[06_Prompts/Complete AI Testing Maturity Audit|Complete AI Testing Maturity Audit]]
