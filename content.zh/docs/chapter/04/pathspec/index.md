---
title: 4.4 DDD PathSpec
type: docs
---

# DDD PathSpec

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