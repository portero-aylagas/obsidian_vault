# W4D2 n8n Node Study Guide Lab

**Source folder**
- `W4D2_n8n_node`

**Main files**
- `node_reference_table.md`
- `lab_summary.md`
- `examples/`
- `screenshots/`
- `workflows/`
- `notes/`

**Lab type**
- n8n node analysis lab
- Main value: understand what common n8n nodes do and how JSON moves between them

## What This Lab Teaches

This lab analyzes two n8n workflows:

- an AI chat agent workflow
- an AI news-to-Notion workflow

Workflow shapes:

```text
When chat message received
-> AI Agent
-> Anthropic Chat Model
-> Simple Memory
```

```text
Schedule Trigger or Manual Trigger
-> Message a model
-> Format Blocks
-> Split Out
-> Create a page
-> HTTP Request
```

## Techniques Practiced

- trigger node inspection
- AI Agent node behavior
- chat model node configuration
- memory node role
- OpenAI Responses node output
- Code node JSON transformation
- Split Out array handling
- Notion page creation
- HTTP Request for app API calls
- credential-reference awareness

## Important Architecture

- Trigger nodes start a workflow.
- AI/model nodes generate structured content.
- Code nodes reshape model output into app-ready JSON.
- Split Out turns arrays into separate items.
- App nodes write structured data to external tools.
- HTTP Request covers API operations beyond the visual node.

## Important Code Patterns

- Treat each node output as the contract for the next node.
- Normalize model output before sending it to app/database nodes.
- Use Code nodes when expression mapping becomes too limited.
- Keep credential references in workflow exports without exposing secret values.

## What Was Provided

- Exported n8n workflows, screenshots, examples, and a node reference table.
- The `lab_source` HTML and the n8n artifacts now align, so this note reflects the actual W4D2 node study guide source.

## What I Practiced

- Reading exported n8n workflow JSON
- Identifying each node's input and output shape
- Tracking field transformations across nodes
- Understanding how credentials are referenced without exposing secret values
- Documenting node behavior in a reusable reference table

## Links to Topic Notes

- [[../n8n/n8n Workflows]]
- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Inspect JSON after every node.
- Use Code nodes when visual mapping is too limited.
- Use Split Out when an array needs to become item streams.
- Keep credential values out of exported examples.
- Record representative input/output JSON while debugging.

## Improvement Ideas

- Add before/after JSON examples for each important node.
- Document common expression failures and their fixes.
- Keep a small reusable checklist for exported workflow review.

## Key Takeaway

n8n workflows are easier to debug when you treat each node as a JSON transformation step.
