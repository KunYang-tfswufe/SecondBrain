ST 官网的软件包（如 CubeIDE, CubeProg）需要登录才能下载，因此 `yay` 无法自动完成。必须手动下载安装包，再进行安装。

> [!WARNING] 核心问题排查
> *   **`未找到文件 (not found)`**: 说明你忘了手动下载或放错位置。
> *   **`校验失败 (FAILED)`**: 说明你下载的**版本**与 AUR 包不匹配。请删除错误文件，重新下载 `PKGBUILD` 中指定的版本。

---

### 1. STM32CubeIDE (IDE)

**依赖**: `stlink-server` 也需要手动下载。

**步骤**:

1.  **准备文件**:
    *   **STM32CubeIDE**: 从 [st.com/stm32cubeide](https://www.st.com/en/development-tools/stm32cubeide.html) 下载 `.zip` 包，放入 `~/.cache/yay/stm32cubeide/`。
    *   **ST-LINK Server**: 从 [st.com/st-link-server](https://www.st.com/en/development-tools/st-link-server.html) 下载 `.zip` 包，放入 `~/.cache/yay/stlink-server/`。
      > [!TIP]
      > 如果目录不存在，可先运行一次安装命令让它失败并自动创建。

2.  **安装**:
    ```bash
    yay -S stm32cubeide
    ```

3.  **运行修复 (Wayland)**:
    *   若启动或显示异常，编辑桌面文件 `sudo nano /usr/share/applications/stm32cubeide.desktop`。
    *   切换 `Exec=` 命令的注释状态，然后运行 `sudo update-desktop-database` 应用更改。

---

### 2. STM32CubeProgrammer (烧录工具)

**步骤**:

1.  **准备文件**:
    *   从 [st.com/stm32cubeprog](https://www.st.com/en/development-tools/stm32cubeprog.html) 下载与 AUR 包版本匹配的 `.zip` 包。
    *   将其重命名为 `yay` 需要的文件名 (如 `en.stm32cubeprg-lin-v....zip`)，并放入 `~/.cache/yay/stm32cubeprog/`。

2.  **安装**:
    ```bash
    yay -S stm32cubeprog
    ```