# Conda Per-Repository Environment

## Standard Setup

### 1. Go to your project

```bash
cd ~/projects/your-repo
```

### 2. Create the environment inside the repo

```bash
conda create -p ./.conda python=3.12 -y
```

### 3. Activate it

```bash
conda activate ./.conda
```

### 4. Verify the Python interpreter

```bash
which python
```

Expected path:

```text
/home/javi/projects/your-repo/.conda/bin/python
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

### 6. Add the environment folder to `.gitignore`

```bash
echo ".conda/" >> .gitignore
```

---

## Daily Usage

```bash
cd ~/projects/your-repo
conda activate ./.conda
```

---

## VS Code Setup

Open the repo folder in VS Code.

Then:

```text
Ctrl + Shift + P
Python: Select Interpreter
```

Choose:

```text
./.conda/bin/python
```

If it does not appear, use:

```text
Enter interpreter path
```

Paste the full path:

```text
/home/javi/projects/your-repo/.conda/bin/python
```

---

## Optional: Export Environment

Export the environment for reproducibility:

```bash
conda env export > environment.yml
```

Recreate it later:

```bash
conda env create -p ./.conda -f environment.yml
```

---

## One-Liner Version

```bash
cd ~/projects/your-repo && conda create -p ./.conda python=3.12 -y && conda activate ./.conda
```

---

## Full Setup With Jupyter Kernel and VS Code

Run this inside the project folder. It creates the local Conda environment, installs the Jupyter kernel, points VS Code to the repo environment, and saves the ignore rules.

```bash
conda create -p ./.conda python=3.12 -y
conda activate ./.conda

python -m pip install --upgrade pip
python -m pip install ipykernel

pip install -r requirements.txt

PROJECT_NAME=$(basename "$PWD")

python -m ipykernel install --user \
  --name "$PROJECT_NAME-conda" \
  --display-name "$PROJECT_NAME (.conda Python 3.12)"

which python

mkdir -p .vscode

cat > .vscode/settings.json <<'EOF'
{
  "python.defaultInterpreterPath": "./.conda/bin/python"
}
EOF

grep -qxF ".conda/" .gitignore || echo ".conda/" >> .gitignore
grep -qxF ".vscode/" .gitignore || echo ".vscode/" >> .gitignore
grep -qxF ".agents/" .gitignore || echo ".codex/" >> .gitignore
grep -qxF ".codex/" .gitignore || echo ".agents/" >> .gitignore
```

Then reload VS Code so it picks up the interpreter setting:

```text
Ctrl + Shift + P
Developer: Reload Window
```

---

## What This Gives You

- One isolated environment per project.
- No dependency conflicts between repositories.
- Predictable builds.
- Simple mental model: repo equals environment.
