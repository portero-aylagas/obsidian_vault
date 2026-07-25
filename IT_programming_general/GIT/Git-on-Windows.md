# Git on Windows

## 1. Install Git

Install Git for Windows using PowerShell:

```powershell
winget install --id Git.Git -e
```

Close and reopen PowerShell, then check the installation:

```powershell
git --version
```

## 2. Configure Git Identity

```powershell
git config --global user.name "portero-aylagas"
git config --global user.email "portero.aylagas.javier@gmail.com"
```

Check the configuration:

```powershell
git config --global --list
```

Expected relevant output:

```text
user.name=portero-aylagas
user.email=portero.aylagas.javier@gmail.com
```

## 3. Create a Work Folder

```powershell
New-Item -ItemType Directory -Force "D:\git_repos"
Set-Location "D:\git_repos"
Get-Location
```

Expected path:

```text
D:\git_repos
```

## 4. Generate an SSH Key in Windows

```powershell
ssh-keygen -t ed25519 -C "portero.aylagas.javier@gmail.com"
```

Recommended defaults:

- File: press **Enter**
- Passphrase: optional

The default key location is:

```text
C:\Users\j_por\.ssh\id_ed25519
```

## 5. Start the SSH Agent and Add the Key

Open **PowerShell as Administrator** and run:

```powershell
Set-Service -Name ssh-agent -StartupType Automatic
Start-Service -Name ssh-agent
Get-Service -Name ssh-agent
```

The service status should be `Running`.

Then open a normal PowerShell window and add the key:

```powershell
ssh-add "$HOME\.ssh\id_ed25519"
```

Check that the key is loaded:

```powershell
ssh-add -l
```

## 6. Copy the Public Key

Copy the public key directly to the Windows clipboard:

```powershell
Get-Content "$HOME\.ssh\id_ed25519.pub" | Set-Clipboard
```

To display it instead:

```powershell
Get-Content "$HOME\.ssh\id_ed25519.pub"
```

The output starts with something like:

```text
ssh-ed25519 AAAA...
```

Only share the public key ending in `.pub`. Never share the private `id_ed25519` file.

## 7. Add the Key to GitHub

In GitHub:

1. Open **Settings**.
2. Select **SSH and GPG keys**.
3. Select **New SSH key**.
4. Use a title such as:

```text
Windows Laptop
```

Paste the public key and save.

## 8. Test the GitHub SSH Connection

```powershell
ssh -T git@github.com
```

On the first connection, you may see:

```text
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Enter:

```text
yes
```

Expected output:

```text
Hi portero-aylagas! You've successfully authenticated, but GitHub does not provide shell access.
```

This is a successful connection. GitHub supports Git operations over SSH but does not provide an interactive server shell.

## 9. Use SSH URLs

Move to the repository folder:

```powershell
Set-Location "D:\git_repos"
```

When cloning repositories, use SSH:

```powershell
git clone git@github.com:portero-aylagas/<repo>.git
```

Avoid HTTPS URLs if you want SSH authentication.

For an existing repository, check its remote:

```powershell
git remote -v
```

To change an existing `origin` remote from HTTPS to SSH:

```powershell
git remote set-url origin git@github.com:portero-aylagas/<repo>.git
```

## 10. Make the SSH Agent Persistent

The following administrator command configures the Windows SSH agent to start automatically:

```powershell
Set-Service -Name ssh-agent -StartupType Automatic
```

Unlike WSL, Windows does not use `.bashrc` or this Linux command:

```text
eval "$(ssh-agent -s)"
```

After the key has been added with `ssh-add`, Windows can use the SSH agent for future Git operations.
