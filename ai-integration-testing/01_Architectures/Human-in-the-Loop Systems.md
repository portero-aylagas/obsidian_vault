---
tags: [ai-integration, human-in-the-loop]
type: architecture
complexity: advanced
---

# Human-in-the-Loop Systems

## Purpose

Require human review or approval at selected control points.

```text
AI proposes → human approves, edits, or rejects → system continues
```

## Appropriate uses

- Irreversible actions
- High-value transactions
- Sensitive communications
- Low-confidence cases
- Legal, safety, or policy review

## What to test

- Approval is enforced
- Rejection prevents execution
- Edited values are used
- Resume works after interruption
- Duplicate approval is prevented
- Permissions are checked
- Audit history is complete
- Timeout and abandonment behavior are defined

## Main failure modes

- Action executes before approval
- Wrong reviewer
- Stale proposal approved
- Resume duplicates action
- Approval state is lost
- Human edits are ignored

## Related notes

- [[AI Agents]]
- [[Graph-Based Workflows]]
- [[Production Readiness]]
