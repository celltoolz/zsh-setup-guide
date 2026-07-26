# Switching to Zsh + Oh My Zsh Setup

Install and configure Zsh with Oh My Zsh, autosuggestions, zsh-completions, syntax highlighting, and fzf-tab.

## 1. Install System Packages

```bash
sudo apt update && sudo apt install -y zsh git curl fzf
```

## 2. Change Default Shell

```bash
chsh -s $(which zsh)
```

> **Note:** Log out and back in for this to take permanent effect. We will do this at the very end.

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

Open your configuration file using a text editor like Nano:

```bash
nano ~/.zshrc
```

### Update Plugins

Find the existing `plugins=(git)` line in the file. Replace it entirely with the block below.

> ⚠️ **Order matters:** You must add `fpath` above the plugins array, and `fzf-tab` must load before `zsh-syntax-highlighting` to avoid tab-completion conflicts.

```zsh
fpath=(${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-completions/src $fpath)

plugins=(
  git
  zsh-completions
  fzf-tab
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

### Set Theme (Optional)

Find the line `ZSH_THEME="robbyrussell"` and change it to your preferred theme. You can browse choices on the [Oh My Zsh themes wiki](https://github.com/ohmyzsh/ohmyzsh/wiki/themes).

```zsh
ZSH_THEME="alanpeabody"
```

(Save and close the file by pressing `Ctrl+O`, `Enter`, then `Ctrl+X`)

## 6. Finish

You must launch your new Zsh environment manually to initialize everything.

1. **Launch Zsh:**

   ```bash
   zsh
   ```

2. **Reload configuration** (if needed in the future):

   ```zsh
   source ~/.zshrc
   ```

3. **Log Out:** Close your terminal completely or log out of your system session and back in to finalize Zsh as your permanent default shell.
