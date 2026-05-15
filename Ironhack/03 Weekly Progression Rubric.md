# Weekly Progression Rubric

> [!info] Purpose
> This note measures progression through the bootcamp.
> It answers:
> - What should I know after each week?
> - What should I be able to build?
> - What does the output of an AI engineer look like at that stage?

Team projects are not the main reference point here; they are treated as applied products of the weekly skills.

---

## High-Level Progression

| Week | Main Shift | Engineer Output |
|---|---|---|
| Week 1 | Learn the components | scripts and notebooks that call models, process data, and handle speech/image inputs |
| Week 2 | Make AI work reliable and controlled | reusable functions, prompt experiments, wrappers, validation, tests, fallback, cost tracking |
| Week 3 | Compose AI systems | dynamic prompts, RAG pipelines, tools, agents, LangChain/MCP integrations |
| Week 4 | Orchestrate AI workflows | explicit state graphs and low-code automations that connect apps and AI steps |

The progression is:

```text
Week 1: Can use AI components
Week 2: Can engineer AI components responsibly
Week 3: Can compose components into AI systems
Week 4: Can orchestrate AI systems into workflows and app integrations
```

---

## Week 1: Foundations and Core AI Components

### Expected Knowledge After Week 1

You should understand:

- how to parse JSON-like API responses
- how to load and inspect data with `pandas`
- how to structure small data-processing workflows
- the basic supervised ML workflow
- classification vs regression
- basic neural network training flow
- what transformer pipelines can do
- how to call the OpenAI API
- how to send text and image inputs to a model
- how to use structured outputs with Pydantic
- how speech-to-text and text-to-speech workflows work

### Techniques You Should Recognize

- JSON parsing
- `pandas` DataFrames
- train/test split
- scaling
- KNN, logistic regression, random forest
- model evaluation metrics
- Keras model definition, compile, fit, evaluate
- Hugging Face zero-shot classification
- OpenAI `responses.create`
- OpenAI `chat.completions.create`
- image input
- Pydantic schemas
- Whisper transcription
- TTS voice generation

### What You Should Be Able To Build

By the end of Week 1, you should be able to build:

- a Python notebook that processes structured data
- a simple sklearn classification model
- a simple neural network training notebook
- a script that calls the OpenAI API
- a prompt that sends text and image input
- a basic structured-output extraction task
- a speech-to-text transcription workflow
- a basic text-to-speech generation workflow

### What an Engineer's Product Looks Like After Week 1

The product is usually still a notebook or small script.

It may look like:

```text
input data or prompt
-> Python processing
-> model/API call
-> printed or saved output
```

Typical outputs:

- a dataframe analysis
- a trained model with metrics
- a generated product description
- a parsed JSON output
- a transcript
- an audio file

### Quality Bar After Week 1

The output should:

- run from top to bottom
- load data correctly
- call the API correctly
- save or print the result
- show basic understanding of the response structure
- include basic comments or markdown explanations

It is not yet expected to be fully modular, tested, or production-ready.

### Week 1 Key Learning

The main Week 1 learning is:

```text
I can use the individual building blocks of AI applications.
```

---

## Week 2: Control, Reliability, and Engineering Discipline

### Expected Knowledge After Week 2

You should understand:

- prompting is an experimental process
- outputs can vary even with the same prompt
- parameters affect stability, creativity, length, and repetition
- prompts should be tested across repeated runs
- model output should be validated when software depends on it
- API calls should be wrapped instead of duplicated
- helper functions make code easier to test and reuse
- retries and circuit breakers protect systems from API failures
- provider fallback improves resilience
- token and cost tracking matter in real applications
- tests are part of AI engineering, not an optional extra

### Techniques You Should Recognize

- zero-shot prompting
- one-shot prompting
- few-shot prompting
- role prompting
- emotional prompting
- chain-of-thought prompting
- prompt iteration
- prompt testing
- temperature control
- `top_p`
- `max_tokens`
- frequency and presence penalties
- seed-based reproducibility
- meta-prompting
- helper functions
- refactoring monolithic code
- API wrapper classes
- standardized response objects
- Pydantic validation
- pytest unit tests
- fake clients and mocks
- exponential backoff
- jitter
- circuit breaker
- multi-provider fallback
- token/cost tracking
- rate limiting

### What You Should Be Able To Build

By the end of Week 2, you should be able to build:

- a prompt experiment notebook with repeated runs and comparisons
- a task-specific prompt that gives more consistent output than a baseline prompt
- a JSON/Pydantic validation workflow
- an API wrapper around model calls
- a small tested Python module
- a multi-provider LLM workflow with fallback
- a cost-tracked summarization or classification pipeline
- a basic async processing pattern for independent items

### What an Engineer's Product Looks Like After Week 2

The product should start looking less like a single notebook and more like a small application module.

It may look like:

```text
input
-> validation
-> reusable helper functions
-> API wrapper
-> prompt/model call
-> structured response
-> error handling
-> tests
```

Typical outputs:

- validated JSON files
- reusable wrapper classes
- tested helper functions
- prompt comparison results
- provider fallback results
- token/cost reports
- summarized articles with sentiment analysis

