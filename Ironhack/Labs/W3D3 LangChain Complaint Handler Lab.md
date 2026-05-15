# W3D3 LangChain Complaint Handler Lab

**Source folder**
- `W3D3_NormalObjects_Creative_Complaint_Handler_LangChain`

**Main files**
- `normalobjects_langchain.py`
- `src/complaint_handler/agent.py`
- `src/complaint_handler/prompts.py`
- `src/complaint_handler/tools/`
- `src/complaint_handler/data/`

**Lab type**
- Provided-code / template-heavy LangChain lab
- Main value: understand agent structure, tools, prompts, and modular organization

## What This Lab Teaches

This lab builds a creative complaint handler using a LangChain agent.

Pipeline:

```text
complaint text
-> LangChain agent
-> tool calls as needed
-> final AI message
-> extracted final answer
```

## Techniques Practiced

- `ChatOpenAI`
- LangChain `create_agent`
- system prompt separation
- tool registration
- hardcoded demo data
- custom tools
- agent invocation
- final answer extraction
- modular project structure
- API connection error handling

## Important Architecture

```text
normalobjects_langchain.py
Compatibility entry point

src/complaint_handler/agent.py
Builds model, builds agent, invokes complaint handling

src/complaint_handler/prompts.py
Stores system prompt

src/complaint_handler/tools/
Tool functions exposed to the agent

src/complaint_handler/data/
Hardcoded demo data used by tools

src/complaint_handler/main.py
Demo runtime flow
```

## Important Code Patterns

### Build model

```python
def build_model() -> ChatOpenAI:
    return ChatOpenAI(model=MODEL_NAME, temperature=TEMPERATURE)
```

### Build agent

```python
def build_agent():
    return create_agent(
        model=build_model(),
        tools=TOOLS,
        system_prompt=SYSTEM_PROMPT,
    )
```

Why it matters:
- Model, tools, and prompt are assembled in one place.
- This is cleaner than mixing everything in the runtime script.

### Invoke agent

```python
result = build_agent().invoke(
    {"messages": [{"role": "user", "content": complaint}]}
)
```

### Extract final answer

```python
def extract_final_answer(result):
    messages = result.get("messages", [])

    for message in reversed(messages):
        if isinstance(message, AIMessage):
            return str(message.content)

    raise ValueError("Agent did not return an AI message.")
```

Why it matters:
- Agent results contain message history, not only a plain string.
- You need to know how to retrieve the final useful answer.

### Tool structure

```python
def check_hawkins_records(query):
    return "..."
```

Tool examples in the project:
- `check_hawkins_records`
- `gather_party_wisdom`
- `consult_demogorgon`
- `cast_interdimensional_spell`

## What Was Provided

You mentioned this lab code was provided. The main learning value is reading and understanding the architecture:

- how an agent is assembled
- how tools are separated
- how data feeds tools
- how prompts are separated
- how the final answer is extracted

## Extra Concepts From Lab Source

- flexible tool chaining
- LLM calls inside tools
- dynamic tool responses
- agent memory
- tool usage efficiency
- freeform vs structured agent design

## What I Practiced

- Navigating a LangChain project
- Understanding the agent loop
- Seeing how tools extend a model
- Recognizing the difference between demo data and production data
- Understanding modular agent design

## Links to Topic Notes

- [[../Frameworks/LangChain]]
- [[../Prompting/Dynamic Prompting]]
- [[../Engineering/Code Quality and Automation]]
- [[../APIs/OpenAI API]]

## What To Reuse Later

- Keep prompts in a separate file.
- Keep tools in a dedicated folder.
- Keep demo data separate from agent logic.
- Wrap agent creation in a function.
- Extract final answer explicitly from agent result messages.
- Handle API connection errors close to the model call.

## Improvement Ideas

- Add tests for each tool.
- Replace hardcoded data with files or a small database.
- Give tools structured return values.
- Add logging of tool calls.
- Add a configuration note for model and temperature.
- Add examples of expected complaint inputs and outputs.

## Key Takeaway

This is the most important current lab for LangChain. It shows the jump from notebook examples to a modular agent project with prompts, tools, data, and runtime logic separated.
