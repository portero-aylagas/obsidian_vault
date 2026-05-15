# W4D1 LangChain Guardrails Lab

**Source folder**
- `W4D1_langchain_guardrails`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- guided / safety sensitization lab
- Main value: learn guardrails as layered controls around an agent, especially for sensitive data and high-risk actions

## What This Lab Teaches

This lab frames agent safety as a layered system:

```text
user input
-> before-agent guardrails
-> agent + tools
-> after-agent guardrails
-> safe response or blocked action
```

The main learning is that guardrails are not only prompts. They can be deterministic filters, middleware, human approval steps, and audit mechanisms.

## Techniques Practiced

- PII detection
- PII redaction
- prompt-injection testing
- LangChain middleware
- before-agent hooks
- after-agent hooks
- deterministic guardrails
- model-based safety checks
- human-in-the-loop approval
- state persistence for approvals
- layered guardrail design

## Important Architecture

```text
Input protection:
PII middleware + content filter

Tool protection:
approval required for sensitive tools

Output protection:
model-based safety review + redaction

Operations:
audit logs + monitoring
```

This is defense in depth: each layer catches a different class of risk.

## Important Code Patterns

### PII middleware shape

```python
middleware = [
    PIIMiddleware("email", strategy="redact", apply_to_input=True),
    PIIMiddleware("email", strategy="redact", apply_to_output=True),
]
```

### Custom guardrail shape

```python
class ContentFilterMiddleware(AgentMiddleware):
    def before_agent(self, state, runtime):
        ...
```

## What Was Provided

The lab source provides scenario, middleware examples, prompt-injection tests, and optional guardrail layers. The workspace currently contains the HTML source but no submitted Python implementation.

## What I Practiced

- thinking about agent safety before deployment
- distinguishing deterministic and model-based controls
- recognizing PII leakage risk
- using middleware as an agent boundary
- adding approval gates for sensitive operations

## Links to Topic Notes

- [[../Frameworks/LangChain]]
- [[../Engineering/Code Quality and Automation]]
- [[../APIs/Reliability Patterns]]

## What To Reuse Later

- Put sensitive checks before the agent when possible.
- Validate outputs as well as inputs.
- Require human approval for destructive or high-stakes tools.
- Log guardrail triggers for later review.
- Test guardrails with prompt-injection attempts, not only happy paths.

## Improvement Ideas

- Add domain-specific PII detectors.
- Add rate limiting for abuse prevention.
- Track guardrail false positives and false negatives.
- Create an audit log for compliance review.
- Tune safety thresholds based on observed failures.

## Key Takeaway

Guardrails are an architecture choice: reliable agents need layered controls around inputs, tools, outputs, and operations.
