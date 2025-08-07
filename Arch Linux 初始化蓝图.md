### Arch Linux 软件包清单 (单一数据源)

> [!TIP] 如何使用
> - **维护**：要增删软件，只需在此表格中添加或删除行。
> - **执行**：需要安装时，将鼠标悬停在下方的“一键生成命令”代码块上，点击右上角的**刷新按钮**即可更新命令，然后复制。

| 包名 (Package Name)             | 描述                |
| ----------------------------- | ----------------- |
| `xdg-desktop-portal-hyprland` | Hyprland 的系统门户后端  |
| `xdg-desktop-portal-gtk`      | GTK 应用的系统门户       |
| `waybar`                      | Wayland 状态栏       |
| `grim slurp wl-clipboard`     | Wayland 截图与剪贴板    |
| `noto-fonts-cjk`              | Noto CJK 字体 (中日韩) |
| `ttf-font-awesome`            | 图标字体库             |
| `ttf-jetbrains-mono-nerd`     | Nerd Font 开发者字体   |
| `fcitx5-im fcitx5-rime`       | Rime 输入法 (Fcitx5) |
| `nvidia-utils`                | NVIDIA 闭源驱动       |
| `lib32-nvidia-utils`          | NVIDIA 驱动 (32位兼容) |
| `ntfs-3g`                     | NTFS 文件系统支持       |
| `ghostty`                     | GPU 加速终端          |
| `tmux`                        | 终端复用器             |
| `fzf`                         | 命令行模糊搜索           |
| `ripgrep`                     | 文件内容快速搜索          |
| `bat`                         | 带高亮的 `cat`        |
| `lazygit`                     | Git 终端 UI         |
| `firefox`                     | 火狐浏览器             |
| `obsidian`                    | 知识库与笔记软件          |
| `keepassxc`                   | 密码管理器             |
| `7zip`                        | 压缩工具              |
| `flatpak`                     | 应用沙盒与分发           |
| `htop`                        | 交互式进程查看器          |
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
# 如果刚修改完表格，请点击右上角刷新按钮更新
${command}
\`\`\`
`);
```