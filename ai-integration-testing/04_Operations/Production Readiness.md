---
tags: [production, ai-operations]
type: checklist
---

# Production Readiness

## Reliability

- [ ] Timeouts are configured.
- [ ] Retries are bounded and safe.
- [ ] Rate limits are handled.
- [ ] External failures have explicit fallbacks.
- [ ] Loops and tool calls have maximum limits.
- [ ] Side effects are idempotent where possible.

## Quality

- [ ] A representative evaluation dataset exists.
- [ ] Baseline metrics are recorded.
- [ ] Critical regression gates exist.
- [ ] Production failures can be converted into test cases.

## Observability

- [ ] Traces identify model, prompt, tool, and dataset versions.
- [ ] Errors, latency, tokens, and tool failures are measurable.
- [ ] Sensitive content is redacted or access-controlled.

## Security

- [ ] Tool arguments are validated.
- [ ] Authorization is outside the model.
- [ ] Prompt injection is tested.
- [ ] High-impact actions require approval.
- [ ] Tenant and user data are isolated.

## Cost and performance

- [ ] Cost per successful task is known.
- [ ] P50 and P95 latency are measured.
- [ ] Caching and context size are controlled.
- [ ] Expensive evaluation is sampled appropriately.

## Operational loop

```text
Production issue
→ inspect trace
→ classify root cause
→ add regression case
→ fix component
→ compare experiment
→ deploy
→ monitor
```

## Related notes

- [[Tracing and Observability]]
- [[Failure Analysis]]
- [[Security Testing]]

## Related audit prompts

- [[06_Prompts/AI Production Readiness Testing Audit|AI Production Readiness Testing Audit]]
- [[06_Prompts/AI CI-CD Testing Audit|AI CI-CD Testing Audit]]
