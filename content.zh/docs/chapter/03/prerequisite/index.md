---
title: 3.2 Hugo环境搭建
type: docs
---


# Hugo本地环境搭建

搭建 Hugo 源码的阅读环境步骤：

### 1. 安装 Git

首先，确保你的机器上安装了 Git。
你可以从[Git 官方网站](https://git-scm.com/)下载并安装。

### 2. 安装 Go

Hugo 是使用 Go 语言编写的，因此你需要安装 Go。
你可以从[Go 官方网站](https://golang.org/)下载并安装。

示例：
```bash
➜  go version
go version go1.21.1 darwin/amd64
```

### 3. 获取 Hugo 源码

在终端中运行以下命令，获取 Hugo 的源代码：

```bash
git clone git@github.com:gohugoio/hugo.git
```

### 4. 进入 Hugo 源码目录

```bash
cd path/to/gohugoio/hugo
```

### 5. 构建 Hugo

在源码目录中运行以下命令，构建 Hugo：

```bash
go install
```

### 6. 验证环境

```bash
go build -o hugo
./hugo version
```

如果一切正常，你应该看到 Hugo 的版本信息。

示例:
```bash
➜  hugo git:(master) ✗ go build -o hugo
➜  hugo git:(master) ✗ ./hugo version
hugo v0.121.0-DEV-ac7cffa7e2932fc3c6bd425f86b981dfdef94968 darwin/amd64 BuildDate=2023-11-08T11:32:02Z
```

现在，你已经在本机搭建好了 Hugo 源码的阅读环境。
就让我们一起，开始深入了解 Hugo 的实现吧。
