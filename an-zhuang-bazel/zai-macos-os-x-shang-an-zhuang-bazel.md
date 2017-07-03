# 在macOS\(OS X\)上安装Bazel

使以以下方式在macOS\(OS X\)上安装Bazel:

* 使用 Homebrew\(推荐\)
* 使用二进制安装包安装
* 从源代码编译安装

Bazel自带了两种命令自动补全的脚本, 安装Bazel之后, 你可以:

* 获取 [bash 自动补全脚本](/an-zhuang-bazel.md#bash-completion)

* 安装 [zsh 自动补全脚本](/an-zhuang-bazel.md#zsh-completion)

## 使用Homebrew安装

1.安装JDK8

JDK8可以从 [Oracle's JDK Page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) 下载,  在 "Java SE Development Kit" 下面找.   你要下载一下带引导安装的DMG镜像.

2.在macOS\(OS X\)上安装Homebrew

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

3.使用Homebrew安装Bazel

```
brew install bazel
```

一切准备就绪, 你可以确认Bazel是否安装正确, 通过运行命令: bazel version .

以后升级 bazel到最新版本, 你可以通过命令: brew upgrade bazel .

## 使用二进制安装包安装Bazel

二进制的安装包可以到Bazel在GitHub上的发布页下载:[GitHub releases page](https://github.com/bazelbuild/bazel/releases).

安装包包含了二进制的Bazel和需要的JDK. 一些其它Bazel运行需要的包也必须安装.

1.安装XCode 命令行工具

Xcode的下载地址: [Apple Developer Site](https://developer.apple.com/xcode/downloads/) \(这个链接跳转到App Store\).

如果你需要支持 objc_\* 和  ios_\_\*  这两个规则,你必须在你的系统上安装Xcode6.1 和 iOS SDK8.1.

安装XCode后，您可以使用以下命令获取license：

```
sudo gcc --version
```

2. 下载Bazel安装包



