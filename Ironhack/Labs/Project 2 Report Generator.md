# Project 2 Report Generator

**Source folder**
- `project2_content_creation/project2_content_creation`

**Main files**
- `src/main.py`
- `src/content_pipeline.py`
- `src/document_processor.py`
- `src/knowledge_base.py`
- `src/prompt_templates.py`
- `src/llm_integration.py`
- `templates/prompt_generation.json`
- `knowledge_base/`
- `tests/`

**Project type**
- Team day project
- End-to-end content generation app
- Main value: strongest current example of dynamic prompting, knowledge-base context assembly, feedback iteration, and code quality

## What This Lab Teaches

This project generates market intelligence reports from a markdown knowledge base.

Pipeline:

```text
UI request
-> selected month/year/markets/sections/style/audience/depth
-> load markdown knowledge base
-> assemble relevant context
-> build prompt from template
-> call OpenAI
-> return report, metadata, tokens, cost
-> optionally apply feedback and regenerate
```

## Techniques Practiced

- Gradio UI
- markdown knowledge-base loading
- nested heading parsing
- section filtering
- market filtering
- date/period filtering
- dynamic prompt construction
- prompt templates from JSON
- style control
- audience control
- report-depth control
- OpenAI model discovery
- model categorization
- generation wrapper
- token/cost tracking
- feedback iteration
- report download
- unit testing

## Important Architecture

```text
src/main.py
Gradio UI, request construction, feedback request construction, downloads

src/content_pipeline.py
Pipeline orchestration for generation and feedback iteration

src/document_processor.py
Loads and parses markdown knowledge-base files

src/knowledge_base.py
Filters and assembles context by section, date, and market

src/prompt_templates.py
Loads prompt templates and formats generation/feedback prompts

src/llm_integration.py
OpenAI client, model discovery, generation, usage/cost tracking

templates/prompt_generation.json
Prompt templates

knowledge_base/
Primary and secondary market intelligence markdown files

tests/
Unit tests for document processing, KB filtering, and prompt templates
```

## Important Code Patterns

### Build UI request

```python
def build_report_request(
    year,
    month_name,
    markets,
    sections,
    report_depth,
    audience,
    style,
    selected_model,
    temperature,
):
    return {
        "month": month_name,
        "year": year,
        "report_period": f"{month_name} {year}",
        "markets": markets,
        "sections": sections,
        "report_depth": report_depth,
        "audience": audience,
        "style": style,
        "model": selected_model,
        "temperature": temperature,
    }
```

Why it matters:
- UI values are normalized into one request object.
- This makes the pipeline easier to test and debug.

### Validate required request fields

```python
required_fields = ("month", "year", "report_period", "markets", "sections")
missing_fields = [
    field for field in required_fields if field not in report_request
]
```

Why it matters:
- The pipeline checks its inputs before doing expensive LLM work.

### Convert UI labels to knowledge-base keys

```python
kb_markets = [
    MARKET_NAME_MAP.get(market_code, market_code)
    for market_code in normalized_request["markets"]
]
```

Why it matters:
- UI values and internal data keys do not always match.
- This mapping keeps the UI user-friendly while preserving internal structure.

### Context assembly

```python
combined_context = get_section_context(
    kb_data,
    kb_sections,
    kb_period,
    kb_markets,
)
```

Why it matters:
- This is not vector RAG.
- It is structured context assembly from a controlled knowledge base.
- For this project, that is a sensible design because the data is organized by month, market, and section.

### Prompt template loading

```python
def load_template(prompt_key):
    template_path = TEMPLATES_DIR / "prompt_generation.json"

    with open(template_path, "r", encoding="utf-8") as f:
        data = json.load(f)

    return data[prompt_key]
```

### Prompt formatting

```python
prompt = template.format(
    combined_context=combined_context,
    style_desc=style_desc,
    audience=audience,
    length_instruction=length_instruction,
)
```

Why it matters:
- Prompt templates keep long prompts out of core business logic.
- This makes prompts easier to edit, compare, and reuse.

### Generate text wrapper

```python
response = _get_client().chat.completions.create(
    model=model,
    messages=[
        {
            "role": "system",
            "content": "You generate high-quality, non-generic business content."
        },
        {"role": "user", "content": prompt_obj["prompt"]}
    ],
    max_tokens=prompt_obj.get("max_tokens", 16000),
    temperature=final_temperature
)
```

### Feedback iteration

```python
feedback_prompt_payload = build_feedback_prompt(
    {
        "original_prompt": original_prompt,
        "generated_content": original_report_text,
        "general_feedback": general_feedback,
        "section_feedback": section_feedback,
        "report_depth": report_depth,
        "audience": audience,
        "style": style,
    }
)
```

Why it matters:
- Feedback iteration is a practical dynamic prompting pattern.
- The model receives the original prompt, previous output, and new feedback.

## What Was Provided

This project is more mature than most day labs. It includes:

- a UI
- a content pipeline
- a markdown knowledge base
- prompt templates
- OpenAI integration
- model selection
- feedback iteration
- usage/cost metadata
- tests

## Extra Concepts From Lab Source

- knowledge-base context injection
- primary vs secondary knowledge bases
- brand-aligned generation
- content uniqueness evaluation
- side-by-side baseline comparison
- human-in-the-loop review
- style variation
- contextual placement
- iterative prompt engineering
- content lifecycle pipelines
- trend monitoring and content gap analysis
- vector store/RAG as optional escalation
- API cost and rate-limit risk management

## What I Practiced

- Designing an AI workflow around structured context
- Separating UI from pipeline logic
- Building prompts from metadata
- Using templates instead of hardcoded prompts
- Tracking LLM cost and token usage
- Adding a revision loop
- Testing non-LLM logic

## Links to Topic Notes

- [[../Prompting/Dynamic Prompting]]
- [[../RAG/RAG Basics]]
- [[../Engineering/Code Quality and Automation]]
- [[../APIs/OpenAI API]]
- [[../APIs/Multi-Provider]]

## What To Reuse Later

- Use a single request object between UI and pipeline.
- Keep prompt templates outside Python logic.
- Build context deterministically when the knowledge base is structured.
- Test document parsing and prompt building without calling the LLM.
- Return metadata with generated output: model, temperature, tokens, cost.
- Keep feedback iteration as a separate pipeline step.

## Important Distinction

This project is related to RAG, but it is not classic vector RAG.

Classic vector RAG:

```text
query -> embeddings -> vector search -> retrieved chunks -> prompt
```

This project:

```text
selected filters -> structured markdown knowledge base -> assembled context -> prompt
```

That is still retrieval-like context assembly, but it is deterministic and structured rather than embedding-based.

## Improvement Ideas

- Add evaluation examples for generated reports.
- Add tests for failed LLM responses.
- Add structured response validation for report metadata.
- Add persistent storage for generated reports.
- Add LangSmith tracing later when evaluation/tracing is introduced.
- Add stricter source citation handling if reports need traceability.

## Key Takeaway

This is currently the best example of a real AI application in your folder. It combines dynamic prompting, context assembly, modular code, UI, feedback loops, cost tracking, and tests.
