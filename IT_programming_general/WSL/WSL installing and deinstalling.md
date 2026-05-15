# WSL Installing and Uninstalling

## List Installed WSL Distributions

Open PowerShell and run:

```powershell
wsl --list --verbose
```

---

## Uninstall a WSL Distribution

Open PowerShell and run:

```powershell
wsl --unregister Ubuntu-24.04
```

Warning: this deletes that WSL distribution and its Linux filesystem.

---

## Install Ubuntu 24.04 in WSL

Open PowerShell and run:

```powershell
wsl --install Ubuntu-24.04
```

---

## WSL Distribution Storage Location

Each WSL distribution is stored somewhere under:

```text
C:\Users\<user>\AppData\Local\Packages\
```

Do not manually edit Linux files from this Windows folder unless you know exactly what you are doing.

Use WSL paths instead:

```bash
/home/javi
~/projects
```
