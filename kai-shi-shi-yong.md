# 开始使用Bazel

### 配置环境

查看[安装说明](/an-zhuang-bazel.md), 在你的机器上安装好Bazel.

### 使用工作区

所有的构建都是在**工作区**\(workspace\)中,  工作区是一个在你的文件系统上包含了要构建软件的源代码的目录, 以及包含构建输出的目录的符号链接\(例如: bazel-bin和bazel-out\). 工作区的目录在哪个地方无所谓, 但是它必须在顶层目录中包含一名为WORKSPACE的文件; 一个空的WORKSPACE文件也是有效的. 这个WORKSPACE文件可用于引用构建输出所需的外部依赖关系。 如果需要，可以在多个项目之间共享一个工作区。

```
touch WORKSPACE
```

### 创建BUILD文件

Bazel通过检查BUILD文件知道你要构建工程中的哪一个目录. BUILD文件是用Bazel语言编写的,它的语法类似于Python. 它声明了一系列的规则,每个规则规定了输入，输出；以及计算输入输出的方法．

也许对以前用过Makefile的人们来说，最熟悉的一个规则应该是genrule

```
genrule(
  name = "hello",
  outs = ["hello_world.txt"],
  cmd = "echo Hello World > $@",
)
```

shell命令可以包含Make变量

使用上面的BUILD文件, 你可以让Bazel生成目标.

```
$ bazel build :hello
.
INFO: Found 1 target...
Target //:hello up-to-date:
  bazel-genfiles/hello_world.txt
INFO: Elapsed time: 2.255s, Critical Path: 0.07s
```

我们注意到两件事情。 首先，目标通常由其标签引用，它由规则的name属性指定。 （通过输出文件名称引用它们也是可以的，但这不是首选的方法。）第二，Bazel将生成的文件放入一个单独的目录中（bazel-genfiles目录实际上是一个符号链接），以免污染您的 源码树。

一个规则的输出,可以做为另一个规则的输入. 就像下面的例子中, 生成的来源被它们的标签引用。

```
genrule(
  name = "hello",
  outs = ["hello_world.txt"],
  cmd = "echo Hello World > $@",
)

genrule(
  name = "double",
  srcs = [":hello"],
  outs = ["double_hello.txt"],
  cmd = "cat $< $< > $@",
)
```

虽然genrule可能看起来很熟悉, 但是最好使用每个语言专有的规则.

