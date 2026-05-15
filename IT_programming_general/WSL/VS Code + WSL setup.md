# VS Code + WSL Setup

## 1. Install VS Code on Windows

Install:

```text
Visual Studio Code
```

No special installation options are required.

---

## 2. Install the WSL Extension

In VS Code:

```text
Extensions
Remote - WSL
Install
```

This extension connects VS Code to the Linux environment inside WSL.

---

## 3. Connect VS Code to WSL

In VS Code:

```text
Ctrl + Shift + P
WSL: Connect to WSL
```

Select:

```text
Ubuntu-24.04
```

A new VS Code window opens connected to WSL.

---

## 4. Open Your Project From WSL

In the WSL-connected VS Code window:

```text
File
Open Folder
```

Navigate to:

```text
/home/javi/projects
```

Or open a specific repo:

```text
/home/javi/projects/Deeplearning_AI
```

---

## 5. Verify Environment

Check the bottom-left corner of VS Code.

Expected:

```text
WSL: Ubuntu-24.04
```

Open the integrated terminal and run:

```bash
which git
```

Expected:

```text
/usr/bin/git
```

Also check that the terminal prompt is from Linux, for example:

```text
javi@Teodora:~/projects/your-repo$
```

---

## 6. Install Extensions Inside WSL

In the WSL VS Code window, install:

```text
Python
Pylance
GitLens
Copilot
```

Important: install them in WSL, not only in Local.

VS Code usually shows whether the extension is installed in:

```text
Local
WSL: Ubuntu-24.04
```

---

## 7. Daily Workflow

### Recommended Option

From the Ubuntu terminal:

```bash
cd ~/projects/<repo>
code .
```

### Alternative Option

From VS Code:

```text
Ctrl + Shift + P
WSL: Connect to WSL
File
Open Folder
/home/javi/projects/<repo>
```
