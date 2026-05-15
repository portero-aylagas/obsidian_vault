# Python `.gitignore`

Use this as a standard `.gitignore` for Python, Conda, VS Code, Jupyter, and dotenv-based projects.

```gitignore
# =========================
# Python
# =========================
__pycache__/
*.py[cod]
*$py.class

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
*.egg-info/
.installed.cfg
*.egg

# Virtual environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# =========================
# Conda
# =========================
.conda/
*.conda

# =========================
# Jupyter Notebook
# =========================
.ipynb_checkpoints/

# =========================
# VS Code
# =========================
.vscode/

# =========================
# OS files
# =========================
.DS_Store
Thumbs.db

# =========================
# Logs
# =========================
*.log

# =========================
# dotenv / secrets
# =========================
.env
.env.*
*.env

# =========================
# pytest / coverage
# =========================
.pytest_cache/
.coverage
.coverage.*
htmlcov/

# =========================
# mypy / type checking
# =========================
.mypy_cache/
.dmypy.json
dmypy.json

# =========================
# pyright
# =========================
.pyright/

# =========================
# pipenv / poetry
# =========================
Pipfile.lock
poetry.lock

# =========================
# Temporary / misc
# =========================
*.tmp
*.swp
*.bak
```
