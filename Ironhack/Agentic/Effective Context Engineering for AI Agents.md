# Effective Context Engineering for AI Agents

**Source**
- Anthropic Engineering: [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- Published: 2025-09-29

**Related labs**
- `W4D2_three_reflection_skills`
- `W3D5_MCP_in_codex_and_claude_code`

## Main Techniques
- Context engineering
- Minimal high-signal context
- Clear system prompt structure
- Token-efficient tool design
- Canonical examples
- Just-in-time context retrieval
- Progressive disclosure
- Compaction
- Structured note-taking
- Sub-agent architectures

## Core Idea
Context engineering is the practice of deciding what information should enter the model's context at each step.

Prompt engineering focuses mostly on how instructions are written. Context engineering is broader: it includes system prompts, tools, examples, message history, retrieved documents, memory, and any runtime state that may affect the model's next action.

## Why It Matters
LLMs have finite attention. Larger context windows do not remove the need for selection because long contexts can dilute focus and make relevant details harder to use.

The goal is not to maximize context size. The goal is to provide the smallest useful set of high-signal tokens that makes the desired behavior more likely.

## Anatomy of Effective Context

### System prompts
Good system prompts should be clear, direct, and written at the right level of abstraction.

Too specific:
- brittle rules
- prompt logic that behaves like hardcoded `if` statements
- difficult maintenance as behavior changes

Too vague:
- high-level advice without concrete behavioral signals
- hidden assumptions about what the model already knows
- weak guidance for output shape or tool use

Better pattern:
- clear sections
- direct instructions
- enough examples to establish behavior
- minimal information that still fully explains the task

### Tools
Tools are part of context because their names, descriptions, schemas, and returned data shape how the agent thinks and acts.

Good tools are:
- self-contained
- easy to choose
- unambiguous
- robust to errors
- token-efficient in their output

Tool bloat creates confusion. If a human cannot clearly decide which tool should be used, the agent will probably struggle too.

### Examples
Few-shot examples are still useful, but they should be curated.

Useful examples:
- canonical
- diverse
- representative of the intended behavior
- short enough to avoid crowding out more important context

Weak examples:
- long lists of edge cases
- repetitive examples
- examples that encode rules better handled by tools or validation

## Runtime Context Retrieval

Agentic systems should not always preload every possible piece of context.

Just-in-time retrieval keeps lightweight references in context, then lets the agent load details only when needed.

Examples of lightweight references:
- file paths
- stored queries
- web links
- database table names
- document titles
- timestamps

This lets the agent explore progressively:
1. inspect names and metadata
2. open only likely relevant sources
3. keep useful details in working memory
4. avoid flooding the model with unrelated content

This is similar to using a file system or bookmark system: the agent does not need to memorize everything if it can reliably find the right thing at the right time.

## Long-Horizon Agent Techniques

### Compaction
Compaction summarizes a long interaction and starts a fresh context window with the important state preserved.

A good compaction should keep:
- goals
- architectural decisions
- unresolved bugs
- implementation details
- recent working files
- important constraints

It should discard:
- redundant tool output
- stale intermediate attempts
- repeated messages
- details that no longer affect the task

The first version of a compaction prompt should favor recall. After it reliably preserves important state, tune it to remove noise.

### Structured note-taking
Structured note-taking stores important state outside the context window.

Examples:
- `NOTES.md`
- task lists
- decision logs
- memory files
- progress checkpoints

This helps an agent continue work across resets or long sessions without keeping every prior message in the active context.

### Sub-agent architectures
Sub-agents let specialized agents explore a focused problem with their own context window.

Pattern:
1. lead agent defines the plan
2. sub-agent investigates or implements one focused part
3. sub-agent returns a compact result
4. lead agent integrates the result

This is useful when parallel exploration matters or when one agent would otherwise overload its context with too many details.

## Tradeoffs

Just-in-time retrieval can be slower than preloading context because the agent has to inspect and retrieve information during the task.

Preloading can be faster but risks context pollution.

Hybrid pattern:
- load stable high-value instructions up front
- keep references to large or changing sources
- retrieve details only when the task needs them

## Practical Heuristics
- Treat context as a limited resource.
- Prefer high-signal context over large context.
- Write prompts that guide behavior without hardcoding brittle logic.
- Keep the tool set small and easy to choose from.
- Return compact tool outputs.
- Give examples that demonstrate the pattern, not every possible exception.
- Let agents retrieve details at runtime when the environment is large.
- Use compaction, notes, or sub-agents for long tasks.

## Key Idea
- Prompt engineering improves the instruction.
- Context engineering improves the whole state the model reasons from.
- Effective agents depend on continuously curating that state.

## Progression
- Extends [[Prompting/Prompting Basics]]
- Extends [[Prompting/Dynamic Prompting]]
- Extends [[RAG/RAG Basics]]
- Extends [[RAG/RAG Optimization]]
- Extends [[Frameworks/LangChain]]
- Extends [[Frameworks/MCP]]
