# Create Permanent Environment Variable

Main reference: [[wsl_environment_variables]]

Quick pattern:

```bash
nano ~/.bashrc
```

Add one line near the bottom:

```bash
export NAME="value"
```

For example:

```bash
export OPENAI_API_KEY="your_api_key_here"
```

Save and exit:

```text
Ctrl + O
Enter
Ctrl + X
```

Reload:

```bash
source ~/.bashrc
```

Verify without printing the full value:

```bash
python -c "import os; print('set' if os.getenv('OPENAI_API_KEY') else 'missing')"
```