### Quality Bar After Week 2

The output should:

- avoid duplicated API code
- separate loading, processing, prompting, and saving
- validate structured data
- handle at least common failure modes
- include tests for pure logic
- track cost or usage when many calls are made
- be understandable as a small codebase, not only a notebook

### Week 2 Key Learning

The main Week 2 learning is:

```text
I can control, validate, test, and protect AI workflows.
```

Week 2 is the biggest jump in engineering maturity.

---

## Week 3: Composition, RAG, Tools, and Agents

### Expected Knowledge After Week 3

You should understand:

- prompts can be built dynamically from runtime data
- conversation memory is a growing message list
- external context can be injected into prompts
- RAG is retrieval plus dynamic prompting
- chunking strategy affects retrieval quality
- embeddings turn text into searchable vectors
- vector stores retrieve semantically similar content
- LangChain provides abstractions for models, messages, tools, and agents
- tools let models interact with external functions
- agents are loops that combine model reasoning and tool use
- MCP standardizes tool and resource access
- modular agent structure matters

### Techniques You Should Recognize

- dynamic prompt construction
- variable injection
- style injection
- context injection
- prompt templates
- conversation memory
- document loading
- PDF loading
- chunking
- recursive chunking
- token chunking
- semantic chunking
- embeddings
- vector stores
- Pinecone
- similarity search
- RAG prompt formatting
- query rewriting
- sub-query decomposition
- parent document retrieval
- reranking
- metadata filtering
- LangChain `invoke`
- LangChain `stream`
- LangChain `batch`
- `SystemMessage`, `HumanMessage`, `AIMessage`
- `@tool`
- Pydantic tool schemas
- tool binding
- manual tool execution
- `create_agent`
- agent result parsing
- MCP tools
- MCP resources
- MCP interceptors

### What You Should Be Able To Build

By the end of Week 3, you should be able to build:

- a function that builds prompts dynamically from user inputs
- a chat flow that preserves message history
- a basic RAG pipeline over documents
- a chunking comparison notebook
- a retrieval pipeline using embeddings and a vector store
- a LangChain model wrapper using `invoke`, `stream`, and `batch`
- a LangChain tool
- a simple agent with tools
- a modular agent project with separate files for prompts, tools, data, and runtime logic
- a basic MCP-connected agent that can use external tools

### What an Engineer's Product Looks Like After Week 3

The product should now look like an AI system rather than a single model call.

It may look like:

```text
user input
-> dynamic prompt or retrieval query
-> context/document/tool selection
-> model or agent execution
-> structured or final response
-> optional tool calls
-> logged/inspectable result
```

For RAG:

```text
documents
-> chunks
-> embeddings
-> vector store
-> retrieval
-> context prompt
-> answer
```

For agents:

```text
user request
-> model decides next step
-> tool call
-> tool result
-> model continues
-> final answer
```

Typical outputs:

- a RAG question-answering notebook
- a chunking comparison
- a LangChain tool demo
- a simple tool-using agent
- a modular agent project
- an MCP-connected agent example

### Quality Bar After Week 3

The output should:

- separate prompts from runtime logic
- separate tools from agent setup
- keep data separate from code when possible
- make retrieval/chunking choices explicit
- make context injection visible and debuggable
- expose tool inputs and outputs clearly
- show understanding of when to use direct API calls, RAG, tools, or agents

It does not yet need to be production-grade, but it should be architecturally understandable.

### Week 3 Key Learning

The main Week 3 learning is:

```text
I can compose AI components into systems that use context, tools, and agents.
```

---

## Week 4: Workflow Orchestration and App Integration

### Expected Knowledge After Week 4

You should understand:

- why some AI systems need explicit workflow stages instead of freeform agents
- how LangGraph represents a workflow as state, nodes, and edges
- how typed state makes a multi-step AI process easier to inspect
- how deterministic workflow order improves traceability
- how to combine LLM calls with business rules inside a graph
- how n8n workflows pass JSON items between nodes
- how trigger nodes, model nodes, Code nodes, and app nodes fit together
- how to normalize nested app payloads before writing them elsewhere
- why inspecting node input/output JSON is the main n8n debugging habit
- how agent skills package repeatable agent behavior into reusable instructions
- how progressive disclosure keeps skill context lightweight

### Techniques You Should Recognize

- `StateGraph`
- typed workflow state
- graph nodes and edges
- graph compilation
- workflow path tracking
- strict JSON prompts inside workflow nodes
- validation before resolution
- duplicate detection and linked-case handling
- tested workflow rules with mocked LLM output
- n8n trigger nodes
- AI Agent nodes
- chat model nodes
- Simple Memory
- Code / Format Blocks nodes
- Split Out
- Edit Fields / Set
- Notion and Airtable app nodes
- HTTP Request nodes
- nested JSON expressions
- agent skills
- `SKILL.md`
- skill description routing
- progressive disclosure
- `scripts/`, `references/`, and `assets/`

### What You Should Be Able To Build

By the end of Week 4, you should be able to build:

