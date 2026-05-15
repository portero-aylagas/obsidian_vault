# STT

**Labs**
- `week-1/submodule-4-speech-recognition/stt.ipynb`
- `week-1/submodule-4-speech-recognition/transformer_audio.ipynb`
- `week-1/submodule-4-speech-recognition/speech_recognition_breaking_points.ipynb`
- `W1D5_compare_whisper_vs_google_STT`

## Main Techniques
- Audio recording
- Audio visualization
- Speech-to-text
- Prompt-assisted transcription
- Chunking long audio
- Timestamps
- Transformer-based audio inference
- Stress-testing recognition

## Example
### Recording audio
```python
audio = sd.rec(
    int(duration * sample_rate),
    samplerate=sample_rate,
    channels=1,
    dtype="float32"
)

sd.wait()
```

### Save audio to WAV
```python
wavfile.write("recording.wav", sample_rate, audio)
```

### Basic transcription
```python
transcript = client.audio.transcriptions.create(
    model="whisper-1",
    file=audio_file
)
```

### Context prompting
Use a prompt to help the model transcribe ambiguous words more accurately.

```python
transcript = client.audio.transcriptions.create(
    model="whisper-1",
    file=buffer,
    prompt="heteronyms, homographs, lead metal, wind turbine"
)
```

### Chunking long audio
- Record or load long audio
- Split it into smaller pieces
- Transcribe each piece separately

### Timestamps
- Request time information so transcription can be aligned with the audio

Example output idea:

```text
0.0s - 1.2s: Hello
1.2s - 2.4s: welcome to the bootcamp
```

### Breaking points analysis
- Compare normal speech
- Compare fast speech
- Compare noisy speech
- Measure word accuracy and exact matches

Example experiment structure:

```python
conditions = ["normal", "fast", "noisy"]

for condition in conditions:
    record_audio(condition=condition)
    transcribe_audio(filename, client)
```

### Transformer audio notebook
- Uses Hugging Face `datasets`
- Casts audio to the correct sampling rate
- Runs transformer-based audio processing

## What the Notebooks Teach

- Whisper can transcribe recorded audio
- Context prompts can improve difficult transcriptions
- Long audio may need chunking
- Recognition accuracy changes under noise, speed, and difficult phrases

## Key Idea
- Speech-to-text shows that AI systems are not only text-in/text-out.
- It also introduces error analysis under noisy and fast conditions.

## Progression
- Related to [[TTS]]
