# LangGraph

**Labs**
- `week-4/langgraph.ipynb`
- `week-4/langgraph_integration.ipynb`
- `W4D1_LangGraph_NormalObjects_Creative_Complaint_Handler`

## Main Techniques
- State graph workflows
- Typed workflow state
- Explicit nodes and edges
- Deterministic step order
- Conditional business rules
- Structured LLM outputs
- Workflow path tracking
- Testable orchestration

## Core Idea
LangGraph is useful when an AI workflow should follow a known sequence instead of letting an agent choose every next step.

A LangChain agent is flexible:

```text
model decides
-> tool call
-> model decides again
-> final answer
```

A LangGraph workflow is explicit:

```text
intake
-> validate
-> investigate
-> resolve
-> close
```

## Example Pattern

### Typed state
The workflow passes one state object through every node.

```python
class ComplaintState(TypedDict, total=False):
    complaint: str
    category: str
    status: str
    investigation: dict[str, Any]
    resolution: dict[str, Any]
    workflow_path: list[str]
```

### Build the graph
Each node receives state and returns updated state.

```python
workflow = StateGraph(ComplaintState)
workflow.add_node("intake", intake_node)
workflow.add_node("validate", validate_node)
workflow.add_node("investigate", investigate_node)
workflow.add_node("resolve", resolve_node)
workflow.add_node("close", close_node)

workflow.set_entry_point("intake")
workflow.add_edge("intake", "validate")
workflow.add_edge("validate", "investigate")
workflow.add_edge("investigate", "resolve")
workflow.add_edge("resolve", "close")
workflow.add_edge("close", END)

app = workflow.compile()
```

### Run the workflow

```python
result = app.invoke({
    "complaint": "The Downside Up portal opened three hours late."
})
```

## What LangGraph Adds

- predictable execution order
- inspectable intermediate state
- a clear place for validation rules
- easier testing of each workflow step
- less hidden behavior than a freeform agent loop

## When To Use It

- The process has required stages.
- Each stage needs structured output.
- Business rules decide whether work continues, blocks, or escalates.
- You need traceability for debugging or review.

## LangChain vs LangGraph

Use LangChain agents when exploration and flexible tool choice matter.

Use LangGraph when correctness, traceability, and consistent order matter more.

## Key Idea
- LangGraph turns an AI system into an explicit state machine.
- The model can still be used inside nodes, but the workflow owns the sequence.

## Progression
- Builds on [[Ironhack/Frameworks/LangChain]]
- Extends [[../Engineering/Code Quality and Automation]]
- Applied in [[../Labs/W4D1 LangGraph Complaint Workflow Lab]]
