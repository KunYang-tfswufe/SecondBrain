### Arch Linux 软件包清单 (单一数据源)

> [!TIP] 如何使用
> - **维护**：要增删软件，只需在此表格中添加或删除行。

| 包名 (Package Name)             | Upstream URL                                          | 描述                     |
| ----------------------------- | ----------------------------------------------------- | ---------------------- |
| `xdg-desktop-portal-hyprland` | https://github.com/hyprwm/xdg-desktop-portal-hyprland | Hyprland 的系统门户后端       |
| `xdg-desktop-portal-gtk`      | https://github.com/flatpak/xdg-desktop-portal-gtk     | GTK 应用的系统门户            |
| `waybar`                      | https://github.com/Alexays/Waybar/                    | Wayland 状态栏            |
| `grim`                        | https://gitlab.freedesktop.org/emersion/grim          | Wayland 的截图工具          |
| `slurp`                       | https://github.com/emersion/slurp                     | 在 Wayland 中选择一个区域      |
| `wl-clipboard`                | https://github.com/bugaevc/wl-clipboard               | 用于 Wayland 的命令行复制/粘贴工具 |
| `noto-fonts-cjk`              | https://www.google.com/get/noto/                      | Noto CJK 字体 (中日韩)      |
| `ttf-font-awesome`            | https://fontawesome.com/                              | 图标字体库                  |
| `ttf-jetbrains-mono-nerd`     | https://github.com/ryanoasis/nerd-fonts               | Nerd Font 开发者字体        |
| `fcitx5-im`                   | https://github.com/fcitx                              | Fcitx5                 |
| `fcitx5-rime`                 | https://github.com/fcitx/fcitx5-rime                  | Rime 输入法 (Fcitx5)      |
| `nvidia-utils`                | http://www.nvidia.com/                                | NVIDIA 闭源驱动            |
| `lib32-nvidia-utils`          | http://www.nvidia.com/                                | NVIDIA 驱动 (32位兼容)      |
| `ntfs-3g`                     | https://www.tuxera.com/community/open-source-ntfs-3g/ | NTFS 文件系统支持            |
| `tmux`                        | https://github.com/tmux/tmux/wiki                     | 终端复用器                  |
| `fzf`                         | https://github.com/junegunn/fzf                       | 命令行模糊搜索                |
| `ripgrep`                     | https://github.com/BurntSushi/ripgrep                 | 文件内容快速搜索               |
| `bat`                         | https://github.com/sharkdp/bat                        | 带高亮的 `cat`             |
| `lazygit`                     | https://github.com/jesseduffield/lazygit              | Git 终端 UI              |
| `firefox`                     | https://www.mozilla.org/firefox/                      | 火狐浏览器                  |
| `obsidian`                    | https://obsidian.md/                                  | 知识库与笔记软件               |
| `keepassxc`                   | https://keepassxc.org/                                | 密码管理器                  |
| `7zip`                        | https://www.7-zip.org/                                | 压缩工具                   |
| `flatpak`                     | https://flatpak.org/                                  | 应用沙盒与分发                |
| `htop`                        | https://htop.dev/                                     | 交互式进程查看器               |
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