# Bazel 概览

Bazel是一个构建工具, 它可以协调构建各个模块, 并且可以运行单元测试.  它的扩展语言使它可以构建任何类型的计算机语言, 并且原生支持Java，Ｃ，Ｃ++和Python.  Bazel的作者已经在各个平台上进行了充分的构建和测试.

## 用简单的声明性语言构建文件

Bazel的BUILD文件描述了怎样构建你的项目.  它的语法结构类似于Python的语法. 你可以编写BUILD文件的规则来构建你的系统. 或者通过扩展Bazel的规则使它能够在任何平台上构建任何语言.

下面是一个Hello World程序的BUILD 构建文件,  它使用到了两个规则:  cc\__library 和 cc_\_binary.

```
cc_library(
    name = "hello-time",
    srcs = ["hello-time.cc"],
    hdrs = ["hello-time.h"],
)

cc_binary(
    name = "hello-world",
    srcs = ["hello-world.cc"],
    deps = [
        ":hello-time",
        "//lib:hello-greet",
    ],
)
```

## 描述整个系统的系赖图

BUILD文件中声明了构建依赖的资源,  Bazel可以通过它精确地画出所有源代码的依赖图.  只不过这张图由Bazel维护在内存中. 由于这张精确的依赖图存在, 它使得增量构建和平行执行成为了可能.

下面这张依赖图是通过上面的BUILD文件,  来描述 "hello-world"目标的依赖的关系

![](https://docs.bazel.build/assets/graph_hello-world.svg)

Bazel的查询语言可以让你生成这样的依赖图, 你也可以使用查询语言获得 构建依赖和依赖之间的关系.

## 快速地构建和测试, 修改和复现

互不干扰的规则和沙箱环境让Bazel构建出正确的, 可重复使用的构件和测试结果. 缓存可以使构建出的构件和和测试结果重复使用.

Bazel的构建速度特别快, 增量构建使得Bazel在进行重复构建时可以做最少的工作.  Bazel的准确性和可重复性使得Bazel可以重复使用未经修改且已缓存的构件. 也就是说当你修改你的代码时, Bazel不会重新构建你所有的源代码, 而只是重新构建你修改了的代码.

你可以完全信任Bazel的构建结果的正确性. 也就是说你不用运行 bazel clean命令来清除bazel的构建结果.  如果你需要运行 bazel clean命令, 那只能说明 bazel 存在着bug.

