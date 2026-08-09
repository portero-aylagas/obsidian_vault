---
tags: [ai-integration, prompt-library, moc]
type: prompt-library
status: active
---

# Prompt Library

Audit prompts for coding agents such as Codex or Claude Code. The library follows the same principle as the testing wiki: start with the architecture actually present, use deterministic tests where possible, and add AI-specific evaluation only where nondeterminism requires it.

> [!tip]
> Start with **[[AI Architecture vs Testing Complexity Audit]]** when you are not yet sure what kind of AI system the project contains. Then use the matching architecture-specific prompt.


## Start here

- [[06_Prompts/AI Architecture vs Testing Complexity Audit|AI Architecture vs Testing Complexity Audit]]
- [[06_Prompts/AI Testing Strategy Audit|AI Testing Strategy Audit]]
- [[06_Prompts/Complete AI Testing Maturity Audit|Complete AI Testing Maturity Audit]]

## Architecture-specific audits

- [[06_Prompts/Single LLM Call Testing Audit|Single LLM Call Testing Audit]]
- [[06_Prompts/Multi-Call Pipeline Testing Audit|Multi-Call Pipeline Testing Audit]]
- [[06_Prompts/Branching Workflow Testing Audit|Branching Workflow Testing Audit]]
- [[06_Prompts/AI Tool Integration Testing Audit|AI Tool Integration Testing Audit]]
- [[06_Prompts/RAG Testing Strategy Audit|RAG Testing Strategy Audit]]
- [[06_Prompts/Conversational State and Memory Testing Audit|Conversational State and Memory Testing Audit]]
- [[06_Prompts/LangChain Testing Audit|LangChain Testing Audit]]
- [[06_Prompts/LangGraph Testing Audit|LangGraph Testing Audit]]
- [[06_Prompts/Agent Testing Strategy Audit|Agent Testing Strategy Audit]]
- [[06_Prompts/Agentic RAG Testing Audit|Agentic RAG Testing Audit]]
- [[06_Prompts/Multi-Agent System Testing Audit|Multi-Agent System Testing Audit]]

## Evaluation and regression

- [[06_Prompts/AI Evaluation Dataset Audit|AI Evaluation Dataset Audit]]
- [[06_Prompts/AI Evaluator Quality Audit|AI Evaluator Quality Audit]]
- [[06_Prompts/AI Regression Testing Audit|AI Regression Testing Audit]]

## Reliability, security, and operations

- [[06_Prompts/AI Failure Injection Audit|AI Failure Injection Audit]]
- [[06_Prompts/AI Security Testing Audit|AI Security Testing Audit]]
- [[06_Prompts/AI Observability and LangSmith Testing Audit|AI Observability and LangSmith Testing Audit]]
- [[06_Prompts/AI CI-CD Testing Audit|AI CI-CD Testing Audit]]
- [[06_Prompts/AI Production Readiness Testing Audit|AI Production Readiness Testing Audit]]

## Suggested audit sequence

```text
Architecture classification
→ General testing strategy
→ Architecture-specific audit
→ Evaluation dataset
→ Evaluator quality
→ Regression testing
→ Failure injection
→ Security
→ Observability
→ CI/CD
→ Production readiness
```

## Related wiki notes

- [[AI Integration - MOC]]
- [[03_Quality/AI System Testing - MOC]]
- [[04_Operations/Production Readiness]]
