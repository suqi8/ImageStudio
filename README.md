# ImageStudio

<div align="center">

**一个基于 Compose Multiplatform 的跨平台 ROM 定制工具**

[![Kotlin](https://img.shields.io/badge/Kotlin-2.1.0-blue.svg?logo=kotlin)](http://kotlinlang.org)
[![Compose Multiplatform](https://img.shields.io/badge/Compose%20Multiplatform-1.7.1-blue)](https://github.com/JetBrains/compose-multiplatform)
[![License](https://img.shields.io/badge/License-Private-red.svg)](LICENSE)

</div>

## 📖 项目简介

ImageStudio 是一个功能强大的 ROM 定制工具，支持 Android 和桌面平台（Windows、macOS、Linux）。使用 Kotlin Multiplatform 和 Compose Multiplatform 技术栈构建，提供统一的用户体验和现代化的 UI 设计。

### ✨ 核心特性

- 🎨 **现代化 UI** - 基于 MIUIX KMP 设计系统，提供流畅的用户体验
- 🔄 **跨平台支持** - 一套代码，支持 Android、Windows、macOS、Linux
- 📁 **项目管理** - 创建、重命名、删除 ROM 项目
- 🛠️ **工作台** - 完整的 ROM 定制工作流程
- ⚙️ **设置中心** - 外观、高级设置等配置选项
- 🌍 **国际化** - 支持中文和英文界面

## 🚀 技术栈

### 核心框架
- **Kotlin Multiplatform** - 跨平台代码共享
- **Compose Multiplatform** - 声明式 UI 框架
- **Voyager** - 导航和状态管理
- **Koin** - 依赖注入

### UI 组件
- **MIUIX KMP** - MIUI 风格的 Compose 组件库
- **Material Icons** - 图标库

### 构建工具
- **Gradle** - 构建系统
- **ProGuard** - Android 代码混淆

## 📦 下载安装

### 系统要求

#### Android
- Android 8.0 (API 26) 或更高版本
- **需要 Root 权限**

#### Windows
- Windows 10/11 (64-bit)
- 无需额外依赖

#### macOS
- macOS 11.0 或更高版本
- Apple Silicon 和 Intel 芯片均支持

#### Linux
- 64-bit Linux 发行版
- 无需额外依赖

### 安装方式

1. 前往 [Releases](https://github.com/suqi8/ImageStudio-Builds/releases) 页面
2. 下载对应平台的安装包：
   - Android: `ImageStudio-android-v*.apk`
   - Windows: `ImageStudio-windows-v*.msi`
   - macOS: `ImageStudio-macos-v*.dmg`
   - Linux: `ImageStudio-linux-v*.deb`
3. 按照系统提示安装

## 📱 使用指南

### 首次启动

1. **Android 用户**：首次启动时会请求 Root 权限，请授予权限以确保功能正常
2. **桌面用户**：直接启动即可使用

### 主要功能

#### 1. 项目管理（工作区）

- **创建项目**：点击"新建项目"卡片，输入项目名称
- **打开项目**：点击项目卡片进入工作台
- **重命名项目**：长按项目卡片 → 选择"重命名"
- **删除项目**：长按项目卡片 → 选择"删除"

#### 2. ROM 工作台

进入项目后，可以进行以下操作：
- 解包 ROM 镜像
- 编辑系统文件
- 重新打包镜像
- 查看操作日志

#### 3. 设置

从"关于"页面进入设置，可配置：
- **外观设置**：主题、语言等
- **高级设置**：日志级别、缓存管理等

## 🛠️ 开发指南

### 环境准备

1. **JDK 17** 或更高版本
2. **Android Studio** (推荐 Hedgehog 或更新版本)
3. **Kotlin 2.1.0**

### 克隆项目

```bash
git clone https://github.com/suqi8/ImageStudio.git
cd ImageStudio
```

### 构建项目

#### Android
```bash
./gradlew assembleDebug
```

#### Desktop (当前平台)
```bash
./gradlew runDistributable
```

#### 打包所有平台
```bash
./gradlew packageDistributionForCurrentOS  # 当前系统
./gradlew packageReleaseApk                # Android
```

### 项目结构

```
ImageStudio/
├── composeApp/                 # 主应用模块
│   ├── src/
│   │   ├── commonMain/        # 跨平台共享代码
│   │   │   ├── kotlin/
│   │   │   │   └── com/suqi8/imagestudio/
│   │   │   │       ├── core/           # 核心功能
│   │   │   │       ├── feature/        # 功能模块
│   │   │   │       │   ├── about/      # 关于页面
│   │   │   │       │   ├── main/       # 主页面（底部导航）
│   │   │   │       │   ├── settings/   # 设置页面
│   │   │   │       │   ├── workbench/  # 工作台
│   │   │   │       │   └── workshop/   # 项目管理
│   │   │   │       └── di/             # 依赖注入
│   │   │   └── composeResources/       # 资源文件
│   │   ├── androidMain/       # Android 特定代码
│   │   └── jvmMain/           # Desktop 特定代码
│   └── build.gradle.kts
├── .github/
│   └── workflows/
│       └── build.yml          # CI/CD 配置
└── build.gradle.kts
```

### 代码规范

- 使用 Kotlin 官方代码风格
- 遵循 MVVM 架构模式
- 使用 Voyager 进行导航管理
- 使用 Koin 进行依赖注入

## 🔧 CI/CD

项目使用 GitHub Actions 进行自动化构建和发布：

- **自动构建**：每次推送到 `main` 分支时触发
- **多平台打包**：自动构建 Android、Windows、macOS、Linux 版本
- **自动发布**：构建产物自动发布到 [ImageStudio-Builds](https://github.com/suqi8/ImageStudio-Builds) 仓库
- **版本管理**：基于 Git commit 数量自动生成版本号

详见 [CI/CD 文档](.github/CI_CD_README.md)

## 📄 开源协议

本项目为私有项目，未开源。

## 👨‍💻 作者

**酸奶 (suqi8)**

- GitHub: [@suqi8](https://github.com/suqi8)

## 🙏 致谢

- [Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform) - JetBrains 的跨平台 UI 框架
- [MIUIX KMP](https://github.com/miuix-kotlin-multiplatform/miuix) - MIUI 风格的 Compose 组件库
- [Voyager](https://github.com/adrielcafe/voyager) - Compose Multiplatform 导航库
- [Koin](https://insert-koin.io/) - Kotlin 依赖注入框架

## 📮 反馈与支持

如遇到问题或有功能建议，请在 [Issues](https://github.com/suqi8/ImageStudio/issues) 页面提交。

---

<div align="center">
Made with ❤️ using Compose Multiplatform
</div>
