# kuikly-client

基于 **Kuikly** 跨平台框架构建的多端统一应用客户端工程。通过 Kotlin Multiplatform (KMP) 架构，实现业务逻辑与 UI 界面在 Android、iOS、HarmonyOS (鸿蒙)、H5 及微信小程序等多端的高效复用。

---

## 📁 目录结构

```text
kuikly-client/
├── .agents/                     # Antigravity 智能体技能规范
│   └── skills/
│       ├── kuikly-dsl/          # Kuikly 原生 DSL 开发规范
│       └── kuikly-compose-dsl/  # Kuikly Compose DSL 跨端规范
├── kuiklyDSL.mdc                # Kuikly 原生 DSL 规则与最佳实践
├── kuiklyComposeDSL.mdc         # Kuikly Compose DSL 规范与差异速查
└── language/                    # 跨端核心业务工程 (KMP)
    ├── shared/                  # 跨端通用核心模块 (commonMain 业务代码与页面定义)
    ├── androidApp/              # Android 原生宿主壳工程
    ├── iosApp/                  # iOS 原生宿主壳工程 (基于 CocoaPods 集成)
    ├── ohosApp/                 # HarmonyOS (鸿蒙 Next) 宿主壳工程
    ├── h5App/                   # H5 / Web 宿主与运行环境
    ├── miniApp/                 # 微信小程序端宿主工程
    └── buildSrc/                # Gradle 插件与版本依赖集中管理
```

---

## 🛠 开发环境与技术栈

| 组件 | 版本 / 要求 | 说明 |
| :--- | :--- | :--- |
| **Kuikly 核心** | 2.7.0 | 腾讯开源跨端渲染与动态化引擎 |
| **Kotlin** | 2.1.21 | 全平台共享业务与 UI 逻辑 |
| **JDK** | JDK 17 / 21 | 推荐使用 Android Studio 附带的 JBR |
| **Android AGP** | 7.4.2 | 搭配 R8 8.6.17+ 兼容 Kotlin 2.1 元数据 |
| **iOS 环境** | Xcode 14+ / CocoaPods 1.12+ | 用于编译打包 iOS 端共享库与 Pod |
| **HarmonyOS** | DevEco Studio 5.0+ | 用于鸿蒙工程构建与预览 |

---

## 🚀 常用命令与构建指引

进入主工程目录：
```bash
cd language
```

### 1. Android 端
- **编译 Debug APK**：
  ```bash
  ./gradlew :androidApp:assembleDebug
  ```
- **安装运行到设备**：
  ```bash
  ./gradlew :androidApp:installDebug
  ```

### 2. H5 / Web 端
- **构建 JS 产物**：
  ```bash
  ./gradlew :h5App:jsBrowserDevelopmentWebpack
  ```

### 3. iOS 端
在 `language/iosApp` 目录下执行：
```bash
pod install
```
随后使用 Xcode 打开 `language/iosApp/iosApp.xcworkspace` 运行。

---

## 📖 开发规范与指南

本工程包含详尽的跨端开发规范，开发时请参考：
* [Kuikly 原生 DSL 规范指南](.agents/skills/kuikly-dsl/SKILL.md)：涵盖 Flexbox 布局、状态管理 (`observable` / `vfor` / `vif`)、生命周期与内置组件。
* [Kuikly Compose DSL 规范指南](.agents/skills/kuikly-compose-dsl/SKILL.md)：涵盖 Compose API 差异、包名引用规范、手势状态绑定与嵌套滚动等最佳实践。
