### Arch Linux 软件包清单 (单一数据源)

> [!TIP] 如何使用
> - **维护**：要增删软件，只需在此表格中添加或删除行。

| 包名 (Package Name)             | Upstream URL                                          | 描述                                                           |
| ----------------------------- | ----------------------------------------------------- | ------------------------------------------------------------ |
| `xdg-desktop-portal-hyprland` | https://github.com/hyprwm/xdg-desktop-portal-hyprland | Hyprland 的 XDG 桌面门户后端，用于处理屏幕截图、文件选择等沙盒应用的权限请求。               |
| `xdg-desktop-portal-gtk`      | https://github.com/flatpak/xdg-desktop-portal-gtk     | GTK 应用的 XDG 桌面门户后端，为 GTK 程序提供文件选择、打开 URI 等原生对话框。             |
| `waybar`                      | https://github.com/Alexays/Waybar/                    | 一款为 Wayland 合成器（如 Hyprland）设计的高度可定制的状态栏。                     |
| `grim`                        | https://gitlab.freedesktop.org/emersion/grim          | Wayland 环境下的截图工具，可以抓取整个屏幕或特定输出。常与 slurp 配合使用。                |
| `slurp`                       | https://github.com/emersion/slurp                     | 用于在 Wayland 中交互式地选择屏幕上的一个区域，常作为 grim 等工具的输入。                 |
| `wl-clipboard`                | https://github.com/bugaevc/wl-clipboard               | Wayland 环境下的命令行剪贴板工具，提供 wl-copy 和 wl-paste 命令。               |
| `noto-fonts-cjk`              | https://www.google.com/get/noto/                      | Google Noto CJK 字体，确保中日韩字符能够被正确渲染，避免乱码。                      |
| `ttf-font-awesome`            | https://fontawesome.com/                              | 一款流行的图标字体库，常用于状态栏、脚本和各种 UI 界面中显示图标。                          |
| `ttf-jetbrains-mono-nerd`     | https://github.com/ryanoasis/nerd-fonts               | JetBrains Mono 字体的 "Nerd Font" 魔改版，集成了大量图标，非常适合在终端和代码编辑器中使用。 |
| `fcitx5-im`                   | https://github.com/fcitx                              | Fcitx5 输入法框架，一个灵活且可扩展的输入法平台。                                 |
| `fcitx5-rime`                 | https://github.com/fcitx/fcitx5-rime                  | 基于 Fcitx5 的 Rime 输入法引擎，以其高度的可定制性而闻名。                         |
| `nvidia-utils`                | http://www.nvidia.com/                                | NVIDIA 闭源显卡驱动程序和核心工具。                                        |
| `lib32-nvidia-utils`          | http://www.nvidia.com/                                | 为 32 位应用程序（如部分 Steam 游戏）提供 NVIDIA 驱动的兼容库。                    |
| `lib32-mesa-utils`            | http://mesa3d.sourceforge.net/                        | Mesa 3D 图形库的 32 位版本，为 32 位应用提供图形支持。                          |
| `mesa-utils`                  | https://www.mesa3d.org/                               | 开源 3D 图形库 (Mesa) 的实用工具，通常用于测试和获取 OpenGL/Vulkan 信息。           |
| `ntfs-3g`                     | https://www.tuxera.com/community/open-source-ntfs-3g/ | 用于在 Linux 系统下安全地读写 Windows NTFS 文件系统的驱动。                     |
| `tmux`                        | https://github.com/tmux/tmux/wiki                     | 终端复用器，允许在一个终端窗口中创建和管理多个会话、窗口和窗格。                             |
| `fzf`                         | https://github.com/junegunn/fzf                       | 一款速度极快的交互式命令行模糊搜索工具，可用于查找文件、历史命令等。                           |
| `ripgrep`                     | https://github.com/BurntSushi/ripgrep                 | 一款以行为单位进行递归搜索的工具，性能远超 grep。                                  |
| `bat`                         | https://github.com/sharkdp/bat                        | cat 命令的替代品，增加了语法高亮、Git 集成和行号显示等功能。                           |
| `lazygit`                     | https://github.com/jesseduffield/lazygit              | 一个简单的 Git 命令终端 UI，让你更直观地进行版本控制操作。                            |
| `firefox`                     | https://www.mozilla.org/firefox/                      | 广受欢迎的开源网页浏览器。                                                |
| `obsidian`                    | https://obsidian.md/                                  | 一款基于本地 Markdown 文件的知识库和笔记软件，以其强大的双向链接功能著称。                   |
| `keepassxc`                   | https://keepassxc.org/                                | 开源、跨平台的密码管理器，将密码安全地存储在本地数据库中。                                |
| `7zip`                        | https://www.7-zip.org/                                | 一款高压缩率的文件归档工具，支持多种压缩格式。                                      |
| `flatpak`                     | https://flatpak.org/                                  | 一种应用程序沙盒和分发技术，允许用户安全地安装和运行跨发行版的应用。                           |
| `htop`                        | https://htop.dev/                                     | top 命令的增强版，一个彩色的、交互式的系统进程查看器。                                |
| `wireshark-cli`               | https://www.wireshark.org/                            | 网络协议分析器 Wireshark 的命令行版本 (tshark)，用于捕获和分析网络数据包。              |
| `github-cli`                  | https://github.com/cli/cli                            | GitHub 官方命令行工具，可直接在终端中管理仓库、Issues 和 PR 等。                    |
| `mpv`                         | https://mpv.io/                                       | 一款极简但功能强大的自由开源媒体播放器，可通过命令行或配置文件高度定制。                         |
| `obs-studio`                  | https://obsproject.com/                               | 免费开源的视频录制和直播软件，功能强大且高度可配置。                                   |
| `yt-dlp`                      | https://github.com/yt-dlp/yt-dlp                      | youtube-dl 的一个活跃分支，功能更强大的在线视频下载工具。                           |
| `nmap`                        | https://nmap.org/                                     | 强大的网络探测和安全审计工具，用于网络发现和端口扫描                                   |
| `scrcpy`                      | https://github.com/Genymobile/scrcpy                  | 通过 USB 或 Wi-Fi 显示和控制安卓设备的工具，无需在手机上安装任何应用。                    |
| `prismlauncher`               | https://prismlauncher.org/                            | 一款功能丰富的开源 Minecraft 启动器，方便管理不同版本的游戏、模组和账户。                   |
| `dust`                        | https://github.com/bootandy/dust                      | du 命令的替代品，能更直观地分析和显示磁盘空间使用情况。                                |
| `okular`                      | https://apps.kde.org/okular/                          | KDE 出品的通用文档查看器，支持 PDF、EPub、Chm 等多种格式。                        |
| `copyq`                       | https://github.com/hluk/copyq                         | 功能强大的高级剪贴板管理器，支持历史记录、搜索、编辑和脚本功能。                             |
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