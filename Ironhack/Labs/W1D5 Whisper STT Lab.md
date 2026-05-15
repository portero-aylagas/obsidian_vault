# W1D5 Whisper STT Lab

**Source folder**
- `W1D5_whisper_STT_implementation`

**Main files**
- `whisper_STT_implementation.ipynb`
- `whisper_STT_implementation.py`
- `conclusions.md`

**Lab type**
- Provided-code / template-heavy speech lab
- Main value: understand a complete STT workflow with prompts, chunking, and timestamps

## What This Lab Teaches

This lab shows how to transcribe audio with Whisper and improve reliability.

Pipeline:

```text
load audio -> transcribe short sample -> transcribe with prompt -> transcribe without prompt -> chunk audio -> transcribe chunks -> export timestamps
```

## Techniques Practiced

- OpenAI audio transcription
- audio loading with `pydub`
- converting audio to in-memory buffers
- prompted transcription
- unprompted transcription comparison
- audio chunking
- timestamp handling
- SRT-style timestamp formatting

## Important Architecture

```text
audio file -> optional chunking -> transcription call -> timestamp formatting -> transcript output
```

## Important Code Patterns

### Export audio segment to buffer

```python
def export_to_buffer(audio_segment, format="mp3"):
    buffer = io.BytesIO()
    audio_segment.export(buffer, format=format)
    buffer.seek(0)
    buffer.name = f"audio.{format}"
    return buffer
```

Why it matters:
- APIs usually need file-like objects.
- Buffers let you send generated or sliced audio without writing every piece manually to disk.

### Basic transcription

```python
transcript = client.audio.transcriptions.create(
    model="whisper-1",
    file=buffer
)

print(transcript.text)
```

### Prompted transcription

```python
prompt = """
This is an interview transcript about a Hawaiian fishing custom called hukilau.
Important vocabulary and spellings: Cassidy, hukilau.
"""

transcript = client.audio.transcriptions.create(
    model="whisper-1",
    file=buffer,
    prompt=prompt
)
```

Why it matters:
- A transcription prompt is not a normal chat prompt.
- It gives vocabulary and context to improve difficult words.

### Chunking idea

```python
chunk_length_ms = 10_000
chunks = [
    audio[i:i + chunk_length_ms]
    for i in range(0, len(audio), chunk_length_ms)
]
```

### Timestamp formatting

```python
def format_srt_time(seconds):
    hours = int(seconds // 3600)
    minutes = int((seconds % 3600) // 60)
    secs = int(seconds % 60)
    millis = int((seconds - int(seconds)) * 1000)
    return f"{hours:02}:{minutes:02}:{secs:02},{millis:03}"
```

## What Was Provided

The lab appears to provide most of the workflow code. Your main learning value is reading, running, comparing, and understanding why each step exists.

## What I Practiced

- Comparing prompted vs unprompted STT
- Understanding why long audio needs chunking
- Handling offsets correctly for timestamps
- Seeing how audio quality affects transcription accuracy

## Links to Topic Notes

- [[../Speech/STT]]
- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Use context prompts for domain-specific vocabulary.
- Chunk long audio to improve stability.
- Preserve chunk offsets when producing timestamps.
- Keep buffer/export helpers separate from transcription logic.

## Improvement Ideas

- Add word error rate evaluation against reference transcripts.
- Track latency and cost per audio minute.
- Compare prompted and unprompted transcription on repeated samples.

## Key Takeaway

The important learning is not only "Whisper transcribes audio." The useful engineering pattern is: prepare audio carefully, provide context when needed, chunk long inputs, and export results in a usable format.
