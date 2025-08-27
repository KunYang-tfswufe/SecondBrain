### Prerequisites

> [!TIP] 建议
>
> - 先同步镜像并安装构建工具：
>   - `sudo pacman -Syu`
>   - `sudo pacman -S --needed git base-devel`
> - Flatpak 建议添加 Flathub 源：
>   - `flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`

### Install AUR Helper (yay)

```bash
# https://github.com/Jguer/yay/
# 安装依赖、克隆、构建、安装，然后清理残留文件夹
sudo pacman -S --needed git base-devel && \
git clone https://aur.archlinux.org/yay.git && \
cd yay && \
makepkg -si && \
cd .. && \
rm -rf yay
```

### Official Repository Package List

```bash
sudo pacman -Syu --needed cockpit neovim openssh xdg-desktop-portal-hyprland xdg-desktop-portal-gtk waybar grim slurp wl-clipboard noto-fonts-cjk ttf-font-awesome ttf-jetbrains-mono-nerd fcitx5-im fcitx5-rime nvidia-utils lib32-nvidia-utils mesa-utils lib32-mesa-utils ntfs-3g zellij fzf jq zoxide ripgrep bat lazygit firefox keepassxc 7zip flatpak bottom wireshark-cli github-cli mpv obs-studio yt-dlp rustscan scrcpy prismlauncher dust okular tigervnc docker docker-compose fish qemu-full edk2-ovmf ollama-cuda rpi-imager npm rclone noto-fonts-emoji swaybg minicom starship stow kitty dolphin wofi playerctl brightnessctl clang dunst wireplumber pipewire pipewire-pulse pipewire-alsa alsa-utils sof-firmware veracrypt ffmpeg unzip wget cronie glow
```

### AUR Package List

| 包名 (Package Name)              | Upstream URL                              |
| -------------------------------- | ----------------------------------------- |
| `cursor-bin`                     | https://www.cursor.com/                   |
| `envycontrol`                    | https://github.com/bayasdev/envycontrol   |
| `espanso-wayland`                | https://github.com/espanso                |
| `subconverter-bin`               | https://github.com/tindy2013/subconverter |
| `zen-browser-bin`                | https://github.com/zen-browser/desktop    |
| `intellij-idea-ultimate-edition` | https://www.jetbrains.com/idea/           |

### Other Package

```bash
# prettier
sudo npm install -g prettier

# gemini-cli
npm install -g @google/gemini-cli

# cursor-cli
curl https://cursor.com/install -fsS | bash
```

### Initialization and Services

```bash
# cockpit
sudo systemctl enable --now cockpit.socket

# Docker
sudo systemctl enable --now docker
sudo usermod -aG docker $USER

# Espanso
espanso service register
espanso service start

# Ollama
sudo systemctl enable --now ollama

# SSH
sudo systemctl start sshd
sudo systemctl enable sshd

# 默认 Shell 切换为 Fish
chsh -s /usr/bin/fish
```

> [!NOTE]
> 将用户加入 `docker` 组后需重新登录（或 `newgrp docker`）才会生效。
> 若使用 Compose 插件，也可安装 `docker-compose-plugin`。

### Optional Docker Applications

```bash
# AnythingLLM
docker pull mintplexlabs/anythingllm
docker run -d --restart always -p 3001:3001 mintplexlabs/anythingllm

# Open WebUI
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data --name open-webui --restart always \
  ghcr.io/open-webui/open-webui:main

# rembg server
docker run -d --restart always -p 7000:7000 danielgatis/rembg s --host 0.0.0.0 --port 7000
```
