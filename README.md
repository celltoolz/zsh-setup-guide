# Switching to Zsh + Oh My Zsh Setup
Install and configure Zsh with Oh My Zsh, autosuggestions, syntax highlighting, and fzf-tab.

## 1. Install System Packages
```bash
sudo apt update && sudo apt install -y zsh git curl fzf
```

## 2. Change Default Shell
```bash
chsh -s $(which zsh)
```
*(Log out and back in for this to take effect.)*

## 3. Install Oh My Zsh
```bash
sh -c "$(curl -fsSL https://install.ohmyz.sh)" "" --unattended
```

## 4. Install Plugins

**Autosuggestions:**
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

**ZSH Completions:**
```bash
git clone https://github.com/zsh-users/zsh-completions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions
```

**Syntax Highlighting:**
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

**fzf-tab:**
```bash
git clone https://github.com/Aloxaf/fzf-tab ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-tab
```

## 5. Configure `.zshrc`

**Plugins** — ⚠️ `fzf-tab` must load **before** `zsh-syntax-highlighting` to avoid tab-completion conflicts:
```bash
plugins=(
  git
  zsh-completions
  fzf-tab
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

**Theme** — pick one from the [Oh My Zsh themes wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/themes) and set `ZSH_THEME` accordingly.
```bash
ZSH_THEME="alanpeabody"
```


