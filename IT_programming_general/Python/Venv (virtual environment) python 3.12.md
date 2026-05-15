# Python 3.12 Virtual Environment With `venv`

## 1. Install `venv` Support

```bash
sudo apt update
sudo apt install -y python3.12-venv python3-pip
```

---

## 2. Create the Virtual Environment

Run this inside your project:

```bash
cd ~/projects/Deeplearning_AI
python3 -m venv .venv
```

---

## 3. Activate the Environment

```bash
source .venv/bin/activate
```

Your terminal should show something like:

```text
(.venv) javi@Teodora:~/projects/Deeplearning_AI$
```

---

## 4. Verify the Environment

```bash
python --version
which python
```

Expected:

```text
Python 3.12.x
/home/javi/projects/Deeplearning_AI/.venv/bin/python
```

---

## 5. Upgrade `pip`

```bash
python -m pip install --upgrade pip
```

---

## 6. Install Dependencies

If the project has a `requirements.txt` file:

```bash
pip install -r requirements.txt
```

---

## 7. Save Ignore Rules

Create or update `.gitignore`:

```bash
cat >> .gitignore <<'EOF'
.venv/
__pycache__/
*.pyc
.ipynb_checkpoints/
EOF
```

---

## 8. Daily Usage

```bash
cd ~/projects/Deeplearning_AI
source .venv/bin/activate
```

---

## 9. Deactivate

```bash
deactivate
```
