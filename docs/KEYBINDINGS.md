# Consolidated Keybindings

**Leader Key:** `<Space>` (Neovim)
**Prefix Key:** `Ctrl + Space` (Tmux)

## 1. Global Navigation (The "Golden Path")
*Works seamlessly across Neovim splits and Tmux panes.*

| Key | Action |
| :--- | :--- |
| `Ctrl + h` | Go Left |
| `Ctrl + j` | Go Down |
| `Ctrl + k` | Go Up |
| `Ctrl + l` | Go Right |

## 2. Neovim Essentials

### General
| Key | Action |
| :--- | :--- |
| `<Space> w` | Save File |
| `<C-s>` | Save File |
| `<C-q>` | Quit Buffer |
| `<Space> +` | Increment Number |
| `<Space> -` | Decrement Number |
| `jk` | Exit Insert Mode |
| `<Space> do` | Toggle Diagnostics |

### Searching (Telescope)
| Key | Action |
| :--- | :--- |
| `<Space> sf` | Find Files |
| `<Space> sg` | Live Grep (Text) |
| `<Space> sb` | Find Buffers |
| `<Space> /` | Fuzzy Search Current Buffer |
| `<Space> sh` | Search Help Tags |

### File Management
| Key | Action |
| :--- | :--- |
| `<Space> e` | NeoTree (Sidebar) |
| `<Space> w` | NeoTree (Float) |
| `-` | Oil (Parent Directory) |

### Git
| Key | Action |
| :--- | :--- |
| `<Space> lg` | LazyGit |
| `]c` | Next Hunk (Gitsigns) |
| `[c` | Prev Hunk (Gitsigns) |
| `<Space> hs` | Stage Hunk |
| `<Space> hr` | Reset Hunk |

### LSP & Code
| Key | Action |
| :--- | :--- |
| `gd` | Goto Definition |
| `gr` | Goto References |
| `K` | Hover Documentation |
| `<Space> ca` | Code Action |
| `<Space> rn` | Rename Symbol |
| `<Space> f` | Format File (if configured) |

## 3. Tmux Essentials

### Window Management
| Key | Action |
| :--- | :--- |
| `<Pre> c` | New Window |
| `<Pre> ,` | Rename Window |
| `<Pre> &` | Kill Window |
| `<Pre> n` | Next Window |
| `<Pre> p` | Previous Window |
| `<Pre> [1-9]` | Select Window N |

### Pane Management
| Key | Action |
| :--- | :--- |
| `<Pre> \` | Split Horizontal |
| `<Pre> -` | Split Vertical |
| `<Pre> m` | Maximize/Zoom Pane |
| `<Pre> x` | Kill Pane |

### Copy Mode
1. `<Pre> [` to enter mode.
2. `v` to visual select.
3. `y` to copy to system clipboard.
4. `<Pre> P` to paste inside tmux (or `Cmd+V` in OS).
