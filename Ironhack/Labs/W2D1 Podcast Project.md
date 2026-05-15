# W2D1 Podcast Project

**Source folder**
- `W2D1_project1_podcast`

**Main files**
- `src/main.py`
- `src/data_processor.py`
- `src/llm_processor.py`
- `src/tts_generator.py`
- `src/config.py`
- `Post-project-review-stakeholder.md`

**Lab type**
- Team day project
- End-to-end AI app
- Main value: connect multiple AI and non-AI steps into a usable workflow

## What This Lab Teaches

This project turns source material into a generated podcast.

Pipeline:

```text
PDF / URL / text input
-> source extraction
-> combined source text
-> summary
-> two-speaker podcast script
-> TTS clips
-> merged MP3
-> transcript export
```

## Techniques Practiced

- Gradio UI
- file upload
- URL validation
- text input handling
- PDF parsing with `pypdf`
- webpage parsing with `requests` and `BeautifulSoup`
- OpenAI summarization
- podcast script generation
- speaker-tag parsing
- OpenAI TTS
- audio merging with `pydub`
- transcript export
- step-by-step pipeline logging

## Important Architecture

### Module responsibilities

```text
src/main.py
UI, validation, pipeline orchestration

src/data_processor.py
PDF/URL/text loading, source combination, summarization

src/llm_processor.py
Podcast script generation

src/tts_generator.py
Speaker parsing, TTS generation, audio merging

src/config.py
Shared OpenAI client/config
```

This separation is important. The project is much easier to understand because UI, data processing, LLM generation, and audio generation are separated.

## Important Code Patterns

### Source combination

```python
def combine_sources(source_info):
    sections = []

    if source_info.get("text_path"):
        sections.append("--- SOURCE: TEXT ---")

    if source_info.get("pdf_path"):
        sections.append("--- SOURCE: PDF ---")

    if source_info.get("url"):
        sections.append("--- SOURCE: URL ---")

    return "\n\n".join(sections)
```

Why it matters:
- Multiple source types are normalized into one text block.
- This is similar to context assembly in RAG-style systems.

### Summarization prompt

```python
prompt = f"""
You are preparing source material for a two-person podcast conversation.

Every source must be used.
Preserve concrete examples and unique details.

Target audience: {target_audience}

Source material:
{text}
"""
```

Why it matters:
- The prompt explicitly protects against dropping shorter or less detailed sources.
- This is a good example of prompt constraints based on product requirements.

### Script parsing

```python
match = re.match(r"\[(.*?)\]:\s*(.*)", line.strip())
```

Why it matters:
- The TTS step depends on the LLM following a predictable format.
- This is a case where structured output would make the system more robust.

### Speaker-to-voice mapping

```python
VOICE_MAP = {
    "Speaker1": "alloy",
    "Speaker2": "nova",
}
```

### Audio merging

```python
pause = AudioSegment.silent(duration=500)
combined = AudioSegment.empty()

for file in files:
    combined += AudioSegment.from_file(file)
    combined += pause
```

## What Was Provided

The project appears to be a team MVP:

- Gradio interface
- input pipeline for PDF, URL, and text
- summarization stage
- podcast script stage
- TTS stage
- final audio output
- transcript output

## Extra Concepts From Lab Source

- multi-source ingestion
- LLM content transformation
- source-to-audio automation pipelines
- audience adaptation
- content summarization and restructuring
- text-to-speech generation
- MVP scope control
- API cost awareness

## What I Practiced

- Thinking in full pipelines instead of isolated prompts
- Turning different input types into one common format
- Chaining LLM tasks
- Connecting text generation to audio generation
- Handling UI state and output files

## Links to Topic Notes

- [[../Speech/TTS]]
- [[../APIs/OpenAI API]]
- [[../Prompting/Dynamic Prompting]]
- [[../Engineering/Code Quality and Automation]]
- [[../RAG/RAG Basics]]

## What To Reuse Later

- Keep UI orchestration separate from processing modules.
- Normalize different input types into a common internal format.
- Save generated outputs as files for reuse and debugging.
- Use speaker tags or schemas when generating dialogue.

## Improvement Ideas

- Validate the generated script before sending it to TTS.
- Use structured output for speaker turns instead of regex parsing.
- Add retry/error handling around API calls.
- Add tests for `parse_script`, URL validation, and source combination.
- Add fallback behavior if one source fails.

## Key Takeaway

This project is your first strong example of an end-to-end AI workflow. It combines ingestion, summarization, generation, TTS, and UI into one app.
