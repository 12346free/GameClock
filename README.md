# GameClock
    **Game Clock** 是一款专为 Windows 游戏玩家打造的轻量级桌面与游戏悬浮时钟工具。

    采用 **Win32 GDI 分层窗口 + QPainter 内存渲染** 混合引擎，完全**不注入进程、不挂钩
  API、不读写游戏内存**。完美解决《赛博朋克 2077》等 DirectX 12 / DirectFlip
  游戏在全屏、无边框窗口化下传统置顶悬浮窗失效或闪烁的问题。

    ---

    ## ✨ 核心特性

    - 🛡️ **100% 反作弊安全**：纯 Win32 API 窗口管辖，0 内存读写、0 注入/Hook，无惧 EAC、BattlEye、Vanguard
  等严苛反作弊系统。
    - 🎯 **完美兼容 DX11/DX12/Vulkan 游戏**：实测支持《赛博朋克 2077》、《永劫无间》、《Apex
  英雄》等游戏在**独占全屏、无边框窗口化、窗口化**模式下稳定置顶。
    - 🎨 **10 种精美预设样式**：内置 4 种 **Material Design**（Indigo, Dark, Teal, You Purple）以及 Cyberpunk
  Neon、Synthwave、Minimal Dark 等多种风格。
    - ⚙️ **高度可定制外观**：支持自定义字体、字号、文本颜色、渐变背景、圆角半径、边框宽度、文字阴影及透明度。
    - 🔒 **一键快捷锁定与点击穿透**：支持快捷键 `Ctrl + Alt + G` 随时锁定/解锁位置。锁定后开启 `WS_EX_TRANSPARENT`
  点击穿透，绝不干扰游戏操作。
    - 📍
  **快捷位置预设与自由拖拽**：解锁状态下鼠标左键直接拖拽移动，或在设置中一键对齐至屏幕“左上”、“右上”、“居中”等常用位置
  。
    - 💻 **资源占用极低**：原生 Win32 事件循环与 UpdateLayeredWindow 合成，CPU/内存占用微乎其微。

    ---

    ## 📸 预设样式一览

    | 预设名称 | 风格特点 |
    | :--- | :--- |
    | **Material Indigo** | 经典 Material Design 靛蓝渐变圆角卡片 |
    | **Material Dark** | 深色优雅 Material 风格 |
    | **Material Teal** | 清爽青绿 Material 主题 |
    | **Material You Purple** | 现代 Material You 动态紫色圆角 |
    | **Cyberpunk Neon** | 赛博朋克荧光绿黑客风格 |
    | **Synthwave** | 霓虹复古浪潮霓虹紫 |
    | **Minimal Light / Dark** | 极简白 / 极简黑 |
    | **Retro Terminal** | 经典终端复古绿字 |
    | **Ocean Deep** | 深海湛蓝风格 |

    ---

    ## 🎮 操作快捷键

    | 操作 | 触发方式 |
    | :--- | :--- |
    | **移动位置** | 悬浮窗未锁定状态下，**鼠标左键拖拽** |
    | **打开设置** | 悬浮窗未锁定状态下 **右键点击** 或 **双击系统托盘图标** |
    | **切换锁定 / 穿透** | **全局快捷键 `Ctrl + Alt + G`** 或托盘菜单勾选 |
    | **快速换色** | 右键托盘图标 → `快速换色` |

    ---

    ## 🛡️ 安全与反作弊说明

    许多游戏重叠层（Overlay）由于采用 DLL 注入（如 Hook DirectX `Present` 函数）容易被反作弊软件误封。

    **Game Clock** 采用独立的 **Desktop Layered Window Overlay** 机制：
    1. **独立进程运行**：与游戏进程彻底隔离。
    2. **零内存接触**：不使用 `OpenProcess`、`WriteProcessMemory` 或 `CreateRemoteThread`。
    3. **原生 Win32 合成**：依靠 Windows 系统 DWM (Desktop Window Manager) 进行层叠渲染。

    *提示：在极少数禁用“全屏优化”的独占全屏游戏中，建议将游戏显示模式切换为**无边框窗口化（Borderless
  Windowed）**以获得最佳置顶体验。*

    ---

    ## 📦 安装与运行

    ### 方式一：直接运行独立单文件 (.exe)
    无需安装 Python 环境，在 Release 页面下载 `GameClock.exe` 后双击即可运行。

    ### 方式二：通过 Python 源码运行

    #### 环境要求
    - Windows 10 / 11
    - Python 3.8+
    - PyQt5

    ```bash
    # 1. 克隆仓库
    git clone https://github.com/your-username/Game-Clock.git
    cd Game-Clock

    # 2. 安装依赖
    pip install PyQt5

    # 3. 运行程序
    python game_clock.py
    ──────
  ## 🛠️ 打包为 .exe

  如需自行打包为独立单文件可执行程序，可以使用 PyInstaller：

    # 安装 PyInstaller
    pip install pyinstaller

    # 一键打包
    pyinstaller --onefile --windowed --noconsole --name "GameClock" --icon "0.ico" --add-data "0.ico;." game_clock.py

  打包成功后，单文件程序将生成在 dist/GameClock.exe。
  ──────
  ## 📄 开源协议

  本项目基于 MIT License /LICENSE 开源。欢迎 Star、Fork 与提交 Pull Request！
