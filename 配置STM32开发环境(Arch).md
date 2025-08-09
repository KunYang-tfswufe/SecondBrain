通过 `yay` 安装 `stm32cubeide` 需要从 ST 官网手动下载两个文件，因为它们需要登录和同意协议。

### 1. 准备工作：手动下载

在运行 `yay` 命令前，先下载以下文件：

1.  **STM32CubeIDE for Linux**
    *   **下载页面**: [st.com/stm32cubeide](https://www.st.com/en/development-tools/stm32cubeide.html)
    *   **需要文件**: `en.st-stm32cubeide_..._amd64.sh.zip` (或类似名称的 `.zip` 包)
    *   **放置目录**: `~/.cache/yay/stm32cubeide/`

2.  **ST-LINK Server**
    *   **下载页面**: [st.com/st-link-server](https://www.st.com/en/development-tools/st-link-server.html)
    *   **需要文件**: `st-link-server-v...zip`
    *   **放置目录**: `~/.cache/yay/stlink-server/`

> [!TIP]
> 如果目录不存在，先运行一次 `yay -S stm32cubeide` 让它失败并创建目录，或者手动创建 (`mkdir -p ...`)。

### 2. 安装

将文件放置到正确位置后，执行安装命令：

```bash
yay -S stm32cubeide
```

### 3. 运行问题排查 (Wayland)

如果启动或显示异常，可修改桌面快捷方式的启动命令。

1.  **编辑文件**:
    ```bash
    sudo nano /usr/share/applications/stm32cubeide.desktop
    ```
2.  **修改内容**:
    *   注释掉当前使用的 `Exec=` 行 (在行首加 `#`)。
    *   取消另一条被注释的 `Exec=` 行的注释 (去掉行首的 `#`)。
3.  **应用更改**:
    ```bash
    sudo update-desktop-database
    ```