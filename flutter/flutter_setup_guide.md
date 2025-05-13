# Flutter 安装和环境配置指南

## 一、安装

### 1. 安装 VSCode 插件

- Flutter
- Dart
- Flutter Widget Snippets
- Android iOS Emulator

### 2. 新建 Flutter 项目

使用快捷键：

```
Ctrl + Shift + P -> Flutter: New Project
```

根据提示从 Git 拉取或加载本地 SDK。

### 3. 检查环境

```bash
flutter doctor
```

### 4. 安装 Android Studio

---

## 二、配置系统变量

- `FLUTTER_GIT_URL`：`https://mirrors.tuna.tsinghua.edu.cn/git/flutter-sdk.git`
- `FLUTTER_STORAGE_BASE_URL`：`https://mirrors.tuna.tsinghua.edu.cn/flutter`
- `PUB_HOSTED_URL`：`https://mirrors.tuna.tsinghua.edu.cn/dart-pub` 或 `https://pub.flutter-io.cn`
- 配置系统变量 `PATH`：
  ```
  F:\env\flutter-sdk\bin
  C:\Users\Administrator.Win102022PFXUKB\AppData\Local\Android\Sdk\platform-tools
  ```

---

## 三、检查 Flutter 版本并切换至稳定版本

```bash
flutter --version
flutter channel stable
flutter upgrade
```

### 启动模拟器并运行项目

```bash
flutter: Launch Emulator
flutter run       # 或
flutter run -v
```

> ⚠️ 第一次运行可能卡在 `Running Gradle task 'assembleDebug'`，建议开 VPN，如有错误需手动排查。

---

## 四、安装夜神模拟器（解决 Android Studio 模拟器无法联网的问题）

1. **找到 Android Studio 模拟器启动器路径（a）：**
   ```
   C:\Users\Administrator.Win102022PFXUKB\AppData\Local\Android\Sdk\platform-tools\adb.exe
   ```

2. **找到夜神模拟器安装路径（y）：**
   ```
   C:\Program Files (x86)\Nox\bin
   ```

3. **复制 `adb.exe` 到夜神目录，并重命名为：**
   ```
   nox_adb.exe
   ```

4. **编写 bat 脚本：**

   ```bat
   c:
   cd C:\Program Files (x86)\Nox\bin
   nox_adb.exe connect 127.0.0.1:62001
   pause
   ```

5. **夜神模拟器打开 USB 调试模式**

6. **运行脚本并启动项目**

---

## 五、处理 `photo_manager: ^3.6.4` 依赖 JDK 17 问题

### 1. 检查 Flutter 信息

```bash
flutter doctor -v
```

### 2. 检查 Java 版本

```text
Android toolchain
Java version Java(TM) SE Runtime Environment (build 17.0.12+8-39)
```

> 如果不是 JDK 17，需要重新安装。

---

## 六、安装配置 Java 环境

### 1. 下载并安装 JDK 17

官方下载地址：

[JDK 17.0.12 下载](https://download.oracle.com/java/17/archive/jdk-17.0.12_windows-x64_bin.exe)

### 2. 设置系统环境变量

- `JAVA_HOME`：`C:\Program Files\Java\jdk-17`
- `PATH`：`%JAVA_HOME%\bin`

### 3. 设置 Flutter 和 Gradle 使用 JDK 17

```bash
flutter config --jdk-dir="C:\Program Files\Java\jdk-17"
```

> 重启电脑后生效。

---

## 七、运行项目

```bash
flutter clean
flutter pub get
flutter run -v
```

---

## 八、开发调试

- 启动模拟器
- 在 `main.dart` 点击 Debug 按钮启动项目
- 快捷键打开 DevTools：

```
Ctrl + Shift + P -> Flutter: Open DevTools
```