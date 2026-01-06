# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

Personal dotfiles for macOS. Manages configurations for WezTerm, tmux, NeoVim, zsh, Starship, and Ranger through symlinks.

## Common Commands

```bash
./install.sh                          # Full setup (prompts for options)
./scripts/symlinks.sh --create        # Create symlinks only
./scripts/symlinks.sh --delete        # Remove symlinks
brew bundle --file=homebrew/Brewfile  # Install packages from Brewfile
```

## Architecture

### Symlink System
`symlinks.conf` defines source:target mappings. `scripts/symlinks.sh` reads this config to create/delete symlinks. Sources are relative to repo root; targets typically in `~/.config/`.

### Theme System
Consistent theming (nord/onedark) via environment variables in `zsh/.zshenv`:
- `NVIM_THEME`, `TMUX_THEME`, `STARSHIP_THEME`, `WEZTERM_THEME`

### NeoVim Structure (`nvim/`)
- `init.lua` - Entry point, loads lazy.nvim plugin manager
- `lua/core/` - Core settings: `options.lua`, `keymaps.lua`, `snippets.lua`
- `lua/plugins/` - Individual plugin configs
- `lua/plugins/themes/` - Theme configurations
- Themes loaded dynamically based on `NVIM_THEME` env var

### Adding New Dotfiles
1. Place config file in appropriate subdirectory
2. Add source:target mapping to `symlinks.conf`
3. Run `./scripts/symlinks.sh --create`
