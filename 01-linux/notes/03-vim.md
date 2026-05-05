# Vim Text Editor

## Key Concepts

- Vim lets you create and edit files directly from the command line
- Has three main modes: **Insert**, **Command**, and **Visual**

## Modes

| Mode | How to enter | Purpose |
|------|-------------|---------|
| Insert | Press `i` | Type and edit text |
| Command | Press `Esc` | Navigate and run commands |
| Visual | Press `v` | Select text |

## Navigation (Command Mode)

| Key | Action |
|-----|--------|
| `h` | Move left |
| `j` | Move down |
| `k` | Move up |
| `l` | Move right |
| `0` | Go to start of line |
| `Shift + 4` (`$`) | Go to end of line |
| `w` | Move forward by word |
| `b` | Move backward by word |
| `:2` | Jump to line 2 |
| `/word` | Search for a word |
| `n` | Go to next search result |
| `N` | Go to previous search result |

## Editing (Command Mode)

| Key | Action |
|-----|--------|
| `dd` | Delete entire line |
| `D` | Delete from cursor to end of line |
| `y` | Copy (yank) a line |
| `p` | Paste a line |
| `u` | Undo |
| `Ctrl + r` | Redo |

## Saving and Quitting

| Command | Action |
|---------|--------|
| `:wq` | Save and exit |
| `:wq!` | Force save and exit |
| `:q` | Quit without saving |

## Display Settings

```bash
:set number       # show line numbers
:set nonumber     # hide line numbers
:syntax on        # enable syntax highlighting
```

## What I Learned

I now understand how powerful the vim command is. Command features such as using /word allows you to search for specific words within files containing large texts. This is important for maintaining high levels of efficiency.
