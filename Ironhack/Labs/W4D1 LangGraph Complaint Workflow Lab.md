# W4D1 LangGraph Complaint Workflow Lab

**Source folder**
- `W4D1_LangGraph_NormalObjects_Creative_Complaint_Handler`

**Main files**
- `normalobjects/workflow.py`
- `normalobjects/state.py`
- `normalobjects/prompts.py`
- `normalobjects/data.py`
- `normalobjects/demo.py`
- `tests/`

**Lab type**
- Structured LangGraph workflow lab
- Main value: turn the earlier complaint handler idea into a predictable multi-step workflow

## What This Lab Teaches

This lab builds a NormalObjects complaint workflow with LangGraph.

Pipeline:

```text
complaint text
-> intake
-> validate
-> investigate
-> resolve
-> close
-> structured state result
```

Unlike the freeform LangChain complaint handler, this version makes the workflow path explicit and repeatable.

## Techniques Practiced

- `StateGraph`
- typed workflow state
- explicit nodes and edges
- LLM-backed classification
- metadata extraction
- missing-detail validation
- duplicate detection
- category-specific validation
- structured investigation records
- resolution protocols
- closure records
- unit tests around workflow rules

## Important Architecture

```text
normalobjects/state.py
Defines the shared ComplaintState passed through the graph

normalobjects/workflow.py
Defines node functions, graph edges, workflow compilation, and process_complaint

normalobjects/prompts.py
Stores strict JSON prompts for classification, investigation, resolution, and closure

normalobjects/data.py
Contains demo complaint records and Downside Up protocols

tests/
Checks date parsing, validation rules, resolution rules, and full graph execution with a mocked LLM
```

## Important Code Patterns

### Build graph

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
```

### Programmatic entry point

```python
def process_complaint(complaint: str) -> ComplaintState:
    return app.invoke({"complaint": complaint})
```

### Workflow path tracking

```python
"workflow_path": state.get("workflow_path", []) + ["intake"]
```

This makes the executed path visible in the final result.

## What Was Provided

- A complaint-handling scenario with a staged workflow expectation.
- LangGraph-style structure for intake, validation, investigation, resolution, and closure.
- Lab guidance around controlled workflows, retries, and human review points.

## Extra Concepts From Lab Source

- parallel workflow branches
- workflow step retry logic
- human-in-the-loop approval
- workflow state persistence
- LangChain vs LangGraph tradeoffs

## What I Practiced

- Designing a workflow as named stages
- Keeping state explicit across steps
- Combining deterministic rules with LLM outputs
- Validating structured LLM responses
- Testing workflow rules without relying on live model calls
- Comparing flexible agents with controlled workflow orchestration

## Improvement Ideas

- Persist workflow state so interrupted cases can resume.
- Add a human approval node for high-risk complaints.
- Add retry policy per node instead of one global behavior.

## Links to Topic Notes

- [[../Frameworks/LangGraph]]
- [[../Frameworks/LangChain]]
- [[../Engineering/Code Quality and Automation]]
- [[W3D3 LangChain Complaint Handler Lab]]

## What To Reuse Later

- Use typed state for multi-step AI workflows.
- Track `workflow_path` for debugging and review.
- Keep prompts outside orchestration logic.
- Test business rules with mocked model outputs.
- Use LangGraph when the process has required stages.

## Key Takeaway

LangGraph is the right fit when the AI system needs a predictable process. The model helps inside each stage, but the graph controls the workflow.
