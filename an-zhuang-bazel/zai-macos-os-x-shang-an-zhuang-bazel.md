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

2.下载Bazel安装包

到Bazel的发布页下载:[GitHub releases page](https://github.com/bazelbuild/bazel/releases)

下载二进制的安装包 **bazel-0.5.2-installer-darwin-x86\_64.sh.** 这个安装包包含了二进制的bazel和需要的JDK. 不管你的系统上是否装有JDK ,都 会使用这个内嵌的JDK.

**注意 **bazel-0.5.2-without-jdk-installer-darwin-x86\_64.sh 是一个没有内嵌JDK8的版本. 只会使用你系统上已经安装的JDK8.

3.运行安装包

```
chmod +x bazel-0.5.2-installer-darwin-x86_64.sh
./bazel-0.5.2-installer-darwin-x86_64.sh --user
```

--user 表示 安装bazel到 你系统的 $HOME/bin 目录 , 并且会在$HOME/.bazelrc中设置PATH环境变量.

--help 命令可以查看其它的安装选项.

4.设置环境变量

如果你用--user安装的Bazel,  Bazel的可执行文件被安装到 $HOME/bin 目录下,  你可以根据下面的命令把这个目录添加到PATH环境变量中

```
export PATH="$PATH:$HOME/bin"
```



