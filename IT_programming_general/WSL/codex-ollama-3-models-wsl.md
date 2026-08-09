# Local Codex Models with Ollama on WSL2 Ubuntu 24.04

**Target setup**

- Windows 11
- WSL2
- Ubuntu 24.04
- VS Code connected to WSL
- NVIDIA RTX 5080 16 GB
- Ollama running inside WSL
- Codex CLI installed inside WSL

The three local models used in this setup are:

```text
qwen35-codex
gptoss-codex
qwen3coder-codex
```

They are based on:

```text
qwen3.5:9b
gpt-oss:20b
qwen3-coder:30b
```

---

# 1. Verify the NVIDIA GPU inside WSL

Run:

```bash
nvidia-smi
```

You should see the RTX 5080.

Do not install a separate Linux NVIDIA display driver inside WSL.

---

# 2. Install Ollama inside WSL

Run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Enable and start the Ollama service:

```bash
sudo systemctl enable --now ollama
```

Verify:

```bash
ollama --version
```

Test the local API:

```bash
curl http://localhost:11434/api/tags
```

---

# 3. Download the three base models

Run:

```bash
ollama pull qwen3.5:9b
```

```bash
ollama pull gpt-oss:20b
```

```bash
ollama pull qwen3-coder:30b
```

Check:

```bash
ollama list
```

You should see:

```text
qwen3.5:9b
gpt-oss:20b
qwen3-coder:30b
```

---

# 4. Create a directory for Ollama Modelfiles

Run:

```bash
mkdir -p ~/.ollama/modelfiles
```

---

# 5. Create the Qwen3.5 Codex model

Create the Modelfile:

```bash
cat > ~/.ollama/modelfiles/qwen35-codex <<'EOF'
FROM qwen3.5:9b
PARAMETER num_ctx 65536
EOF
```

Create the Ollama alias:

```bash
ollama create qwen35-codex -f ~/.ollama/modelfiles/qwen35-codex
```

This is the recommended default local model.

---

# 6. Create the GPT-OSS Codex model

Create the Modelfile:

```bash
cat > ~/.ollama/modelfiles/gptoss-codex <<'EOF'
FROM gpt-oss:20b
PARAMETER num_ctx 65536
EOF
```

Create the Ollama alias:

```bash
ollama create gptoss-codex -f ~/.ollama/modelfiles/gptoss-codex
```

Use this when Qwen3.5 is not reasoning well enough.

---

# 7. Create the Qwen3-Coder Codex model

Create the Modelfile:

```bash
cat > ~/.ollama/modelfiles/qwen3coder-codex <<'EOF'
FROM qwen3-coder:30b
PARAMETER num_ctx 65536
EOF
```

Create the Ollama alias:

```bash
ollama create qwen3coder-codex -f ~/.ollama/modelfiles/qwen3coder-codex
```

This is the heavy local coding model.

Because the model is larger than 16 GB VRAM, expect some CPU/system-RAM offload.

---

# 8. Verify the final model list

Run:

```bash
ollama list
```

The important entries should be:

```text
qwen35-codex
gptoss-codex
qwen3coder-codex

qwen3.5:9b
gpt-oss:20b
qwen3-coder:30b
```

The aliases reuse the base-model data; they do not duplicate all model weights.

---

# 9. Test each model directly in Ollama

## Qwen3.5

```bash
ollama run qwen35-codex
```

## GPT-OSS

```bash
ollama run gptoss-codex
```

## Qwen3-Coder

```bash
ollama run qwen3coder-codex
```

While a model is generating, check GPU placement:

```bash
ollama ps
```

Also monitor the GPU:

```bash
watch -n 1 nvidia-smi
```

For Qwen3.5, the preferred result is:

```text
PROCESSOR    100% GPU
CONTEXT      65536
```

For Qwen3-Coder, partial CPU/RAM offload is expected.

---

# 10. Run the local models through Codex

From the VS Code WSL terminal or any WSL terminal inside your repository:

## Qwen3.5 — default local Codex

```bash
codex --oss --local-provider ollama -m qwen35-codex
```

## GPT-OSS — stronger local reasoning

```bash
codex --oss --local-provider ollama -m gptoss-codex
```

## Qwen3-Coder — heavy local coding

```bash
codex --oss --local-provider ollama -m qwen3coder-codex
```

Your normal cloud Codex remains:

```bash
codex
```

Inside normal cloud Codex, use:

```text
/model
```

to choose among the cloud models available to your ChatGPT subscription.

---

# 11. Optional shell aliases

Add these lines to:

```text
~/.bashrc
```

```bash
alias cx='codex'
alias cxlocal='codex --oss --local-provider ollama -m qwen35-codex'
alias cxoss='codex --oss --local-provider ollama -m gptoss-codex'
alias cxheavy='codex --oss --local-provider ollama -m qwen3coder-codex'
```

Reload Bash:

```bash
source ~/.bashrc
```

Then use:

```bash
cx
```

for normal cloud Codex.

```bash
cxlocal
```

for Qwen3.5.

```bash
cxoss
```

for GPT-OSS.

```bash
cxheavy
```

for Qwen3-Coder.

---

# 12. Recommended usage

Use this order:

```text
1. qwen35-codex
   Default local model.
   Fastest and best fit for the RTX 5080 16 GB.

2. gptoss-codex
   Use when you need stronger reasoning.

3. qwen3coder-codex
   Use for heavier coding tasks.
   Expect slower performance because it exceeds 16 GB VRAM.

4. Normal cloud Codex
   Use when the local models are not sufficient.
```

---

# 13. Useful commands

List installed models:

```bash
ollama list
```

See loaded models and GPU/CPU placement:

```bash
ollama ps
```

Check GPU:

```bash
nvidia-smi
```

Monitor GPU continuously:

```bash
watch -n 1 nvidia-smi
```

Check Ollama:

```bash
systemctl status ollama --no-pager
```

Restart Ollama:

```bash
sudo systemctl restart ollama
```

Check disk usage:

```bash
sudo du -sh /usr/share/ollama/.ollama/models
```

---

# 14. Final configuration

```text
Windows 11
└── WSL2 Ubuntu 24.04
    ├── VS Code
    ├── Codex CLI
    ├── Ollama
    │   ├── qwen35-codex       ← default
    │   ├── gptoss-codex       ← stronger reasoning
    │   └── qwen3coder-codex   ← heavy coding
    │
    └── RTX 5080 16 GB
```

Normal cloud Codex:

```bash
codex
```

Default local Codex:

```bash
codex --oss --local-provider ollama -m qwen35-codex
```
