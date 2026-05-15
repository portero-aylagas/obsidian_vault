# AI System Quality Prompts

> [!info] Purpose
> Use these prompts to review the AI-specific parts of a project: prompts, structured outputs, RAG, LangChain, speech, providers, and cost tracking.

---

## Prompt Quality Audit

```text
Review the prompts in this project.

Context:
This is a bootcamp AI project. I want to improve prompt quality without overcomplicating the code.

Check:
- What task each prompt is trying to solve
- Whether the prompt is too vague
- Whether the prompt gives enough context
- Whether the prompt defines the audience, tone, format, or constraints
- Whether examples would improve the prompt
- Whether the task should use zero-shot, one-shot, or few-shot prompting
- Whether the output format is constrained enough
- Whether the prompt is mixed into application logic
- Whether temperature/model settings match the task
- Whether the prompt should be replaced by structured output

Return:
1. Prompt inventory by file/function
2. Current prompt technique used
3. Prompt weaknesses
4. Minimal improved prompt examples
5. When to use lower/higher temperature
6. What not to change

Rules:
- Do not edit files yet.
- Do not rewrite all prompts.
- Focus on high-impact prompt improvements.
```

---

## Dynamic Prompting Audit

```text
Audit dynamic prompt construction in this project.

Check:
- Which variables are injected into prompts
- Whether user input is inserted safely and clearly
- Whether context is separated from instructions
- Whether tone, audience, style, and length controls are explicit
- Whether prompt templates are easier to maintain than inline strings
- Whether the prompt can be logged or inspected for debugging
- Whether prompt construction is duplicated across files
- Whether missing inputs produce clear errors

Return:
1. Current dynamic prompting pattern
2. Variables injected into prompts
3. Risks or weaknesses
4. Minimal improvements
5. Example improved prompt template
6. What would be over-engineering

Rules:
- Do not edit files yet.
- Keep recommendations beginner/intermediate-friendly.
```

---

## Structured Output and Pydantic Audit

```text
Review structured outputs and schema validation in this project.

Check:
- Whether model output is free text, JSON-like text, or validated schema
- Whether downstream code depends on exact fields
- Whether Pydantic models are used where needed
- Whether fields have clear types
- Whether required and optional fields are appropriate
- Whether validation errors are handled clearly
- Whether raw model output is stored when parsed output should be stored
- Whether malformed JSON can break the workflow

Return:
1. Current output format assessment
2. Where structured output is needed
3. Schema weaknesses
4. Minimal Pydantic model improvements
5. Error handling improvements
6. What is acceptable for a local lab

Rules:
- Do not edit files yet.
- Do not introduce schemas for outputs that do not need them.
```

---

## LLM/API Integration Audit

```text
Review the LLM/API integration in this project.

Check:
- Whether API keys are read safely from environment variables
- Whether model names are hardcoded unnecessarily
- Whether temperature and model selection are configurable
- Whether prompts are isolated from application logic
- Whether prompt construction is clean
- Whether API responses are parsed safely
- Whether failures from the LLM provider are handled
- Whether usage/tokens/cost are tracked when useful
- Whether the app can support multiple providers later
- Whether adding another provider would require changing many files
- Whether there is unnecessary abstraction already

Return:
1. Current LLM integration assessment
2. Problems
3. Minimal improvements
4. Optional future improvements
5. What would be over-engineering right now

Rules:
- Do not edit files yet.
- Distinguish local project needs from production needs.
```

---

## RAG and Chunking Audit

```text
Review the RAG or document-context pipeline in this project.

Check:
- How documents are loaded
- How text is cleaned
- Which chunking strategy is used
- Chunk size and overlap
- Whether chunk boundaries preserve meaning
- Whether token limits are considered
- Whether embeddings are used
- Whether vector search is used
- Whether retrieved context actually answers the question
- Whether metadata filtering is needed
- Whether reranking is needed
- Whether the app is true vector RAG or deterministic context assembly
- Whether hallucination risk is increased by poor retrieval

Return:
1. Current RAG/context pipeline summary
2. Chunking strategy assessment
3. Retrieval/context quality risks
4. Minimal improvements
5. Test questions to evaluate retrieval
6. What would be over-engineering now

Rules:
- Do not edit files yet.
- Do not recommend vector databases if the current structured context approach is sufficient.
```

---

## LangChain Agent and Tools Audit

