# Environment Variables in WSL

Use this for Linux environment variables inside WSL. Windows environment variables are separate, so define the variable inside WSL when a WSL terminal, Python process, Jupyter kernel, or VS Code WSL session needs it.

## Cheat Sheet

| Need | Command / file |
|---|---|
| Set only in current terminal | `export NAME="value"` |
| Set every time WSL opens | Add `export NAME="value"` to `~/.bashrc` |
| Reload after editing | `source ~/.bashrc` |
| Remove from current terminal | `unset NAME` |
| Check without printing a secret | `python -c "import os; print('set' if os.getenv('NAME') else 'missing')"` |

For normal WSL terminal work, `~/.bashrc` is the usual place.

## Temporary Variable

This lasts only until the current terminal closes:

```bash
export OPENAI_API_KEY="your_api_key_here"
```

Check from Bash:

```bash
echo $OPENAI_API_KEY
```

Check from Python:

```bash
python -c "import os; print(os.getenv('OPENAI_API_KEY'))"
```

## Permanent Variable

Open your Bash config:

```bash
nano ~/.bashrc
```

Add variables near the bottom:

```bash
# API keys
export OPENAI_API_KEY="your_openai_key_here"
export ANTHROPIC_API_KEY="your_anthropic_key_here"
```

Save and exit nano:

```text
Ctrl + O
Enter
Ctrl + X
```

Reload:

```bash
source ~/.bashrc
```

New WSL terminals will load the value automatically.

## Add Without Nano

For non-secret values, you can append directly:

```bash
echo 'export MY_VARIABLE="my_value"' >> ~/.bashrc
source ~/.bashrc
```

For API keys, prefer `nano ~/.bashrc` so the full key is less likely to end up in shell history.

## Edit or Remove

Open the file:

```bash
nano ~/.bashrc
```

Search inside nano with `Ctrl + W`, then type the variable name, for example `OPENAI_API_KEY`.

To edit, change the line:

```bash
export OPENAI_API_KEY="new_key_here"
```

To remove, delete the line or comment it out:

```bash
# export OPENAI_API_KEY="old_key_here"
```

Then reload:

```bash
source ~/.bashrc
```

If the old value is still present in the current terminal:

```bash
unset OPENAI_API_KEY
```

## Safer Verification

Avoid printing a full API key if someone can see your screen.

Check whether it exists:

```bash
if [ -n "$OPENAI_API_KEY" ]; then echo "OPENAI_API_KEY is set"; else echo "OPENAI_API_KEY is missing"; fi
```

Check from Python:

```bash
python -c "import os; print('set' if os.getenv('OPENAI_API_KEY') else 'missing')"
```

Show only the first characters:

```bash
echo "${OPENAI_API_KEY:0:8}..."
```

## Current Shell vs New Processes

Environment variables are inherited by child processes. If you export a variable and then start Python, Python can see it:

```bash
export TEST_VAR="hello"
python -c "import os; print(os.getenv('TEST_VAR'))"
```

Already-running programs do not automatically receive new values. Restart the relevant process if needed:

- VS Code
- VS Code integrated terminal
- Jupyter kernel
- Python script
- Long-running server
- Codex/OpenClaw process

You usually do not need to restart WSL itself.

## `.bashrc` vs `.profile`

| File | Use |
|---|---|
| `~/.bashrc` | Interactive Bash terminals. Best default for normal WSL terminal sessions. |
| `~/.profile` | Login shells. Use only when you specifically need login-session setup. |

After editing either file, reload that file with `source ~/.bashrc` or `source ~/.profile`.

## Common Mistakes

| Mistake | Wrong | Correct / fix |
|---|---|---|
| Missing `export` | `OPENAI_API_KEY="key"` | `export OPENAI_API_KEY="key"` |
| Spaces around `=` | `export OPENAI_API_KEY = "key"` | `export OPENAI_API_KEY="key"` |
| Forgot to reload | Edit only | Run `source ~/.bashrc` or open a new terminal |
| Wrong user's file | Editing another home folder | Check with `whoami` and `echo $HOME` |
| Expecting Windows variables in WSL | Set only in Windows | Set it inside WSL too |
