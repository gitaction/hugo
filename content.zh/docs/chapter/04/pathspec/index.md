---
title: 4.4 DDD PathSpec
type: docs
---

# DDD PathSpec

在用DDD来驱动Hugo依赖的PathSpec之前，让我们还是先来回顾一下[Hugo源码精读 PathSpec](../../03/code/deps/pathSpec)中所描述到的主要实现思路。

![PathSpec](images/9.10-Hugo-Sites-PathSpec-input-output.svg)

输入初始文件系统，以及模块信息，输出统一文件系统。

这样做的好处是让使用者不用去面对复杂的文件系统组织关系，而是直接使用按Hugo文件系统结构组织好的统一文件系统。

比如layouts：

- 用户可能会自定义layout，所以在Project模块下有可能有layouts目录。
- 用户还可能会引用主题，主题里也会有layouts目录。复杂的情况是这个主题可能还会引用其它主题，那我们就还得处理好其它的主题layouts目录。

如果不把这些目录结构都统一设置好，那我们在用layouts里的模板时，就得自己处理这些模板的依赖关系，及覆盖关系。
这些复杂度就会分散在不同的代码里，显然不符合高内聚，低耦合的要求。

所以，Hugo的做法是提前把这些信息都准备好，放在Hugo构建站点的依赖Deps里，以备后续使用之需。

## Hugoverse PathSpec 源码运行展示

## Hugoverse PathSpec 信息流

## PathSpec DDD 战略图更新

## PathSpec 内部结构

## PathSpec DDD 战术图更新


源码运行结果

1. pathspec的功能，定位：9.10
2. 采用总分总，从 ddd 战略图查看 pathspec 与 deps 之间的关系
   1. ~/go/bin/dp strategic -m ./ -p github.com/dddplayer/hugoverse
3. pathspec message flow 用来帮助理解源码里的调用逻辑:
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/internal/domain/pathspec -mf
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.internal.domain.pathspec.messageflow.dot
4. pathspec 对象组成
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/internal/domain/pathspec -c
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.internal.domain.pathspec.composition.dot
5. fs message flow :
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/internal/domain/fs -mf
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.internal.domain.fs.messageflow.dot
6. fs composition
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/internal/domain/fs -c
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.internal.domain.fs.composition.dot
7. Overlay
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/pkg/overlayfs -mf
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.pkg.overlayfs.messageflow.dot
   3. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/pkg/overlayfs -c
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.pkg.overlayfs.composition.dot
8. Radix Tree
   1. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/pkg/radixtree -mf
   2. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.pkg.radixtree.messageflow.dot
   3. ~/go/bin/dp normal -m ./ -p github.com/dddplayer/hugoverse/pkg/radixtree -c
   4. https://dddplayer.com/?path=https://assets.dddplayer.com/resource/hugov/github.com.dddplayer.hugoverse.pkg.radixtree.composition.dot