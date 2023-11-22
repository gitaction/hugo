---
title: 4.2 样例工程
type: docs
---

# Hugo 样例工程

在源码精读的[Hugo本地环境搭建](../../03/prerequisite/#7-创建样例项目)环节，我们有搭建一个简单的样例博客。

让我们继续使用这个样例，来打造我们的Hugoverse。

## 创建Hugo样例项目Demo

使用我们在上一节准备好的hugoverse命令行工具hugov，来帮助我们创建这个样例项目。

```shell
➜  hugoverse git:(main) ✗ ./hugov demo
demo dir: /var/folders/rt/bg5xpyj51f98w79j6s80wcr40000gn/T/hugoverse-temp-dir782641825
```

**查看Demo项目结构:**

创建成功后，我们会得到一个临时项目路径，让我们用`tree`命令帮助查看一下文件结构。

```shell
➜  hugoverse git:(main) ✗ cd /var/folders/rt/bg5xpyj51f98w79j6s80wcr40000gn/T/hugoverse-temp-dir782641825
➜  hugoverse-temp-dir782641825 tree
.
├── config.toml
├── layouts
│   ├── _default
│   │   └── single.html
│   └── index.html
├── mycontent
│   └── blog
│       └── post.md
├── myproject.txt
└── themes
    └── mytheme
        └── mytheme.txt

7 directories, 6 files

```

可以看到包含了:

### 配置文件config.toml

```shell
➜  hugoverse-temp-dir782641825 cat config.toml
theme = "mytheme"
contentDir = "mycontent"%
```

### 自定义面局目录layouts

```shell
➜  hugoverse-temp-dir782641825 cd layouts
➜  layouts tree
.
├── _default
│   └── single.html
└── index.html

2 directories, 2 files
```

其中模板index.html有如下内容：

```shell
➜  layouts cat index.html
{{ $entries := (readDir ".") }}
START:|{{ range $entry := $entries }}{{ if not $entry.IsDir }}{{ $entry.Name }}|{{ end }}{{ end }}:END:%
```

用来生成站点首页index.html，从源码了解到，这个模板会遍历根目录下的所有文件，如果不是文件夹，就显示文件名。

再来看看模板single.html：

```shell
➜  layouts cat _default/single.html
<p>hello single page</p>
{{ .Content }}
===
Static Content
===
```

这个模板会用来显示单页面内容，像blog等文章信息。

### 主题目录themes，而且我们用到的是一个名为mytheme的主题

```shell
➜  hugoverse-temp-dir782641825 cd themes
➜  themes ls
mytheme
➜  themes tree
.
└── mytheme
    └── mytheme.txt

2 directories, 1 file
➜  themes cat mytheme/mytheme.txt
Hello theme!%
```

### 内容目录mycontent

```shell
➜  hugoverse-temp-dir782641825 cd mycontent
➜  mycontent tree
.
└── blog
    └── post.md

2 directories, 1 file
```

有一篇博客post.md:

```shell
➜  mycontent cat blog/post.md
---
title: "Post Title"
---
### first blog
Hello Blog%
```

这个内容就会应用到上面的layouts/_default/single.html模板。

### 根目录文件myproject.txt

```shell
➜  hugoverse-temp-dir782641825 cat myproject.txt
Hello project!%
```

这个文件就是用来配合上面的index.html模板的，文件名myproject.txt会显示在模板中。
