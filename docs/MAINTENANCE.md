# Maintenance Guide

How to keep your dotfiles environment up to date.

## Homebrew Packages

### Check current state
```bash
brew bundle check --file=homebrew/Brewfile
```

### Install missing packages
```bash
brew bundle --file=homebrew/Brewfile
```

### Update Brewfile from installed packages
```bash
brew bundle dump --file=homebrew/Brewfile --force
```

### Upgrade all packages
```bash
brew upgrade
```

### Clean up old versions
```bash
brew cleanup
```

## NeoVim Plugins

### Update all plugins
Inside NeoVim:
```
:Lazy update
```

### Restore to locked versions
```
:Lazy restore
```

### Check plugin health
```
:checkhealth
```

### Update lock file
After testing updates, commit `nvim/lazy-lock.json` to preserve working state.

## Tmux Plugins

### Install plugins
Press `prefix + I` (capital I) inside tmux.

### Update plugins
Press `prefix + U` (capital U) inside tmux.

### Reload config
```bash
tmux source ~/.config/tmux/tmux.conf
```
Or inside tmux: `prefix + r` (if bound)

## Symlinks

### Recreate all symlinks
```bash
./scripts/symlinks.sh --delete
./scripts/symlinks.sh --create
```

### Check for broken symlinks
```bash
find ~/.config -type l ! -exec test -e {} \; -print
```

## Shell

### Reload zsh config
```bash
source ~/.zshrc
```

### Update completions
```bash
rm -f ~/.zcompdump && compinit
```

## Starship

### Reload prompt
Starship reloads automatically. Force with:
```bash
source ~/.zshrc
```

## Running Audits

See [VERIFY.md](VERIFY.md) for verification commands to run after changes.
