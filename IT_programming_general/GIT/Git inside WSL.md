# Git Inside WSL

## 1. Install Git

```bash
sudo apt update
sudo apt install -y git
git --version
```

---

## 2. Configure Git Identity

```bash
git config --global user.name "portero-aylagas"
git config --global user.email "portero.aylagas.javier@gmail.com"
```

Check the configuration:

```bash
git config --global --list
```

Expected relevant output:

```text
user.name=portero-aylagas
user.email=portero.aylagas.javier@gmail.com
```

---

## 3. Create a Work Folder

```bash
mkdir -p ~/projects
cd ~/projects
pwd
```

Expected path:

```text
/home/javi/projects
```

---

## 4. Generate SSH Key Inside WSL

```bash
ssh-keygen -t ed25519 -C "portero.aylagas.javier@gmail.com"
```

Recommended defaults:

```text
File: press Enter
Passphrase: optional
```

---

## 5. Start SSH Agent and Add Key

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

## 6. Copy Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the full output.

It starts with something like:

```text
ssh-ed25519 AAAA...
```

---

## 7. Add Key to GitHub

In GitHub:

```text
Settings
SSH and GPG keys
New SSH key
```

Use a title like:

```text
WSL Laptop
```

Paste the public key and save.

---

## 8. Test GitHub SSH Connection

```bash
ssh -T git@github.com
```

Expected output:

```text
Hi portero-aylagas! You've successfully authenticated...
```

---

## 9. Use SSH URLs

When cloning repositories, use SSH:

```bash
git clone git@github.com:portero-aylagas/<repo>.git
```

Avoid HTTPS URLs if you want SSH authentication.

---

## 10. Make SSH Agent Persistent

Open `.bashrc`:

```bash
nano ~/.bashrc
```

Add this at the end:

```bash
# Start SSH agent and add GitHub key
eval "$(ssh-agent -s)" > /dev/null
ssh-add ~/.ssh/id_ed25519 2>/dev/null
```

Save and exit nano:

```text
Ctrl + O
Enter
Ctrl + X
```

Reload `.bashrc`:

```bash
source ~/.bashrc
```
