---
title: GitHub Pages sunwei.xyz
type: docs
---

## 将站点部署到GitHub Pages

将 Hugo 站点部署到 GitHub Pages 非常简单，以下是详细的步骤：

### 步骤 1：创建 GitHub 仓库

1. 在 GitHub 上创建一个新的仓库，仓库名为 `<你的用户名>.github.io`。请确保使用你的 GitHub 用户名替换 `<你的用户名>`。

2. 在终端中，进入你的 Hugo 站点目录。

3. 初始化 Git 仓库并将其关联到你的 GitHub 仓库：

    ```bash
    git init
    git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
    ```

### 步骤 2：配置 Hugo

1. 打开站点的配置文件 `config.toml`（或 `config.yaml` 或 `config.json`，取决于你使用的配置格式）。

2. 添加以下配置，指定基准路径（baseURL）：

    ```toml
    baseURL = "https://<你的用户名>.github.io/"
    ```

   请确保使用你的 GitHub 用户名替换 `<你的用户名>`。

### 步骤 3：生成静态站点

在终端中运行以下命令，生成静态站点文件：

```bash
hugo
```

这将在站点目录下生成一个 `public/` 文件夹，其中包含静态站点的所有文件。

### 步骤 4：提交代码到 GitHub

1. 将生成的 `public/` 文件夹下的内容提交到 GitHub 仓库：

    ```bash
    git add .
    git commit -m "Initial commit"
    ```

2. 推送到 GitHub：

    ```bash
    git push -u origin master
    ```

### 步骤 5：启用 GitHub Pages

1. 进入你的 GitHub 仓库。

2. 点击上方导航栏中的 "Settings"。

3. 在仓库设置页面的左侧导航栏中，找到 "Pages" 选项。

4. 在 "Source" 下拉菜单中选择 `master branch`，然后点击 "Save"。

5. GitHub Pages 将自动为你的仓库启用，并提供站点的链接。通常是 `https://<你的用户名>.github.io/`。

6. 等待一段时间，GitHub 将构建并发布你的 Hugo 站点。

一旦 GitHub Pages 构建完成，你的 Hugo 站点就会在指定的链接上可见了。访问 `https://<你的用户名>.github.io/` 查看你的站点。请注意，可能需要一些时间才能完成首次构建。


## 进阶：通过GitHub Actions持续部署

### 创建GitHub Actions Workflow

如实例[sunwei.xyz](https://github.com/sunwei/xyz)所示[gh-pages.yml](https://github.com/sunwei/xyz/blob/master/.github/workflows/gh-pages.yml):

```toml
name: github pages

on:
  push:
    branches:
      - master  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: "latest"

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/master'
        with:
          github_token: ${{ secrets.DEPLOY_TOKEN }}
          publish_dir: ./public
          cname: sunwei.xyz
```

### 申请 DEPLOY_TOKEN

- 申请 token: [配置Tokens](https://github.com/settings/tokens)
- 配置仓库 token: 依次点击./settings/secrets/actions, 将 token 取名为: "DEPLOY_TOKEN"
- 自定义域名: [为您的 GitHub Pages 站点配置自定义域](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

从现在起，我们只需要日常的更新自己的站点内容，我们的站点就可以自动部署了。
你也就可以和我一样，通过自己的域名，来访问自己的网站了。
