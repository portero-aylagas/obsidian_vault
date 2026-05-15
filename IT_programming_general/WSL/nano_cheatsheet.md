# Nano Cheatsheet

## Open / Create a File

```bash
nano filename.md
```

Opens an existing file or creates it if it does not exist.

---

## Basic Commands

| Action | Shortcut |
|---|---|
| Save file | `Ctrl + O` |
| Confirm save filename | `Enter` |
| Exit nano | `Ctrl + X` |
| Cancel current action | `Ctrl + C` |
| Help menu | `Ctrl + G` |

---

## Navigation

| Action | Shortcut |
|---|---|
| Move cursor | Arrow keys |
| Start of line | `Ctrl + A` |
| End of line | `Ctrl + E` |
| Previous page | `Ctrl + Y` |
| Next page | `Ctrl + V` |
| Go to line/column | `Ctrl + _` |
| Show current position | `Ctrl + C` |

---

## Editing

| Action | Shortcut |
|---|---|
| Cut current line | `Ctrl + K` |
| Paste cut text | `Ctrl + U` |
| Delete character under cursor | `Ctrl + D` |
| Backspace | `Backspace` |
| Justify paragraph | `Ctrl + J` |
| Undo | `Alt + U` |
| Redo | `Alt + E` |

---

## Search and Replace

| Action | Shortcut |
|---|---|
| Search text | `Ctrl + W` |
| Search next match | `Ctrl + W`, then `Enter` |
| Replace text | `Ctrl + \\` |

---

## Copy / Paste

| Action | Shortcut |
|---|---|
| Start selection | `Alt + A` |
| Move cursor to select | Arrow keys |
| Copy selected text | `Alt + 6` |
| Cut selected text | `Ctrl + K` |
| Paste text | `Ctrl + U` |

### Copy a block of text

1. Move the cursor to the start of the text.
2. Press `Alt + A` to start selection.
3. Move the cursor to the end of the text.
4. Press `Alt + 6` to copy.
5. Move where you want to paste.
6. Press `Ctrl + U`.

### Cut and paste a block

1. Move the cursor to the start of the text.
2. Press `Alt + A`.
3. Select the block.
4. Press `Ctrl + K` to cut.
5. Move where you want to paste.
6. Press `Ctrl + U`.

Note: in some terminals, `Alt` shortcuts may require pressing `Esc` first, then the key. For example, `Alt + 6` can be `Esc`, then `6`.

---

## Useful Launch Options

```bash
nano -l filename.md
```

Opens nano with line numbers enabled.

```bash
nano +25 filename.md
```

Opens the file directly at line 25.

```bash
nano -m filename.md
```

Enables mouse support.

```bash
nano -w filename.md
```

Disables automatic line wrapping.

---

## Common Workflow

```bash
nano notes.md
```

Inside nano:

1. Edit the file.
2. Press `Ctrl + O` to save.
3. Press `Enter` to confirm.
4. Press `Ctrl + X` to exit.

---

## Emergency Exit Logic

If you press `Ctrl + X` and nano asks:

```text
Save modified buffer?
```

Choose:

| Key | Meaning |
|---|---|
| `Y` | Save changes |
| `N` | Exit without saving |
| `Ctrl + C` | Cancel exit and return to editing |

---

## Nano Shortcut Notation

Nano shows shortcuts at the bottom like this:

| Nano Notation | Meaning |
|---|---|
| `^O` | `Ctrl + O` |
| `^X` | `Ctrl + X` |
| `M-A` | `Alt + A` |
| `M-U` | `Alt + U` |

`^` means `Ctrl`.  
`M` means `Alt` or `Esc` first.
