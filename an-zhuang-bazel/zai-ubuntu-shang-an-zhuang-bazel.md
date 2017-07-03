# 在Ubuntu上安装Bazel {#test}

支持的Ubuntu Linux版本包括:

* 16.04\(LTS\)
* 15.10
* 14.04\(LTS\)

在Ubuntu上安装bazel,有以下几种方式

* 使用我们的APT库\(推荐\)
* 使用二进制安装包
* 从源码编译安装

Bazel自带了两个自动命令补全的脚本, 安装Bazel之后,你可以:

* 获取 [bash 自动补全脚本](/an-zhuang-bazel.md#bash-completion)
* 安装 [zsh 自动补全脚本](/an-zhuang-bazel.md#zsh-completion)

# 使用Bazel的APT仓库安装

1.添加Bazel的分发包地址作为源

```
echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
```

如果你想安装测试版的Bazel , 把上面命令中的 stable替换成 testing

2. 安装和升级Bazel

```
sudo apt-get update && sudo apt-get install bazel
```

安装成功之后,你可以通过以下命令升级到最新的Bazel

```
sudo apt-get upgrade bazel
```

# 通过二进制安装包安装Bazel

Bazel的二进制安装包可以在Bazel的[ GitHub发面页](https://github.com/bazelbuild/bazel/releases) 下载 .

安装包 包含了二进制的Bazel和需要的JDK,  一些Bazel运行必须需的库也要安装.

1.安装必须的包

```
sudo apt-get install pkg-config zip g++ zlib1g-dev unzip
```

2. 下载Bazel

到Bazel的发布页[GitHub releases page](https://github.com/bazelbuild/bazel/releases)

下载二进制安装包**bazel-0.5.2-installer-linux-x86\_64.sh. **这个安装包包含了二进制的Bazel和需要的JDK, 即使已经安装了JDK, 也会使用自带的JDK.

注意: **bazel-0.5.2-without-jdk-installer-linux-x86\_64.sh.** 它是一个没有内嵌JDK的版本, 只会使用你自已安装的JDK8.

3. 运行安装包

```
chmod +x bazel-0.5.2-installer-linux-x86_64.sh
./bazel-0.5.2-installer-linux-x86_64.sh --user
```

--user 表示 安装bazel到 你系统的 $HOME/bin 目录 , 并且会在$HOME/.bashrc中设置PATH环境变量. 

--help 命令可以查看其它的安装选项.

4. 设置环境变量

如果你用--user安装Bazel,  Bazel的可执行文件被安装到 $HOME/bin 目录下,  你可以根据下面的命令把这个目录添加到PATH环境变量中

```
export PATH="$PATH:$HOME/bin"
```

你也可以把这个命令添加到你的 ~/.bashrc 文件中

安装完成之后,你可以升到Bazel到最新的版本,通过以下命令:

```
sudo apt-get upgrade bazel
```



