### 目录
- [前置准备](#前置准备)
- [安装 AUR 助手 (yay)](#安装-aur-助手-yay)
- [官方仓库软件包清单](#官方仓库软件包清单)
- [一键生成命令 (pacman)](#一键生成命令-pacman)
- [AUR 软件包清单](#aur-软件包清单)
- [一键生成命令 (yay)](#一键生成命令-yay)
- [初始化与服务](#初始化与服务)
- [可选的 Docker 应用](#可选的-docker-应用)
- [环境配置](#环境配置)
- [快速验证](#快速验证)

### 前置准备
> [!TIP] 建议
> - 先同步镜像并安装构建工具：
>   - `sudo pacman -Syu`
>   - `sudo pacman -S --needed git base-devel`
> - Flatpak 建议添加 Flathub 源：
>   - `flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo`

### 安装 AUR 助手 (yay)

```bash
# https://github.com/Jguer/yay/
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

### 官方仓库软件包清单

> [!TIP] 如何使用
> - **维护**：要增删软件，只需在此表格中添加或删除行。

| 包名 (Package Name)             | Upstream URL                                               |
| ----------------------------- | ---------------------------------------------------------- |
| `neovim`                      | https://neovim.io/                                         |
| `xdg-desktop-portal-hyprland` | https://github.com/hyprwm/xdg-desktop-portal-hyprland      |
| `xdg-desktop-portal-gtk`      | https://github.com/flatpak/xdg-desktop-portal-gtk          |
| `waybar`                      | https://github.com/Alexays/Waybar/                         |
| `grim`                        | https://gitlab.freedesktop.org/emersion/grim               |
| `slurp`                       | https://github.com/emersion/slurp                          |
| `wl-clipboard`                | https://github.com/bugaevc/wl-clipboard                    |
| `noto-fonts-cjk`              | https://www.google.com/get/noto/                           |
| `ttf-font-awesome`            | https://fontawesome.com/                                   |
| `ttf-jetbrains-mono-nerd`     | https://github.com/ryanoasis/nerd-fonts                    |
| `fcitx5-im`                   | https://github.com/fcitx                                   |
| `fcitx5-rime`                 | https://github.com/fcitx/fcitx5-rime                       |
| `nvidia-utils`                | http://www.nvidia.com/                                     |
| `lib32-nvidia-utils`          | http://www.nvidia.com/                                     |
| `mesa-utils`                  | https://www.mesa3d.org/                                    |
| ``lib32-mesa-utils``          | http://mesa3d.sourceforge.net/                             |
| `ntfs-3g`                     | https://www.tuxera.com/community/open-source-ntfs-3g/      |
| `zellij`                      | https://archlinux.org/packages/extra/x86_64/zellij/        |
| `fzf`                         | https://github.com/junegunn/fzf                            |
| `jq`                          | https://jqlang.github.io/jq/                               |
| `zoxide`                      | https://github.com/ajeetdsouza/zoxide                      |
| `ripgrep`                     | https://github.com/BurntSushi/ripgrep                      |
| `bat`                         | https://github.com/sharkdp/bat                             |
| `lazygit`                     | https://github.com/jesseduffield/lazygit                   |
| `firefox`                     | https://www.mozilla.org/firefox/                           |
| `keepassxc`                   | https://keepassxc.org/                                     |
| `7zip`                        | https://www.7-zip.org/                                     |
| `flatpak`                     | https://flatpak.org/                                       |
| `bottom`                      | https://github.com/ClementTsang/bottom                     |
| `wireshark-cli`               | https://www.wireshark.org/                                 |
| `github-cli`                  | https://github.com/cli/cli                                 |
| `mpv`                         | https://mpv.io/                                            |
| `obs-studio`                  | https://obsproject.com/                                    |
| `yt-dlp`                      | https://github.com/yt-dlp/yt-dlp                           |
| `rustscan`                    | https://github.com/rustscan/RustScan                       |
| `scrcpy`                      | https://github.com/Genymobile/scrcpy                       |
| `prismlauncher`               | https://prismlauncher.org/                                 |
| `dust`                        | https://github.com/bootandy/dust                           |
| `okular`                      | https://apps.kde.org/okular/                               |
| `tigervnc`                    | https://www.tigervnc.org/                                  |
| `docker`                      | https://www.docker.com/                                    |
| `docker-compose`              | https://www.docker.com/                                    |
| `fish`                        | https://fishshell.com/                                     |
| `qemu-full`                   | https://www.qemu.org/                                      |
| `edk2-ovmf`                   | https://github.com/tianocore/tianocore.github.io/wiki/OVMF |
| `obsidian`                    | https://obsidian.md/                                       |
| `ollama-cuda`                 | https://github.com/ollama/ollama                           |
| `rpi-imager`                  | https://github.com/raspberrypi/rpi-imager                  |
| `npm`                         | https://www.npmjs.com/                                     |
| `rclone`                      | https://github.com/rclone/rclone                           |
| `noto-fonts-emoji`            | https://www.google.com/get/noto/                           |
| `swaybg`                      | https://github.com/swaywm/swaybg                           |
| `minicom`                     | https://salsa.debian.org/minicom-team/minicom              |
| `starship`                    | https://starship.rs/                                       |

### 一键生成命令 (pacman)

```dataviewjs
// 解析“官方仓库软件包清单”表格，生成 pacman 安装命令
const file = dv.current().file;
const content = await dv.io.load(file.path);
const lines = content.split('\n');

function collectPackagesAfterHeading(headingText) {
  const startIdx = lines.findIndex(l => l.trim().startsWith(headingText));
  if (startIdx === -1) return [];
  let inTable = false;
  const pkgs = [];
  for (let i = startIdx + 1; i < lines.length; i++) {
    const line = lines[i].trim();
    if (!inTable && line.startsWith('| ---')) { inTable = true; continue; }
    if (inTable) {
      if (!line.startsWith('|')) break; // 表格结束
      const parts = line.split('|').map(s => s.trim());
      if (parts.length > 2 && parts[1]) {
        const pkg = parts[1].replace(/`/g, '');
        if (pkg) pkgs.push(pkg);
      }
    }
    // 若遇到新的小节标题则提前终止
    if (!inTable && line.startsWith('### ')) break;
  }
  return pkgs;
}

const packages = collectPackagesAfterHeading('### 官方仓库软件包清单');
const command = `sudo pacman -Syu --needed ${packages.join(' ')}`;

dv.paragraph(`\n\n\`\`\`bash\n# 此命令由 Dataview 自动生成，与上方表格保持同步\n${command}\n\`\`\`\n`);
```

### AUR 软件包清单

| 包名 (Package Name)  | Upstream URL                              |
| ------------------ | ----------------------------------------- |
| `cursor-bin`       | https://www.cursor.com/                   |
| `envycontrol`      | https://github.com/bayasdev/envycontrol   |
| `espanso-wayland`  | https://github.com/espanso                |
| `subconverter-bin` | https://github.com/tindy2013/subconverter |

### 一键生成命令 (yay)

```dataviewjs
// 解析“AUR 软件包清单”表格，生成 yay 安装命令
const file2 = dv.current().file;
const content2 = await dv.io.load(file2.path);
const lines2 = content2.split('\n');

function collectAUR() {
  const startIdx = lines2.findIndex(l => l.trim().startsWith('### AUR 软件包清单'));
  if (startIdx === -1) return [];
  let inTable = false;
  const pkgs = [];
  for (let i = startIdx + 1; i < lines2.length; i++) {
    const line = lines2[i].trim();
    if (!inTable && line.startsWith('| ---')) { inTable = true; continue; }
    if (inTable) {
      if (!line.startsWith('|')) break;
      const parts = line.split('|').map(s => s.trim());
      if (parts.length > 2 && parts[1]) {
        const pkg = parts[1].replace(/`/g, '');
        if (pkg) pkgs.push(pkg);
      }
    }
    if (!inTable && line.startsWith('### ')) break;
  }
  return pkgs;
}

const aurPkgs = collectAUR();
const yayCmd = `yay -Syu --needed ${aurPkgs.join(' ')}`;

dv.paragraph(`\n\n\`\`\`bash\n# 此命令由 Dataview 自动生成，与上方表格保持同步\n${yayCmd}\n\`\`\`\n`);
```

### 初始化与服务

- [ ] Docker：开机自启并加入用户组
- [ ] Espanso：注册并启动服务
- [ ] Ollama：开机自启
- [ ] Fish：设置为默认 Shell

```bash
# Docker
sudo systemctl enable --now docker
sudo usermod -aG docker $USER

# Espanso
espanso service register
espanso service start

# Ollama
sudo systemctl enable --now ollama

# 默认 Shell 切换为 Fish
chsh -s /usr/bin/fish
```

> [!NOTE]
> 将用户加入 `docker` 组后需重新登录（或 `newgrp docker`）才会生效。
> 若使用 Compose 插件，也可安装 `docker-compose-plugin`。

### 可选的 Docker 应用
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

### 环境配置
[[配置STM32开发环境(Arch).md]]

### 快速验证
```bash
nvidia-smi || true
docker ps
espanso --version || true
yay --version
ollama --version || true
fish --version
```
