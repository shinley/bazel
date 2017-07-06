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



