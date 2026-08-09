# Python `venv` Per-Repository Environment

## Standard Setup

### 1. Go to your project

```bash
cd ~/projects/your-repo
```

### 2. Install `venv` support on Ubuntu/WSL

On Ubuntu/WSL, Python can be installed without the package needed to create virtual environments.

For Python 3.12:

```bash
sudo apt update
sudo apt install python3.12-venv -y
```

If you are using the default system Python instead:

```bash
sudo apt update
sudo apt install python3-venv -y
```

### 3. Create the environment inside the repo

```bash
python3.12 -m venv .venv
```

If `python3.12` is not available, use:

```bash
python3 -m venv .venv
```

### 4. Activate it

```bash
source .venv/bin/activate
```

Your shell prompt should usually show:

```text
(.venv)
```

### 5. Verify the Python interpreter

```bash
which python
python --version
```

Expected path:

```text
/home/javi/projects/your-repo/.venv/bin/python
```

### 6. Upgrade `pip`

```bash
python -m pip install --upgrade pip
```

### 7. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 8. Add the environment folder to `.gitignore`

```bash
touch .gitignore
grep -qxF ".venv/" .gitignore || echo ".venv/" >> .gitignore
```

---

## Daily Usage

```bash
cd ~/projects/your-repo
source .venv/bin/activate
```

Check that the correct interpreter is active:

```bash
which python
```

Expected:

```text
/home/javi/projects/your-repo/.venv/bin/python
```

---

## VS Code Setup

Open the repo root in VS Code.

Example:

```bash
code ~/projects/your-repo
```

Then:

```text
Ctrl + Shift + P
Python: Select Interpreter
```

Choose:

```text
.venv (Python 3.12.x)
```

If it does not appear, use:

```text
Enter interpreter path
```

Paste the full path:

```text
/home/javi/projects/your-repo/.venv/bin/python
```

---

## VS Code Workspace Settings

Create the `.vscode` folder:

```bash
mkdir -p .vscode
```

Write the interpreter setting:

```bash
cat > .vscode/settings.json <<'EOF'
{
  "python.defaultInterpreterPath": "./.venv/bin/python"
}
EOF
```

This path is relative to the repo root. It works when VS Code is opened at the same folder where `.venv` exists.

Reload VS Code:

```text
Ctrl + Shift + P
Developer: Reload Window
```

---

## Optional: Export Dependencies

Export the current installed packages:

```bash
python -m pip freeze > requirements.txt
```

Install them later in a recreated environment:

```bash
python -m pip install -r requirements.txt
```

---

## Recreate the Environment Later

Delete the old environment:

```bash
rm -rf .venv
```

Create it again:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

---

## One-Liner Version

```bash
cd ~/projects/your-repo && sudo apt update && sudo apt install python3.12-venv -y && python3.12 -m venv .venv && source .venv/bin/activate && python -m pip install --upgrade pip && python -m pip install -r requirements.txt
```

---

## Full Setup With Jupyter Kernel and VS Code

Run this inside the project root.

It installs Ubuntu/WSL `venv` support, creates the local Python environment, installs the Jupyter kernel, points VS Code to the repo environment, and saves ignore rules.

```bash
sudo apt update
sudo apt install python3.12-venv -y

python3.12 -m venv .venv
source .venv/bin/activate

python -m pip install --upgrade pip
python -m pip install ipykernel

python -m pip install -r requirements.txt

PROJECT_NAME=$(basename "$PWD")

python -m ipykernel install --user \
  --name "$PROJECT_NAME-venv" \
  --display-name "$PROJECT_NAME (.venv Python 3.12)"

which python
python --version

mkdir -p .vscode

cat > .vscode/settings.json <<'EOF'
{
  "python.defaultInterpreterPath": "./.venv/bin/python"
}
EOF

touch .gitignore
grep -qxF ".venv/" .gitignore || echo ".venv/" >> .gitignore
grep -qxF ".vscode/" .gitignore || echo ".vscode/" >> .gitignore
grep -qxF ".agents/" .gitignore || echo ".agents/" >> .gitignore
grep -qxF ".codex/" .gitignore || echo ".codex/" >> .gitignore
```

