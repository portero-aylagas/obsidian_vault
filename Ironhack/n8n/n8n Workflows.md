# n8n Workflows

**Labs**
- `W4D2_n8n_node`
- `W4D3_arxiv_n8n_notion_research_summarizer`
- `W4D3_n8n_multiapp_integration`
- `W4D4_n8n_error_handling_and_scheduled_workflows`

## Main Techniques
- Trigger nodes
- AI model nodes
- Agent nodes
- Memory nodes
- Code nodes
- Split Out
- Edit Fields / Set
- HTTP Request
- App nodes
- JSON inspection and reshaping
- Error workflows
- Retry behavior
- Schedule triggers
- Idempotency guards

## Core Workflow Shape
n8n workflows move structured JSON items from node to node.

```text
trigger
-> transform or enrich JSON
-> call model or API
-> write to an app/database
```

## Example Patterns

### Chat agent workflow

```text
When chat message received
-> AI Agent
-> Anthropic Chat Model
-> Simple Memory
```

This pattern is useful when the workflow starts from a chat interface and needs session context.

### Scheduled AI content workflow

```text
Schedule Trigger or Manual Trigger
-> Message a model
-> Code / Format Blocks
-> Split Out
-> Notion Create Page
-> HTTP Request
```

This pattern is useful when an AI model produces structured content that must be transformed before sending it to another app.

### Multi-app intake workflow

```text
Telegram Trigger
-> Edit Fields / Set
-> Airtable Create Record
```

### Operational workflow hardening

```text
Schedule Trigger or scenario input
-> HTTP Request or summary step
-> retry / failure handling
-> duplicate guard
-> final write or skip
```

This pattern is useful when a message from one app should become a structured record in another app.

## Important Debugging Habit
Inspect the input and output JSON after every node.

Most n8n mistakes come from assuming a field exists directly on `$json` when it is actually nested or was changed by a previous node.

## Common Node Roles

- Trigger nodes start execution.
- AI model nodes generate or classify content.
- Code nodes reshape JSON when visual mapping is not enough.
- Split Out turns arrays into one item per array element.
- Edit Fields / Set normalizes nested data into flat fields.
- HTTP Request handles API operations not covered by a dedicated app node.
- App nodes write to tools such as Notion, Airtable, or Sheets.

## Key Idea
- n8n is a low-code orchestration layer.
- The engineering skill is understanding the JSON contract between nodes.

## Progression
- Extends [[Code Quality and Automation]]
- Related to [[../APIs/OpenAI API]]
- Applied in [[../Labs/W4D2 n8n Node Study Guide Lab]]
- Applied in [[../Labs/W4D3 arXiv n8n Notion Research Summarizer Lab]]
- Applied in [[../Labs/W4D3 n8n Multi-App Integration Lab]]
- Applied in [[../Labs/W4D4 n8n Error Handling and Scheduled Workflows Lab]]
