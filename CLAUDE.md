# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

Minimal macOS dotfiles for terminal-focused development. Configures WezTerm, Zsh, Starship, NeoVim, Tmux, and Ranger.

## Commands

```bash
./install.sh                          # Full setup (interactive)
./scripts/symlinks.sh --create        # Create symlinks only
./scripts/symlinks.sh --delete        # Remove symlinks
brew bundle --file=homebrew/Brewfile  # Install Homebrew packages
```

## Structure

```
homebrew/Brewfile     # Package definitions
nvim/                 # NeoVim config (lazy.nvim)
ranger/               # File manager config
scripts/              # Install helpers
starship/             # Prompt config
symlinks.conf         # Symlink mappings (source:target)
tmux/                 # Multiplexer config
wezterm/              # Terminal config (Lua)
zsh/                  # Shell config
```

## Key Files

- `symlinks.conf` - Defines all symlink source:target mappings
- `zsh/.zshenv` - Theme env vars: `NVIM_THEME`, `TMUX_THEME`, `STARSHIP_THEME`, `WEZTERM_THEME`
- `nvim/lazy-lock.json` - Pinned plugin versions (preserve for reproducibility)

## Not Included

VS Code, iTerm2, Kitty, Karabiner-Elements, Rectangle, Obsidian, DBeaver, Vim configs were intentionally removed. Uses default macOS window management.
