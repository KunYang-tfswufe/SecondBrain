### Arch Linux 软件包清单 (单一数据源)

> [!TIP] 如何使用
> - **维护**：要增删软件，只需在此表格中添加或删除行。

| 包名 (Package Name)             | Upstream URL                                          |
| ----------------------------- | ----------------------------------------------------- |
| `xdg-desktop-portal-hyprland` | https://github.com/hyprwm/xdg-desktop-portal-hyprland |
| `xdg-desktop-portal-gtk`      | https://github.com/flatpak/xdg-desktop-portal-gtk     |
| `waybar`                      | https://github.com/Alexays/Waybar/                    |
| `grim`                        | https://gitlab.freedesktop.org/emersion/grim          |
| `slurp`                       | https://github.com/emersion/slurp                     |
| `wl-clipboard`                | https://github.com/bugaevc/wl-clipboard               |
| `noto-fonts-cjk`              | https://www.google.com/get/noto/                      |
| `ttf-font-awesome`            | https://fontawesome.com/                              |
| `ttf-jetbrains-mono-nerd`     | https://github.com/ryanoasis/nerd-fonts               |
| `fcitx5-im`                   | https://github.com/fcitx                              |
| `fcitx5-rime`                 | https://github.com/fcitx/fcitx5-rime                  |
| `nvidia-utils`                | http://www.nvidia.com/                                |
| `lib32-nvidia-utils`          | http://www.nvidia.com/                                |
| `mesa-utils`                  | https://www.mesa3d.org/                               |
| `lib32-mesa-utils`            | http://mesa3d.sourceforge.net/                        |
| `ntfs-3g`                     | https://www.tuxera.com/community/open-source-ntfs-3g/ |
| `zellij`                      | https://archlinux.org/packages/extra/x86_64/zellij/   |
| `fzf`                         | https://github.com/junegunn/fzf                       |
| `ripgrep`                     | https://github.com/BurntSushi/ripgrep                 |
| `bat`                         | https://github.com/sharkdp/bat                        |
| `lazygit`                     | https://github.com/jesseduffield/lazygit              |
| `firefox`                     | https://www.mozilla.org/firefox/                      |
| `obsidian`                    | https://obsidian.md/                                  |
| `keepassxc`                   | https://keepassxc.org/                                |
| `7zip`                        | https://www.7-zip.org/                                |
| `flatpak`                     | https://flatpak.org/                                  |
| `bottom`                      | https://github.com/ClementTsang/bottom                |
| `wireshark-cli`               | https://www.wireshark.org/                            |
| `github-cli`                  | https://github.com/cli/cli                            |
| `mpv`                         | https://mpv.io/                                       |
| `obs-studio`                  | https://obsproject.com/                               |
| `yt-dlp`                      | https://github.com/yt-dlp/yt-dlp                      |
| `nmap`                        | https://nmap.org/                                     |
| `scrcpy`                      | https://github.com/Genymobile/scrcpy                  |
| `prismlauncher`               | https://prismlauncher.org/                            |
| `dust`                        | https://github.com/bootandy/dust                      |
| `okular`                      | https://apps.kde.org/okular/                          |
| `copyq`                       | https://github.com/hluk/copyq                         |
### 一键生成命令 (动态更新)

```dataviewjs
// 这个脚本会自动读取上面表格中的第一列，并生成 pacman 命令
const file = dv.current().file;
const content = await dv.io.load(file.path);
const lines = content.split('\n');

let packages = [];
let inTable = false;

for (const line of lines) {
    if (line.trim().startsWith('| ---')) {
        inTable = true;
        continue;
    }
    if (inTable && line.trim().startsWith('|')) {
        const parts = line.split('|').map(s => s.trim());
        if (parts.length > 2 && parts[1]) {
            // 从 `包名` 中提取纯文本
            const pkgName = parts[1].replace(/`/g, '');
            packages.push(pkgName);
        }
    }
}

const command = `sudo pacman -Syu --needed ${packages.join(' ')}`;

dv.paragraph(`
\`\`\`bash
# 此命令由 Dataview 自动生成，与上方表格保持同步
${command}
\`\`\`
`);
```