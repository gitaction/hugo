# Hugo 游乐场

使用Hugo构建站点的体验很棒。
首先是构建速度快，其次是使用起来简单，一个`hugo`命令，我们的站点就已经就绪。

在构建过程中，Hugo提供了丰富的内置功能函数，可以在构建过程中向你提供所需要的几乎任何站点相关的信息。
通过可重用模板，让主题来帮助处理所有展示和布局相关的问题。
让作者更专注在内容的创作上。

## 游乐场

站点构建的就将写好的内容，转化成Web服务器能理解的网站资源。
比如我们写作的时候用的是Markdown格式，生成的网站资源通常是HTML格式。

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

通过golang tools txtar解析上述文本，方便我们转换成如下结构的磁盘文件：
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
通过Hugo命令进行构建，就能生成如下站点资源：
```
➜  public tree
.
├── blog
│   └── index.html
├── index.html
└── robots.txt
```
并包含了我们想要的信息：

### 站点首页
```
➜  public cat index.html

START:|config.toml|myproject.txt|:END:%
```

### 博客页面
```
➜  public cat blog/index.html
<h3 id="first-blog">first blog</h3>
<p>Hello Blog</p>

===
Static Content
===

  %
```

那Hugo的这个魔术到底是怎么变出来的呢？

为了了解Hugo构建的核心原理，通过对Hugo最新源码进行裁剪，移除当前阶段不必要的"噪音"。
结合我们上面的实例，手动生成了一个最小可工作源码库 - [hugo游乐场](https://github.com/gitaction/hugo-palyground)。
以保证我们在这个游乐场可以尽情地玩耍，专注于核心原理，享受整个源码的学习过程。

通过命令:
```
git ls-files | grep '\.go' | xargs wc -l
```
分别统计[gohugoio/hugo](https://github.com/gohugoio/hugo)和[hugo playground](https://github.com/gitaction/hugo-palyground)的代码行数。
我们得到的数据分别是 **163075** 和 **33990** 行。

**整整缩减了近四倍！**

相信各位看官也会虎躯一震，信心倍增！看源码原来也可以这么开心。
请准备好瓜子饮料小板凳，各位看官你细听分说。

### Show Me The Code

```go
package main

import (
	"bytes"
	"fmt"
	"path/filepath"

	"golang.org/x/tools/txtar"
)

// 文件结构
// 文件名: config.toml
// 文件内容：theme = 'mytheme'
var files = "-- config.toml --\n" +
	"theme = 'mytheme'"

func main() {
	// 解析上面的文件结构
	data := txtar.Parse([]byte(files))
	fmt.Println("File start:")

	// 遍历解析生成的所有文件，通过File结构体获取文件名和文件数据
	// f.Name 获取文件名
	// f.Data 获取文件数据
	for _, f := range data.Files {
		filename := filepath.Join("workingDir", f.Name)
		data := bytes.TrimSuffix(f.Data, []byte("\n"))

		fmt.Println(filename)
		fmt.Println(string(data))
	}
	fmt.Println("File end.")
}
```
Output:
```text
# 解析后得到文件config.toml，以及下面的文件内容
# workingDir就是我们的工作目录，通常是要写入的文件目录

File start:
workingDir/config.toml
theme = 'mytheme'
File end.
```

[Try it yourself](https://c.sunwei.xyz/txtar.html)