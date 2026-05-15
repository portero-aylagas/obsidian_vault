# W1D5 Whisper STT Evaluation Lab

**Source folder**
- `W1D5_compare_whisper_vs_google_STT`

**Main files**
- `lab_source/Ironhack Student Portal.html`

**Lab type**
- open-ended evaluation lab
- Main value: learn how to evaluate an AI speech service before deciding whether it is good enough to deploy

## What This Lab Teaches

This lab is about evaluation, not just transcription.

```text
audio sample
-> Whisper transcription
-> human ground truth
-> WER calculation
-> cost analysis
-> deployment recommendation
```

The central concept is that an AI API should be measured against real use cases before adoption.

## Techniques Practiced

- audio recording for test data
- Whisper API transcription
- human-verified ground truth creation
- Word Error Rate calculation
- substitution / insertion / deletion analysis
- cost estimation
- paired comparison across speakers or samples
- evidence-based service recommendation

## Important Architecture

```text
audio file
-> STT provider
-> raw transcript
-> manual correction
-> metric calculation
-> report
```

The human transcript is the evaluation anchor. Without it, the model output can look plausible but still be wrong.

## Important Code Patterns

### WER evaluation shape

```python
wer = jiwer.wer(reference_transcript, model_transcript)
```

### Cost estimate shape

```python
estimated_cost = audio_minutes * price_per_minute
```

## What Was Provided

The lab source provides the evaluation workflow, report expectations, and suggested metric. The workspace currently contains the HTML source but no submitted evaluation script, audio files, or report.

## What I Practiced

- treating transcription as measurable output
- separating model transcript from ground truth
- using WER as a quality metric
- connecting accuracy to deployment decisions
- estimating API cost for scale

## Links to Topic Notes

- [[../Speech/STT]]
- [[../APIs/OpenAI API]]
- [[../Engineering/Code Quality and Automation]]

## What To Reuse Later

- Always create a trusted reference before judging STT quality.
- Evaluate across voices, accents, recording conditions, and speaking styles.
- Pair quality metrics with cost metrics before recommending a provider.
- Use error categories to understand what kind of mistakes the model makes.

## Improvement Ideas

- Compare Whisper with another STT provider on the same clips.
- Track WER by audio condition.
- Add speaker-level or segment-level metrics.
- Include latency and retry behavior in the provider comparison.

## Key Takeaway

The lab turns STT from a demo into an evaluation problem: good AI engineering means measuring accuracy, cost, and failure modes before scaling.
