# W4D3 n8n Multi-App Integration Lab

**Source folder**
- `W4D3_n8n_multiapp_integration`

**Main files**
- `workflow/Telegram_and_airtable.json`
- `screenshots/n8n_workflow.png`
- `screenshots/airtable_rows_telegram_messages.png`
- `lab_summary.md`
- `README.md`

**Lab type**
- n8n multi-app integration lab
- Main value: move real app data from a chat trigger into a structured table

## What This Lab Teaches

This lab builds a simple support intake workflow.

Pipeline:

```text
Telegram Trigger
-> Edit Fields / Set
-> Airtable Create Record
```

The workflow receives Telegram bot messages, normalizes the nested message data, and creates Airtable records for review.

## Extra Concepts From Lab Source

- source-transform-sink workflow design
- field normalization
- event filtering
- credential isolation
- deduplication with cache or lookup checks
- parallel enrichment
- rate-limit-aware branching
- AI summarization before storage

## Techniques Practiced

- Telegram Trigger configuration
- field normalization with Edit Fields / Set
- nested JSON field access
- Airtable record creation
- timestamp mapping
- fallback sender mapping
- workflow export
- screenshot-based proof of execution

## Important Architecture

```text
Telegram event -> field normalization -> Airtable record -> execution evidence
```

## Important Code Patterns

```text
Message ID
<- message.message_id

Timestamp
<- $now

Sender
<- message.from.username or message.from.first_name

Chat ID
<- message.chat.id

Message Text
<- message.text
```

## What Was Provided

- A Telegram-to-Airtable workflow task with expected proof of execution.
- Workflow-export and screenshot requirements.
- Lab guidance around source-transform-sink automation and credential handling.

## What I Practiced

- Connecting two external apps without writing a full application
- Turning nested Telegram payloads into flat database fields
- Using n8n expressions correctly
- Verifying that the destination app received the expected rows

## Links to Topic Notes

- [[../n8n/n8n Workflows]]
- [[../APIs/OpenAI API]]
- [[W4D2 n8n Node Study Guide Lab]]

## What To Reuse Later

- Normalize external app payloads before writing them to a database.
- Keep field names clear and stable in the destination table.
- Add an IF node when empty messages or commands should be ignored.
- Use screenshots and exported JSON as proof of workflow behavior.

## Improvement Ideas

- Add an IF node to filter commands, empty messages, or malformed payloads.
- Add deduplication using message IDs before writing to Airtable.
- Add rate-limit-aware handling if enrichment or AI summarization is added.

## Key Takeaway

n8n is useful for small operational workflows where data from one app needs to become structured records in another app.
