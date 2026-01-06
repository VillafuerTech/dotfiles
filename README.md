# Dotfiles

Minimal macOS terminal-focused development environment.

## Supported Tools

| Tool | Purpose |
|------|---------|
| [WezTerm](https://wezfurlong.org/wezterm/) | Terminal emulator |
| [Zsh](https://www.zsh.org/) | Shell |
| [Starship](https://starship.rs/) | Shell prompt |
| [NeoVim](https://neovim.io/) | Editor |
| [Tmux](https://github.com/tmux/tmux/wiki) | Terminal multiplexer |
| [Ranger](https://github.com/ranger/ranger) | File manager |

Theme: Nord (configurable to OneDark via env vars in `zsh/.zshenv`)

## Requirements

- macOS (tested on Apple Silicon, Homebrew at `/opt/homebrew`)
- Xcode Command Line Tools
- Homebrew

## Quick Start

```bash
git clone https://github.com/YOUR_USER/dotfiles ~/.config/dotfiles
cd ~/.config/dotfiles
./install.sh
```

The installer prompts for:
1. **Install apps?** - Runs Homebrew to install packages from `homebrew/Brewfile`
2. **Overwrite existing dotfiles?** - Removes existing symlinks/files before creating new ones

## What Gets Changed

- Symlinks created from this repo to `~/.config/` and `~/`
- Homebrew packages installed (if selected)
- macOS defaults applied (Dock, Finder preferences)
- `~/.hushlogin` created (suppresses terminal login message)

## How Symlinks Work

Mappings are defined in `symlinks.conf`:
```
$(pwd)/nvim:$HOME/.config/nvim
$(pwd)/zsh/.zshrc:$HOME/.zshrc
```

Manual management:
```bash
./scripts/symlinks.sh --create   # Create symlinks
./scripts/symlinks.sh --delete   # Remove symlinks only
```

## Theme Configuration

Environment variables in `zsh/.zshenv` control theming:
- `NVIM_THEME` - NeoVim colorscheme
- `TMUX_THEME` - Tmux status bar
- `STARSHIP_THEME` - Shell prompt
- `WEZTERM_THEME` - Terminal colors

Values: `nord` (default), `onedark`

## Maintenance

### Homebrew
```bash
brew bundle check --file=homebrew/Brewfile  # Check status
brew bundle --file=homebrew/Brewfile        # Install missing
brew bundle dump --file=homebrew/Brewfile --force  # Update Brewfile from installed
```

### NeoVim Plugins
Plugins managed by [lazy.nvim](https://github.com/folke/lazy.nvim). Lock file: `nvim/lazy-lock.json`
```bash
nvim                    # Open nvim, lazy.nvim auto-installs
:Lazy update            # Update plugins
:Lazy restore           # Restore from lock file
```

### Tmux Plugins
```bash
tmux source ~/.config/tmux/tmux.conf   # Reload config
# Press prefix + I to install plugins via TPM
```

## Troubleshooting

```bash
# Verify symlinks work
./scripts/symlinks.sh --delete && ./scripts/symlinks.sh --create

# Test nvim config
nvim --headless "+quitall"

# Test tmux config
tmux -f tmux/tmux.conf new-session -d && tmux kill-server

# Brewfile issues
brew bundle check --file=homebrew/Brewfile
```

## What's NOT Included

This repo intentionally excludes:
- VS Code (not used)
- iTerm2, Kitty (WezTerm only)
- Karabiner-Elements, Rectangle (default macOS window management)
- Obsidian, DBeaver, Vim configs

## Adding New Dotfiles

1. Place config in appropriate directory
2. Add mapping to `symlinks.conf`
3. Run `./scripts/symlinks.sh --create`

## Documentation

- [docs/SETUP.md](docs/SETUP.md) - Detailed install steps
- [docs/CONFIG_OVERVIEW.md](docs/CONFIG_OVERVIEW.md) - Module explanations
- [docs/MAINTENANCE.md](docs/MAINTENANCE.md) - Update workflows
- [docs/VERIFY.md](docs/VERIFY.md) - Verification commands
