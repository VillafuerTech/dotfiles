# Dotfiles

Configuration files for my macOS development environment. These dotfiles are minimal and focused on a core terminal-based workflow.

## Tools

- **Terminal**: [WezTerm](https://wezfurlong.org/wezterm/index.html)
- **Multiplexer**: [Tmux](https://github.com/tmux/tmux/wiki)
- **Editor**: [NeoVim](https://neovim.io/)
- **Shell Prompt**: [Starship](https://starship.rs/)
- **File Manager**: [Ranger](https://github.com/ranger/ranger)
- **Color Theme**: Nord (configurable via environment variables in `.zshenv`)

## Setup

```bash
./install.sh
```

The installer will prompt you to:
1. Install apps via Homebrew (optional)
2. Overwrite existing dotfiles (optional)

## How It Works

### Symlinks

All configurations are managed via symlinks defined in `symlinks.conf`. Each line maps a source file in this repo to its target location:

```
$(pwd)/nvim:$HOME/.config/nvim
$(pwd)/zsh/.zshrc:$HOME/.zshrc
```

To manage symlinks manually:
```bash
./scripts/symlinks.sh --create   # Create all symlinks
./scripts/symlinks.sh --delete   # Remove symlinks only
```

### Theme Configuration

Themes are controlled by environment variables in `zsh/.zshenv`:
- `NVIM_THEME` - NeoVim colorscheme
- `TMUX_THEME` - tmux status bar theme
- `STARSHIP_THEME` - Shell prompt theme
- `WEZTERM_THEME` - Terminal theme

Supported values: `nord`, `onedark`

### Homebrew

All packages are defined in `homebrew/Brewfile`. To update:
```bash
brew bundle --file=homebrew/Brewfile
```

### Neovim Plugins

Plugins are managed by [lazy.nvim](https://github.com/folke/lazy.nvim). The `nvim/lazy-lock.json` file locks plugin versions for reproducibility.

## Adding New Dotfiles

1. Place the config in the appropriate directory
2. Add a mapping to `symlinks.conf`
3. Run `./scripts/symlinks.sh --create`
