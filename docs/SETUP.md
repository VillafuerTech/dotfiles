# Setup Guide

Step-by-step installation for a fresh macOS system.

## Prerequisites

1. **Xcode Command Line Tools**
   ```bash
   xcode-select --install
   ```

2. **Homebrew** (if not installed, install.sh will prompt)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

## Installation

```bash
git clone https://github.com/YOUR_USER/dotfiles ~/.config/dotfiles
cd ~/.config/dotfiles
./install.sh
```

## What install.sh Does

### 1. Prerequisites (if "Install apps? y")
- Verifies/installs Xcode CLI tools
- Verifies/installs Homebrew

### 2. Apps (if "Install apps? y")
- Runs `brew bundle` with `homebrew/Brewfile`
- Installs: neovim, tmux, ranger, starship, wezterm, fzf, ripgrep, lazygit, etc.

### 3. macOS Defaults (always)
- Registers CTRL+/ keyboard binding (prevents system beep)
- Applies Finder/Dock preferences:
  - Key repeat enabled
  - Three-finger drag
  - Hidden files visible
  - Dock autohide
  - Desktop icons hidden

### 4. Terminal Setup (always)
- Creates `~/.hushlogin` to suppress login message

### 5. Symlinks (always)
- If "Overwrite existing? y": deletes existing symlinks/files first
- Creates symlinks from repo to target locations

## Post-Install

1. **Restart terminal** to load new shell config
2. **Open NeoVim** - lazy.nvim will auto-install plugins
3. **Open Tmux** - press `prefix + I` to install TPM plugins

## Symlink Targets

| Source | Target |
|--------|--------|
| `zsh/.zshrc` | `~/.zshrc` |
| `zsh/.zshenv` | `~/.zshenv` |
| `zsh/*.zsh` | `~/.config/zsh/` |
| `nvim/` | `~/.config/nvim` |
| `tmux/*.conf` | `~/.config/tmux/` |
| `wezterm/` | `~/.config/wezterm` |
| `starship/starship.toml` | `~/.config/starship/starship.toml` |
| `ranger/` | `~/.config/ranger` |

## Uninstall

Remove symlinks only (keeps repo):
```bash
./scripts/symlinks.sh --delete
```

Remove symlinks and target files:
```bash
./scripts/symlinks.sh --delete --include-files
```
