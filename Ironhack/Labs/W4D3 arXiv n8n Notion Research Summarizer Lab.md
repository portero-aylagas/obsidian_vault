# W4D3 arXiv n8n Notion Research Summarizer Lab

**Source folder**
- `W4D3_arxiv_research_summarizer_n8n_notion`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- guided low-code integration lab
- Main value: learn the webhook-to-API-to-AI-to-database automation pattern for research workflows

## What This Lab Teaches

This lab builds a personal research intake pipeline:

```text
arXiv URL
-> webhook
-> paper ID extraction
-> arXiv API
-> XML parsing
-> AI summary
-> Notion database record
```

The transferable idea is not Notion specifically. It is the pattern of receiving an event, enriching it through an external API, applying AI, and storing structured output.

## Techniques Practiced

- webhook input handling
- URL parsing
- API request construction
- XML response parsing
- AI summarization
- database field mapping
- Notion integration
- structured response confirmation
- low-code workflow orchestration

## Important Architecture

```text
Webhook
-> Set / Function node
-> HTTP Request to arXiv
-> XML parsing
-> OpenAI summarization
-> Notion create page
-> Respond to webhook
```

The workflow has a clean source-transform-enrich-store shape.

## Important Code Patterns

### arXiv API request shape

```text
https://arxiv.org/api/query?id_list={{ paper_id }}&start=0&max_results=1
```

### Webhook payload shape

```json
{
  "arxiv_url": "https://arxiv.org/abs/2301.12345"
}
```

## What Was Provided

The lab source provides the workflow design, Notion schema, node sequence, and improvement ideas. The workspace currently contains the HTML source but no exported n8n workflow or screenshots for this extra lab.

## What I Practiced

- designing a multi-service automation
- turning a URL into API-ready metadata
- parsing non-JSON API responses
- using AI as an enrichment step
- mapping extracted fields into a database schema

## Links to Topic Notes

- [[../n8n/n8n Workflows]]
- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Validate incoming webhook payloads before calling downstream APIs.
- Keep parsing and summarization as separate workflow stages.
- Map destination database fields explicitly.
- Return a confirmation payload so the caller knows what happened.
- Handle external API and parsing failures as first-class cases.

## Improvement Ideas

- Add invalid-URL and arXiv API error handling.
- Support batch processing for multiple papers.
- Add AI-based auto-categorization and tagging.
- Add weekly digest notifications.
- Store paper PDFs or canonical links with the Notion record.

## Key Takeaway

The lab is a reusable integration pattern: webhook intake, external metadata lookup, AI enrichment, structured storage, and confirmation.
