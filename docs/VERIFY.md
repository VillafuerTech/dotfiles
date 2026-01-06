# Verification Commands

Copy-paste these commands to verify repo integrity after changes.

## Quick Health Check

```bash
cd ~/.config/dotfiles

# All checks in sequence
echo "=== Broken symlinks ===" && \
find . -type l ! -exec test -e {} \; -print && \
echo "(none = good)" && \
echo "" && \
echo "=== Shell syntax ===" && \
bash -n install.sh && echo "install.sh OK" && \
for f in scripts/*.sh; do bash -n "$f" && echo "$f OK"; done && \
echo "" && \
echo "=== Brewfile check ===" && \
brew bundle check --file=homebrew/Brewfile 2>&1 || true
```

## Individual Checks

### Broken Symlinks in Repo
```bash
find . -type l ! -exec test -e {} \; -print
```
Expected: no output

### References to Removed Modules
```bash
rg -n "vscode|dbeaver|obsidian|karabiner|rectangle|kitty|iterm" . --glob '!.git' --glob '!docs/PRUNE_PLAN.md'
```
Expected: no output

### Shell Script Syntax
```bash
bash -n install.sh
bash -n scripts/*.sh
```
Expected: no errors

### Brewfile Validity
```bash
brew bundle check --file=homebrew/Brewfile
```
Expected: "satisfied" or list of missing packages

### NeoVim Starts Clean
```bash
nvim --headless "+quitall"
```
Expected: exits without Lua errors (plugin install messages OK)

### Tmux Config Loads
```bash
tmux -f tmux/tmux.conf -L verify new-session -d && \
tmux -L verify kill-server && \
echo "tmux OK"
```
Expected: "tmux OK"

### WezTerm No Absolute Paths
```bash
rg -n "/Users/" wezterm/
```
Expected: no output

### lazy-lock.json Exists
```bash
test -f nvim/lazy-lock.json && echo "lazy-lock.json exists"
```
Expected: "lazy-lock.json exists"

### Starship Initialized
```bash
grep -n "starship init" zsh/custom.zsh
```
Expected: line with `eval "$(starship init zsh)"`

## Symlink Verification (After Install)

```bash
# Check deployed symlinks work
ls -la ~/.zshrc ~/.zshenv ~/.config/nvim ~/.config/tmux ~/.config/wezterm ~/.config/starship ~/.config/ranger
```

All should be symlinks pointing to this repo.