- a LangGraph workflow with explicit stages
- a typed state object that carries data across workflow nodes
- a workflow that uses LLM calls inside controlled steps
- tests for workflow rules without relying on live model calls
- an n8n workflow that starts from a trigger and writes to an external app
- an n8n workflow that reshapes nested JSON into app-ready fields
- a node reference table that documents input, output, and transformation behavior
- a focused agent skill for one repeated workflow

### What an Engineer's Product Looks Like After Week 4

The product should now show orchestration, not only AI capability.

For LangGraph:

```text
input
-> typed state
-> node 1
-> node 2
-> node 3
-> final structured state
```

For n8n:

```text
external trigger
-> JSON transformation
-> AI or app node
-> destination app record
```

Typical outputs:

- a structured workflow application
- a tested graph-based process
- an exported n8n workflow
- app integration screenshots
- node reference documentation
- a reusable agent skill with clear activation rules

### Quality Bar After Week 4

The output should:

- make workflow stages explicit
- make state changes inspectable
- separate prompts, data, workflow logic, and tests
- validate structured model output where the workflow depends on it
- document n8n node inputs and outputs
- verify app integrations with exported workflow JSON or screenshots
- avoid hiding critical behavior inside uninspected node expressions
- keep agent skills scoped, lean, and routed by clear descriptions

### Week 4 Key Learning

The main Week 4 learning is:

```text
I can orchestrate AI systems into explicit workflows and app integrations.
```

---

## Progression by Engineer Capability

| Capability | After Week 1 | After Week 2 | After Week 3 | After Week 4 |
|---|---|---|---|---|
| Python/data handling | basic scripts and notebooks | reusable functions and validation | used inside larger pipelines | used inside workflow nodes and tests |
| Prompting | basic prompts and API calls | tested and refined prompts | dynamic prompts from runtime data | strict prompts inside controlled workflow stages |
| Structured output | basic Pydantic examples | validation workflows | used as part of pipelines/tools | required for state transitions and resolution records |
| API usage | direct model calls | wrappers, fallback, cost tracking | integrated into agents/RAG systems | integrated into low-code app workflows |
| Speech | STT/TTS basics | can be part of workflows | can be combined with larger pipelines | can become one step in orchestrated systems |
| RAG | not yet central | chunking begins conceptually | full retrieval and context-injection pipelines | retrieval quality can be evaluated inside larger workflows |
| LangChain | not yet central | not yet central | models, messages, tools, agents | foundation for structured LangGraph workflows |
| LangGraph | not yet central | not yet central | not yet central | explicit state graphs and workflow orchestration |
| Low-code automation | not yet central | simple integration awareness | external tools through agents/MCP | n8n workflows across triggers, models, transformations, and apps |
| Agent skills | not yet central | not yet central | agent behavior is mostly coded in project files | reusable skill instructions with progressive disclosure |
| Code quality | mostly notebooks | modular functions, wrappers, tests | modular AI systems | tested workflow rules and documented app automations |
| Evaluation mindset | basic model metrics | repeated prompt tests | retrieval/tool behavior inspection | workflow traceability and node-level JSON inspection |

---

## What To Measure Each Week

### Week 1 Measurement Questions

- Can I call an AI API successfully?
- Can I parse the response?
- Can I send text, image, or audio input?
- Can I save the output?
- Can I train and evaluate a basic ML model?
- Can I explain what each step in the notebook does?

### Week 2 Measurement Questions

- Can I improve a weak prompt systematically?
- Can I test a prompt across multiple runs?
- Can I validate JSON/model output?
- Can I refactor repeated code into helper functions?
- Can I write tests for pure logic?
- Can I wrap API calls behind a reusable class/function?
- Can I track token or cost usage?
- Can I add fallback behavior?

### Week 3 Measurement Questions

- Can I build a prompt dynamically from variables and context?
- Can I explain how RAG differs from normal prompting?
- Can I compare chunking strategies?
- Can I create embeddings and retrieve relevant chunks?
- Can I create a LangChain tool?
- Can I explain what an agent loop does?
- Can I separate agent, tools, prompts, and data into modules?
- Can I explain when not to use an agent?

### Week 4 Measurement Questions

- Can I explain when a graph workflow is better than a freeform agent?
- Can I define a typed state object for a multi-step AI workflow?
- Can I trace how state changes from node to node?
- Can I test workflow rules with mocked model responses?
- Can I explain the role of each node in an n8n workflow?
- Can I inspect n8n input/output JSON to debug a field mapping?
- Can I normalize nested app data before writing it to another app?
- Can I verify a workflow with exported JSON, screenshots, or structured output?

---

## Final Summary

After Week 1, you should be able to use AI components.

After Week 2, you should be able to engineer those components with better control, reliability, validation, and tests.

After Week 3, you should be able to compose those components into larger AI systems using dynamic prompts, RAG, tools, and agents.

After Week 4, you should be able to orchestrate those systems into predictable workflows and app integrations.

The expected engineer progression is:

```text
Week 1 engineer: can run and adapt AI notebooks
Week 2 engineer: can build small reliable AI modules
Week 3 engineer: can design simple AI systems with context and tools
Week 4 engineer: can orchestrate AI workflows with explicit state and app automation
```
