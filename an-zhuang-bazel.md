# 安装Bazel

Bazel可以安装在以下平台上:

* Ubuntu Linux \(16.04, 15.10, 和 14.04\)
* Mac OS X
* Windows\(试验\)      不推荐在windows上使用bazel
* 源码安装

需要的JAVA 版本:

需要Java JDK 8或更高版本。 为了解决JDK 8在某些机器上无法使用的问题，Bazel的二进制安装程序默认嵌入了JDK。

**注意：**

Homebrew和Debian软件包不包含嵌入式JDK。 shell安装程序是唯一具有嵌入式JDK的安装程序。

在JDK7下安装Bazel

Bazel的0.5.1版本可以运行在JDK 7上, 但是 Bazel的0.5.2版本必须使用JDK 8版本 .

可用的安装程序有下面这些:

* bazel-0.5.1-install.sh: 默认有内嵌的JDK
* bazel-0..5.1-without-jdk-install.sh :默认没有内嵌JDK
* bazel-0.5.1-jdk7-install.sh : 些版本与JDK7兼容,但与以后的JDK版本不兼容

#### 通过bash脚本实现**命令补全: ** {#bash-completion}

Bazel 自带了一个命令自动补全的脚本,  当你通过shell脚本安装bazel时,如果加了参数 --user , 这个脚本就在 $HOME/.bazel/bin目录下. 如果你是用root用户安装的, 这个脚本就在/usr/local/bazel/bin目录下. 这个脚本的名字叫做 bazel-complete.bash.

拷贝bazel-complete.bash脚本到你的自动补全文件夹下\(Ubuntu下是/etc/bash_completion.d目录\), 如果你没有一个自动补全的目录, 你可以把这个脚本拷贝到合适的位置, 然后在 ~/.bashrc文件中插入 source /path/to/bazel-complete.bash. \(在 OS X 系统下, 插入到~/.bash_\_profile文件中\)

如果你是通过 Bazel的源码安装的, 这个自动被全的目标在 //scripts包下:

* 用Bazel构建 : bazel build //scripts:bazel-complete.bash
* 然后拷贝构建后的脚本 bazel-bin/scripts/bazel-complete.bash到合适的位置. 参考上面的描述.

#### **通过zsh脚本实现命令补全** {#zsh-completion}

此方式没有使用过, 如果你需要使用,可以参考官方文档.

