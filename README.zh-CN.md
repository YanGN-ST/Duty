**[English](README.md) | 简体中文**

<p align="center">
  <img src="./assets/readme/hero-zh-v2.svg" width="100%" alt="Duty: 守住你的默认应用。">
</p>

为选定的文件扩展名守住默认应用。Duty 监测关联变化，在被更改后恢复，并记录变更历史。

## 功能与原理

- 只保护选定的扩展名，检测到关联变化后恢复。
- 按需清除单个文件的「始终打开方式」覆盖。
- 搜索内置文件类型目录，查看变更历史。支持开机启动和中英文界面。

Duty 监听 Launch Services 配置变化并定期检查，读取系统关联配置，通过系统 API 恢复关联。可选的 duti 只用于解析系统无法识别的扩展名。

## 安装

从 [Releases](https://github.com/YanGN-ST/Duty/releases) 下载 `Duty.dmg` 并拖入「应用程序」，或使用 Homebrew：

```sh
brew install --cask yangn-st/ygn/duty
```

需要 macOS 14 或更高版本。系统无法识别少见扩展名时，可选安装 [duti](https://github.com/moretension/duti)，多数用户不需要。

## 开始使用

1. 点击菜单栏的盾牌图标。
2. 添加文件类型并选择默认应用。
3. 打开该扩展名的锁定开关。

关闭窗口后保护继续运行，从菜单退出才会停止。

<details>
<summary>从源码构建</summary>

```sh
git clone https://github.com/YanGN-ST/Duty.git
cd Duty
./build_app.sh
open Duty.app
```

也可在 Xcode 中打开 Swift Package。

</details>

## 许可

[MIT](LICENSE)