```text
Review the LangChain agent and tools in this project.

Check:
- Whether the project really needs an agent
- How the model is initialized
- Whether prompts are separated from runtime logic
- Whether tools have clear names and descriptions
- Whether tool inputs are typed clearly
- Whether tool outputs are useful to the model
- Whether tools hide too much logic
- Whether data is separated from tool logic
- Whether final answer extraction is correct
- Whether the agent flow is debuggable
- Whether errors from tool calls or model calls are handled

Return:
1. Current agent architecture summary
2. Tool inventory and purpose
3. Problems by file/function
4. Minimal improvements
5. What should stay simple
6. Whether this should remain an agent or become a simpler chain

Rules:
- Do not edit files yet.
- Do not add advanced LangChain patterns unless clearly justified.
```

---

## Speech Pipeline Audit

```text
Review the speech pipeline in this project.

Check:
- How audio is loaded or recorded
- Whether audio is converted to the right format
- Whether long audio is chunked
- Whether chunk offsets are handled correctly
- Whether timestamps are preserved or reconstructed
- Whether prompted transcription is used for domain vocabulary
- Whether prompted vs unprompted transcription is compared
- Whether TTS voice selection is clear
- Whether generated audio segments are validated before merging
- Whether transcript and audio outputs stay aligned
- Whether file cleanup/output naming is safe

Return:
1. Current speech pipeline summary
2. STT risks
3. TTS risks
4. Chunking/timestamp risks
5. Minimal improvements
6. What is acceptable for a local lab

Rules:
- Do not edit files yet.
- Keep recommendations focused on reliability and clarity.
```

---

## Agent Skill Audit

```text
Review the agent skills in this project or repository.

Check:
- Whether each skill solves one coherent repeated workflow
- Whether `SKILL.md` has clear `name` and `description` frontmatter
- Whether the description is written for user intent and implicit activation
- Whether the skill boundaries prevent false triggers
- Whether the main instructions are lean enough for context use
- Whether long details should move into `references/`
- Whether deterministic repeat steps should move into `scripts/`
- Whether templates or examples belong in `assets/`
- Whether the skill explains when to use MCP tools, CLI commands, or repo files
- Whether the skill can be tested with realistic prompts

Return:
1. Skill inventory
2. Activation description assessment
3. Scope and boundary issues
4. Progressive disclosure problems
5. Minimal improvements
6. Test prompts for validating the skill
7. What would be over-engineering

Rules:
- Do not edit files yet.
- Prefer small, focused skills over broad meta-skills.
- Keep recommendations grounded in actual repeated work.
```

---

## AI Evaluation Audit

```text
Review how this AI project evaluates output quality.

Context:
This is a bootcamp project, so evaluation should be lightweight but intentional. I want to know whether the project tests more than one happy-path example.

Check:
- Whether there are representative test inputs
- Whether expected outputs or success criteria are defined
- Whether prompt behavior is tested across repeated runs
- Whether structured outputs are validated against schemas
- Whether RAG answers are checked against source evidence
- Whether retrieval is tested with realistic questions
- Whether speech transcription uses reference text, WER, or qualitative comparison
- Whether cost and latency are tracked when many calls are made
- Whether failure cases are tested, not only successful examples
- Whether evaluation results are easy to compare between versions

Return:
1. Current evaluation approach
2. What is being measured
3. Missing success criteria
4. Minimal evaluation set to add
5. Cost/latency considerations
6. What would be over-engineering for this project

Rules:
- Do not edit files yet.
- Prefer small repeatable checks over complex evaluation frameworks.
- Distinguish model-quality evaluation from normal software tests.
```

---

## AI Cost and Usage Audit

```text
Review token, cost, and usage tracking in this project.

Check:
- Whether the app makes one call or many calls
- Whether usage should be tracked
- Whether the code uses direct provider usage or estimates
- Whether pricing is hardcoded
- Whether pricing may become stale
- Whether total requests, total tokens, and total cost are visible
- Whether budget limits or warnings exist
- Whether cost tracking is mixed into business logic
- Whether the UI or report should show usage

Return:
1. Current usage tracking summary
2. Whether tracking is necessary for this project
3. Problems or inaccuracies
4. Minimal improvements
5. What would be unnecessary for a small lab

Rules:
- Do not edit files yet.
- Avoid making cost tracking more complex than the project requires.
```
