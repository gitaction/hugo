---
title: 1.4 创建Hugo站点
type: docs
---

# 1.4 创建第一个Hugo站

确保 Hugo 已经安装在你的系统上。
开始创建站点：

## 步骤 1：创建新站点

在终端中，使用以下命令创建一个新的 Hugo 站点：

```bash
hugo new site myfirstsite
```

这将在当前目录下创建一个名为 `myfirstsite` 的新 Hugo 站点。

## 步骤 2：添加内容

进入新创建的站点目录：

```bash
cd myfirstsite
```

然后，添加一篇文章：

```bash
hugo new posts/my-first-post.md
```

这将在 `content/posts/` 目录下创建一个名为 `my-first-post.md` 的 Markdown 文件。

## 步骤 3：编辑内容

使用你喜欢的文本编辑器打开 `content/posts/my-first-post.md` 文件，并编辑文章内容。你可以使用 Markdown 格式书写文章。

```markdown
---
title: "我的第一篇文章"
date: 2023-11-13T10:00:00+00:00
draft: false
---

# 欢迎来到我的第一篇文章

这是我使用 Hugo 创建的第一篇文章。希望你喜欢！
```

## 步骤 4：运行本地服务器

在站点根目录下运行以下命令，启动 Hugo 的本地服务器：

```bash
hugo server -D
```

这将启动一个本地服务器，允许你在浏览器中查看你的站点。访问 `http://localhost:1313/` 即可查看。

## 步骤 5：构建静态站点

如果你满意本地预览，可以构建整个静态站点。在终端中运行：

```bash
hugo
```

这将在 `public/` 目录下生成静态站点文件。

## 步骤 6：部署

将生成的 `public/` 目录下的文件部署到你喜欢的托管平台，如 Netlify、GitHub Pages 等，或者自己的服务器。

这样，你就成功地创建了一个简单的 Hugo 静态站点，添加了一篇文章，并在本地预览了站点。