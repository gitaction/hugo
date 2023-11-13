---
title: 1.3 安装Hugo
type: docs
---

# 1.3 安装Hugo

在Mac上安装Hugo非常简单，你可以按照以下步骤进行：

## 使用 Homebrew 安装（推荐）

1. **打开终端：** 打开你的终端应用程序。

2. **安装 Homebrew（如果未安装）：** 如果你还没有安装Homebrew，可以在终端中运行以下命令进行安装：

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   ```

   上述命令会下载并运行Homebrew的安装脚本。

3. **使用 Homebrew 安装 Hugo：** 在终端中运行以下命令安装Hugo：

   ```bash
   brew install hugo
   ```

4. **验证安装：** 安装完成后，可以验证Hugo是否成功安装，运行以下命令检查版本：

   ```bash
   hugo version
   ```

## 使用官方二进制文件安装

1. **访问 Hugo GitHub Release 页面：** 打开[Hugo GitHub Release页面](https://github.com/gohugoio/hugo/releases)，找到最新版本的Hugo。

2. **下载二进制文件：** 在Assets栏下找到适用于macOS的二进制文件（通常以`.tar.gz`为扩展名），点击下载。

3. **解压缩文件：** 下载完成后，使用终端进入下载目录，解压缩文件，例如：

   ```bash
   tar -xzvf hugo_extended_0.XX.X_macOS-64bit.tar.gz
   ```

   请将上述命令中的`0.XX.X`替换为下载的Hugo版本号。

4. **移动二进制文件：** 将解压后的`hugo`二进制文件移动到一个你喜欢的目录，例如 `/usr/local/bin/`：

   ```bash
   mv hugo /usr/local/bin/
   ```

5. **验证安装：** 在终端中运行以下命令验证Hugo是否成功安装：

   ```bash
   hugo version
   ```

## 升级Hugo到最新版本

1. **打开终端：** 打开你的终端应用程序。

2. **更新 Homebrew：** 在终端中运行以下命令，确保你的 Homebrew 是最新的：

    ```bash
    brew update
    ```

3. **升级 Hugo：** 运行以下命令升级 Hugo：

    ```bash
    brew upgrade hugo
    ```

   这将下载并安装 Hugo 的最新版本。

4. **验证升级：** 升级完成后，你可以运行以下命令验证 Hugo 是否已成功升级：

    ```bash
    hugo version
    ```

   如果看到最新版本的 Hugo 版本号，那么升级就成功了。

hugo通过这些步骤，你就能够使用 Homebrew 将 Hugo 升级到最新版本。

无论你选择使用Homebrew还是官方二进制文件，以上步骤都将在你的Mac上安装Hugo，并使其可用于构建静态站点。


截止写作本章时，本机Hugo版本为：

```bash
➜ hugo version
hugo v0.120.4-f11bca5fec2ebb3a02727fb2a5cfb08da96fd9df+extended darwin/amd64 BuildDate=2023-11-08T11:18:07Z VendorInfo=brew
```