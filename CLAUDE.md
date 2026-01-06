# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a personal dotfiles repository for macOS development environment configuration. It manages configurations for NeoVim, tmux, zsh, WezTerm, Karabiner-Elements, and other tools through symlinks.

## Common Commands

### Installation
```bash
./install.sh                          # Full setup (prompts for options)
./scripts/symlinks.sh --create        # Create symlinks only
./scripts/symlinks.sh --delete        # Remove symlinks
./scripts/symlinks.sh --delete --include-files  # Remove symlinks and target files
```

### Homebrew Package Management
```bash
./scripts/brew-install-custom.sh      # Install custom formulae/casks
brew bundle --file=homebrew/Brewfile  # Install from Brewfile
```

## Architecture

### Symlink System
- `symlinks.conf` defines source:target mappings for all dotfiles
- `scripts/symlinks.sh` reads this config to create/delete symlinks
- Sources are relative to repo root; targets typically in `~/.config/`

### Theme System
Consistent theming (nord/onedark) across tools via environment variables in `zsh/.zshenv`:
- `NVIM_THEME` - NeoVim theme selection
- `TMUX_THEME` - tmux status bar theme
- `STARSHIP_THEME` - Shell prompt theme
- `WEZTERM_THEME` - Terminal theme

### NeoVim Structure (`nvim/`)
- `init.lua` - Entry point, loads lazy.nvim plugin manager
- `lua/core/` - Core settings: `options.lua`, `keymaps.lua`, `snippets.lua`
- `lua/plugins/` - Individual plugin configs (telescope, lsp, treesitter, etc.)
- `lua/plugins/themes/` - Theme configurations
- `lua/tools/` - Custom tools like `sql-runner.lua`
- Themes loaded dynamically based on `NVIM_THEME` env var

### Karabiner Configuration
`karabiner/karabiner.json` implements custom window management:
- Tab key as hyperkey (tap=Tab, hold=modifier)
- `Tab + W + key` - Window management layer (Rectangle integration)
- `Tab + E + key` - Exposé layer for app switching

### Adding New Dotfiles
1. Place config file in appropriate subdirectory
2. Add source:target mapping to `symlinks.conf`
3. Run `./scripts/symlinks.sh --create`
4. For new software, add to `homebrew/Brewfile`
