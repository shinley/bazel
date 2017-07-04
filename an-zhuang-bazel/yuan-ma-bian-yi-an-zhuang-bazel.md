# 从源代码编译Bazel

### 在Linux 或者macOS上

1.确保你的机器上安装了Open JDK8,   如果你的系统是基于debian的包管理的\(如: Debian, Ubuntu\), 安装OpenJDK8可以通过命令

```
sudo apt-get install openjdk-8-jdk
```

1. 从源代码编译Bazel的标准方式是使用Bazel源代码分发包,  从Bazel的发布页[release page](https://github.com/bazelbuild/bazel/releases)下载你需要的版本 bazel-&lt;VERSION&gt;-dist.zip , 我们建议验证我们的[发行号码](https://bazel.build/bazel-release.pub.gpg)48457EE0所签署的签名, 分发包包含 了生成的文件和已经版本化了的源代码, 所这一步不能通过检出源代码简化.

2. 解压源码包并且执行 bash ./compile.sh; 这个命令会在output/bazel目录下创建一个二进制的bazel文件.  这个二进制文件是独立的,你可以把它拷贝到PATH路径下\(比如: /usr/local/bin\), 或者放到意目录并添加到PATH环境变量中.

### 在windows上

由于官方不建议在windows上使用bazel, 所以不再翻译.

