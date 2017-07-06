* 介绍 Introduction
* 工作区, 包和目标  Workspace. Packages and Targets

  * 工作区\(Workspace\)
  * 包\(Packages\)
  * 目标\(Targets\)
  * 标签\(Labels\)
  * 标签规范
  * 规则\(Rules\)

* BUILD文件

  * 核心构建语言
  * 声明构建规则

* 构建规则的类型

* 依赖

  * 实际依赖和声明依赖

  * 依赖类型

  * 使用标签引用目录

# 介绍

Bazel从一个叫做工作区的目录中的源码构建软件, 工作区中的源文件组织在一个嵌套的层次结构中，其中每个包是一个包含一组相关源文件和一个BUILD文件的目录。 BUILD文件指定了从源文件构建出什么 样的软件.

# 工作区, 包和目标\(Workspace, Packages, Targets\)

## 工作区

一个工作区就是一个在你的文件系统中的目录, 它包含了你要构建的软件的源文件, 和包含构建输出目录的链接符号. 每一个工作区包含 了一个叫做WORKSPACE的文本文件, WORKSPACE文件可以是空的, 或者包含了需要的外部依赖的引用.  你可以在构建百科中查看工作区规则 .

## 包

在工作区中,最主要的代码组织单元就是包.  包就是一组相关的文件和它们之间依赖关系的一种规范.

包被定义为一个包含了名叫BUILD文件的目录. 它在工作区目录之下. 包中包含 其目录中的所有文件,以及它下面的所有子目录, 但是其中也包含了BUILD文件的文件夹除外.

例如, 在下面的目录树中, 有两个包: my/app 和子包 my/app/tests. 注意: my/app/data不是一个包, 它是属于包my/app的一个目录

```
src/my/app/BUILD
src/my/app/app.cc
src/my/app/data/input.txt
src/my/app/tests/BUILD
src/my/app/tests/test.cc
```



