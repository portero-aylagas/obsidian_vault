# Workflow Quality Prompts

> [!info] Purpose
> Use these prompts to review orchestrated AI systems: LangGraph workflows, MCP integrations, n8n automations, guardrails, human approval flows, and submission evidence for workflow-heavy projects.

---

## LangGraph Workflow Audit

```text
Review this LangGraph workflow as an AI workflow engineer.

Context:
This is a bootcamp project. I want the workflow to be understandable, testable, and traceable without adding unnecessary complexity.

Check:
- Whether LangGraph is justified instead of a simpler chain or agent
- Whether the state schema is explicit and understandable
- Whether each node has one clear responsibility
- Whether graph edges match the intended process
- Whether conditional routing is visible and testable
- Whether LLM calls are separated from deterministic business rules
- Whether prompts are stored outside orchestration logic
- Whether structured model outputs are validated before state transitions
- Whether workflow path tracking or logging makes execution inspectable
- Whether retry, failure, or human-review points are needed
- Whether tests can run without live model calls

Return:
1. Current workflow summary
2. State schema assessment
3. Node and edge issues
4. Traceability and debugging risks
5. Minimal improvements
6. Tests to add or improve
7. What would be over-engineering

Rules:
- Do not edit files yet.
- Prefer clear staged workflows over clever graph logic.
- Distinguish local lab needs from production workflow needs.
```

---

## MCP Integration Audit

```text
Review this MCP integration.

Context:
This project may connect an agent to filesystem, Git, documentation, APIs, or app tools through MCP. I want to know whether MCP is being used clearly and safely.

Check:
- Which MCP servers are configured
- Which tools and resources are exposed
- Whether tool names and descriptions are clear enough for the agent
- Whether MCP is justified compared with direct API calls
- Whether setup steps and environment requirements are documented
- Whether connection failures are handled or surfaced clearly
- Whether tool outputs are compact and useful to the model
- Whether file/API access is appropriately scoped
- Whether credentials or secrets are protected
- Whether the integration can be tested with a simple validation prompt

Return:
1. MCP architecture summary
2. Tool/resource inventory
3. Direct API vs MCP tradeoff
4. Setup and reliability risks
5. Security or scope concerns
6. Minimal improvements
7. Validation prompts or commands

Rules:
- Do not edit files yet.
- Do not recommend MCP if a direct API call is simpler and clearer for the project.
- Focus on debuggability and boundaries.
```

---

## n8n Workflow Audit

```text
Review this n8n workflow or exported workflow folder.

Context:
This is a bootcamp automation project. I want to understand whether the workflow is reliable, inspectable, and easy to explain.

Check:
- What starts the workflow: manual, schedule, webhook, chat, app trigger, or test input
- Whether each node has a clear role
- Whether input and output JSON are understood after each important node
- Whether field mappings use the correct nested paths
- Whether Code nodes are necessary and readable
- Whether Split Out, Edit Fields, Set, HTTP Request, and app nodes are used correctly
- Whether credentials are referenced without exposing secret values
- Whether retries are configured where failures are temporary
- Whether error workflows or failure branches exist where needed
- Whether idempotency or duplicate guards are needed
- Whether scheduled workflows handle timezone and repeat runs correctly
- Whether exported JSON, screenshots, or execution history prove the workflow works

Return:
1. Workflow summary
2. Node-by-node role table
3. JSON contract risks
4. Reliability risks
5. Credential/security risks
6. Evidence gaps
7. Minimal improvements before submission

Rules:
- Do not edit files yet.
- Treat n8n as JSON orchestration, not just visual wiring.
- Prefer practical workflow fixes over production architecture.
```

---

## Guardrails and Human Approval Audit

```text
Review guardrails, safety checks, and human approval behavior in this AI system.

Check:
- Which inputs are validated before model calls
- Which outputs are validated before downstream use
- Whether PII, secrets, or sensitive data are redacted or blocked
- Whether policy checks are deterministic, model-based, or both
- Whether middleware or guardrails are placed at the right stage
- Whether high-risk actions require human approval
- Whether rejected or escalated requests return clear messages
- Whether failures are logged or surfaced clearly
- Whether tests cover allowed, blocked, and escalated cases
- Whether the guardrails are too broad, brittle, or easy to bypass

Return:
1. Current guardrail design
2. Input risks
3. Output/downstream risks
4. Human approval gaps
5. Minimal improvements
6. Test cases to add
7. What would be over-engineering for this project

Rules:
- Do not edit files yet.
- Keep the review practical for a bootcamp project.
- Distinguish safety-critical issues from polish.
```

---

## Workflow Submission Evidence Prompt

```text
Review this workflow-heavy project for submission evidence.

Context:
The reviewer may not run every external integration. The project needs clear proof that the workflow works.

Check:
- Whether the repository includes exported workflow files
- Whether screenshots show the full workflow and key result states
- Whether sample inputs and expected outputs are documented
- Whether execution history or logs show success, retry, and failure cases
- Whether external app results are visible without exposing secrets
- Whether credentials are documented as required but not included
- Whether the README explains how to import, configure, and run the workflow
- Whether known limitations are stated
- Whether the student contribution is clear

Return:
1. Evidence currently present
2. Evidence missing
3. What a reviewer can verify quickly
4. Submission blockers
5. Minimal evidence checklist
6. Suggested README/demo explanation

Rules:
- Do not edit files yet.
- Do not ask for unnecessary polish screenshots.
- Focus on evidence that proves behavior.
```
