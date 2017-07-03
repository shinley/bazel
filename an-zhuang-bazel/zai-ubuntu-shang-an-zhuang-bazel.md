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

