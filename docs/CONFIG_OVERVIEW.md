# Configuration Overview

Brief explanation of each module in this dotfiles repo.

## WezTerm (`wezterm/`)

GPU-accelerated terminal emulator. Config in Lua.

- `wezterm.lua` - Entry point, loads config and applies theme
- `config.lua` - Main settings: font, padding, keybindings, hyperlink rules
- `events.lua` - Startup events (auto-maximize window)

Theme controlled by `WEZTERM_THEME` env var. Defaults to Nord.

## Zsh (`zsh/`)

Shell configuration split into focused files.

- `.zshrc` - Minimal loader, sources other files
- `.zshenv` - Environment variables, theme settings, PATH
- `custom.zsh` - Shell options, history, completions, starship init
- `aliases.zsh` - Command aliases (ls→eza, vim→nvim, etc.)
- `git-completion.*` - Git tab completion

## Starship (`starship/`)

Cross-shell prompt. Single config file.

- `starship.toml` - Prompt format, symbols, colors

Initialized in `zsh/custom.zsh` via `eval "$(starship init zsh)"`.

## NeoVim (`nvim/`)

Lua-based config using lazy.nvim plugin manager.

- `init.lua` - Entry point, loads core modules and plugins
- `lua/core/options.lua` - Editor settings (tabs, numbers, etc.)
- `lua/core/keymaps.lua` - Key bindings
- `lua/core/snippets.lua` - Custom code snippets
- `lua/plugins/` - Plugin specs (one file per plugin)
- `lua/plugins/themes/` - Colorscheme configs
- `lua/tools/sql-runner.lua` - Custom SQL execution tool
- `lazy-lock.json` - Pinned plugin versions

Theme controlled by `NVIM_THEME` env var.

## Tmux (`tmux/`)

Terminal multiplexer config.

- `tmux.conf` - Main config: prefix key, bindings, status bar
- `nord-theme.conf` - Nord colorscheme for status bar
- `onedark-theme.conf` - OneDark alternative

Uses TPM (Tmux Plugin Manager). Theme loaded based on `TMUX_THEME` env var.

## Ranger (`ranger/`)

Terminal file manager. Python-based config.

Contains rc.conf and other ranger settings. Symlinked to `~/.config/ranger`.

## Scripts (`scripts/`)

Helper scripts for installation.

- `utils.sh` - Colored output functions (info, warning, error, success)
- `prerequisites.sh` - Xcode and Homebrew checks
- `brew-install-custom.sh` - Homebrew bundle runner
- `osx-defaults.sh` - macOS system preferences
- `symlinks.sh` - Symlink creation/deletion

## Homebrew (`homebrew/`)

Package definitions.

- `Brewfile` - All brew formulae and casks to install
