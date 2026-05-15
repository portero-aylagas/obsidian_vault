# TTS

**Labs**
- `week-1/submodule-4-speech-recognition/tts.ipynb`

## Main Techniques
- Offline TTS
- API-driven TTS
- Voice comparison
- External TTS provider example

## Example
### Offline TTS
```python
import pyttsx3

engine = pyttsx3.init()
engine.setProperty("rate", 150)
engine.say("Hello, welcome to the bootcamp.")
engine.runAndWait()
```

### OpenAI TTS
```python
audio = client.audio.speech.create(
    model="gpt-4o-mini-tts",
    voice="alloy",
    input="Hello, welcome to the bootcamp."
)
```

### Voice comparison
- Try different voices
- Compare style, clarity, and tone

Example loop:

```python
voices = ["alloy", "echo", "fable", "onyx", "nova", "shimmer"]

for voice in voices:
    audio = client.audio.speech.create(
        model="gpt-4o-mini-tts",
        voice=voice,
        input="This is a voice test."
    )
```

### External provider example
- The notebook also shows an ElevenLabs example for alternative voice generation

```python
audio = elevenlabs_client.text_to_speech.convert(
    voice_id="example_voice_id",
    text="Hello from ElevenLabs."
)
```

## What the Notebook Teaches

- Older TTS can run locally but is less expressive
- API TTS gives more natural voices
- Voice choice affects tone and user experience
- External providers can be swapped in for different voice quality

## Key Idea
- TTS complements STT and expands the course beyond text-only outputs.

## Progression
- Related to [[STT]]