Then reload VS Code:

```text
Ctrl + Shift + P
Developer: Reload Window
```

Then select the interpreter:

```text
Ctrl + Shift + P
Python: Select Interpreter
.venv (Python 3.12.x)
```

---

## Full Setup VS Code Without Jupyter

Run this inside the project root.

It installs Ubuntu/WSL `venv` support, creates the local Python environment, points VS Code to the repo environment, and saves ignore rules.

```bash
sudo apt update
sudo apt install python3.12-venv -y

python3.12 -m venv .venv
source .venv/bin/activate

python -m pip install --upgrade pip
python -m pip install -r requirements.txt

which python
python --version

mkdir -p .vscode

cat > .vscode/settings.json <<'EOF'
{
  "python.defaultInterpreterPath": "./.venv/bin/python"
}
EOF

touch .gitignore
grep -qxF ".venv/" .gitignore || echo ".venv/" >> .gitignore
grep -qxF ".vscode/" .gitignore || echo ".vscode/" >> .gitignore
grep -qxF ".agents/" .gitignore || echo ".agents/" >> .gitignore
grep -qxF ".codex/" .gitignore || echo ".codex/" >> .gitignore
```

Then reload VS Code:

```text
Ctrl + Shift + P
Developer: Reload Window
```

Then select the interpreter:

```text
Ctrl + Shift + P
Python: Select Interpreter
.venv (Python 3.12.x)
```

---

## Clean Up Old Local Conda Environment

If the repo previously used a local Conda environment:

```bash
conda deactivate 2>/dev/null || true
deactivate 2>/dev/null || true

rm -rf .conda
```

Keep `.conda/` in `.gitignore` so it does not get committed later:

```bash
grep -qxF ".conda/" .gitignore || echo ".conda/" >> .gitignore
```

---

## Troubleshooting

### `ensurepip` is not available

If you see:

```text
The virtual environment was not created successfully because ensurepip is not available.
```

Install the missing package:

```bash
sudo apt update
sudo apt install python3.12-venv -y
```

Then recreate the environment:

```bash
rm -rf .venv
python3.12 -m venv .venv
source .venv/bin/activate
```

### `source .venv/bin/activate` fails

If this fails:

```text
No such file or directory
```

the environment was not created correctly.

Fix:

```bash
rm -rf .venv
python3.12 -m venv .venv
source .venv/bin/activate
```

Wait until `python3.12 -m venv .venv` finishes. Do not interrupt it with `Ctrl+C`.

### `python` command not found

Before activating the environment, Ubuntu may only expose:

```bash
python3
```

After activating `.venv`, this should work:

```bash
python
```

### VS Code cannot resolve interpreter path

Check that VS Code opened the repo root, not a parent folder.

Run in the VS Code terminal:

```bash
pwd
ls -l .venv/bin/python
cat .vscode/settings.json
```

Expected:

```text
/home/javi/projects/your-repo
.venv/bin/python exists
{
  "python.defaultInterpreterPath": "./.venv/bin/python"
}
```

If the files are correct but VS Code still warns, select the interpreter manually:

```text
Ctrl + Shift + P
Python: Select Interpreter
.venv (Python 3.12.x)
```

Then reload:

```text
Ctrl + Shift + P
Developer: Reload Window
```

---

## Notes

The recommended folder name is:

```text
.venv/
```

Do not commit `.venv/`.

The VS Code path:

```json
{
  "python.defaultInterpreterPath": "./.venv/bin/python"
}
```

is relative to the folder opened in VS Code.

This means the pattern only works reliably when VS Code is opened at the project root.

---

## What This Gives You

- One isolated Python environment per project.
    
- No dependency conflicts between repositories.
    
- Works without Conda.
    
- Standard Python tooling.
    
- VS Code uses the repo-local interpreter.
    
- Simple mental model: repo equals environment.