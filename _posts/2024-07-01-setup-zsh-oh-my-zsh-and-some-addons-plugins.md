---
layout: post
title: Setup ZSH, oh-my-zsh and some addons/plugins
date: 2024-07-01 11:53 +0200
---

Unter Debian 12.6 soll die Shell ZSH mit dem Framework oh-my-zsh, dem fuzzy finder FZF und derm Theme Powerlevel10k installiert werden. Im Anschluss werden die wichtigsten Plugins für das Framework oh-my-ush installiert.

### ZSH installieren

Am Anfang wird ZSH für alle Benutzer installiert:

```bash
sudo apt update
sudo apt install zsh -y
```

### Oh-My-Zsh installieren

Im Anschluss wird das Framework Oh-My-Zsh installiert:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Powerlevel10k Theme installieren

Für die Installation des Powerlevel10k Themes müssen folgende Schritte ausgeführt werden:

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Danach muss die Verwendung des Themes in der Datei .zshrc eingetragen werden:

```bash
sed -i 's/ZSH_THEME=".*"/ZSH_THEME="powerlevel10k\/powerlevel10k"/' ~/.zshrc
```

### FZF installieren

Der fuzzy finder FZF wird installiert:

```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### Plugins für Oh-My-Zsh installieren

Die wichtigsten Plugins werden installiert:

```bash
# Plugin-Verzeichnis erstellen
mkdir -p ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins

# zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# you-should-use
git clone https://github.com/MichaelAquilina/zsh-you-should-use ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/you-should-use

# zsh-bat
git clone https://github.com/fdellwing/zsh-bat.git $ZSH_CUSTOM/plugins/zsh-bat

# fast-syntax-highlighting
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting

# fzf-tab
git clone https://github.com/Aloxaf/fzf-tab ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-tab

# zsh-history-substring-search
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search

# zsh-autocomplete
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autocomplete
```

### Plugins aktivieren

Um die installierten Plugins zu aktivieren, muss die Datei .zshrc bearbeitet werden:

```bash
sed -i 's/plugins=(.*)/plugins=(fast-syntax-highlighting sudo fzf-tab docker docker-compose git you-should-use zsh-autosuggestions zsh-bat zsh-syntax-highlighting zsh-history-substring-search web-search z)/' ~/.zshrc
```

### Installation von bat als Ersatz für cat

```bash
sudo apt install bat
mkdir -p ~/.local/bin
ln -s /usr/bin/batcat ~/.local/bin/bat
```

### Installation von EXA als Erweiterung von ls

```bash
sudo apt install exa
touch $ZSH_CUSTOM/aliases.zsh
echo 'alias list="exa -l -a -h -g --octal-permissions"' >> $ZSH_CUSTOM/aliases.zsh
```

### ZSH als Standard-Shell festlegen

```bash
chsh -s $(which zsh)
```

### Benutzer-Shell aktualisieren

```bash
sudo usermod -s /usr/bin/zsh <username>
```

### ZSH-Konfiguration für alle (neuen) Benutzer

```bash
sudo cp ~/.zshrc /etc/skel/.zshrc
```

### System aktualisieren und abschliessen

```bash
sudo apt upgrade -y
source ~/.zshrc
```

