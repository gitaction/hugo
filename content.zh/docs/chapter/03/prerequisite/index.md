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

### 7. 创建样例项目

让我们准备一个样例博客，足够简单，但也要结构完整。
这样一方面可以减少我们的心智负担，另一方面，在理解构建的这个过程中，也能方便的将文件一一对应上，帮助我们理解源码结构。

下面是一个简单的初始化博客内容：
```
-- config.toml --
theme = "mytheme"
contentDir = "mycontent"
-- myproject.txt --
Hello project!
-- themes/mytheme/mytheme.txt --
Hello theme!
-- mycontent/blog/post.md --
---
title: "Post Title"
---
### first blog
Hello Blog
-- layouts/index.html --
{{ $entries := (readDir ".") }}
START:|{{ range $entry := $entries }}{{ if not $entry.IsDir }}{{ $entry.Name }}|{{ end }}{{ end }}:END:
-- layouts/_default/single.html --
{{ .Content }}
===
Static Content
===

```

可以看到我们自定义了一个主题**mytheme**，只有一个mytheme.txt文件，并没有实际的模板文件。
这将会在下面的构建流程讲解中，帮助我们理解到主题是如何嵌套和加载的。

我们的内容文件夹是**mycontent**，在blog目录下有一篇简单博文/blog/post.md。
如果想要独立访问这篇博文，就需要为她生成一个HTML文件，这样我们就可以在浏览器中访问了。

在样例中，为了生成首页和博客，我们还在layouts下创建了两个模板。
一个是首页模板index.html，另一个则是单篇文章会用到的模板_default/single.html。

通过[golang tools txtar](https://pkg.go.dev/golang.org/x/tools/txtar)解析上述文本，方便我们转换成如下结构的磁盘文件：

```
.
├── config.toml
├── layouts
│  ├── _default
│  │   └── single.html
│  └── index.html
├── mycontent
│   └── blog
│     └── post.md
├── myproject.txt
└── themes
    └── mytheme
        └── mytheme.txt
```

用刚准备好的hugo命令行进行构建，就能生成如下站点目录：

```
➜  public tree
.
├── blog
│   └── index.html
├── index.html
└── robots.txt
```

这里面包含了我们想要的信息：

#### 样例站点首页
```
➜  public cat index.html

START:|config.toml|myproject.txt|:END:%
```

#### 样例博客页面

```
➜  public cat blog/index.html
<h3 id="first-blog">first blog</h3>
<p>Hello Blog</p>

===
Static Content
===

  %
```

如果对上面的代码实现感兴趣，可以参照[Txtar样例代码](https://c.sunwei.xyz/txtar.html)。

现在，你已经在本机搭建好了 Hugo 源码的阅读环境。
就让我们一起，开始深入了解 Hugo 的实现吧。
