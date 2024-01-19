## 准备工作

1. 下载Hugo[安装包](https://wwtl.lanzoum.com/iwFUs1lefywd)，hugo安装包后缀extension代表扩展版，一般就下载这个（更全面，更兼容）
2. 下载自己喜欢的hugo[主题](https://github.com/CaiJimmy/hugo-theme-stack)，这里提供的是本站使用的主题，直接Github上clone下来或者Download ZIP即可

这边说明一下

- **GitHub Pages** 是一个静态站点托管服务，直接将个人、组织或项目的页面托管于 GitHub 库或仓库 (repository) 中。
- **Hugo** 是一个用 Go 语言编写的静态站点生成器，它针对速度、易用性和可配置性进行了优化，快速灵活。

这也就意味着是使用Hugo在本地进行网站文件的编写，然后生成Public文件夹（静态网站文件），最后将Public文件夹部署到Github上，通过GitHub Pages生成静态网页。

## 安装Hugo

这里只说明在windows上安装的方法，即将解压后的***hugo.exe所在目录***加入系统环境变量中。

安装完成后，输入以下命令来确认。

```bash
hugo version
```

安装是否成功显而易见


## 新建 Hugo 网站

1. 进入你想存放 Hugo 网站文件夹的目录。
2. 打开终端（注意要在第一步的目录下）执行以下命令新建一个 Hugo 网站。

```bash
hugo new site blog   # "blog" 是我的网站文件夹名。
```

进入创建的 `blog` 目录，可以看到生成的目录结构长这样：

```text
├── archetypes
    └── default.md
├── hugo.toml
├── content
├── data
├── layouts
├── static
└── themes
......
```

## 选择一个主题

创建完网站之后，我们就可以使用一开始下载的主题了。

这里以 hugo-theme-stack 这个主题为例，进入上一步创建的个人网站文件夹，并克隆主题到 themes 文件夹（如果没有就新建一个）。

## 修改网站配置

修改项目根目录下的hugo.toml，最后一行新增：

theme = '你使用的主题名称'

例如：theme = 'hugo-theme-stack'

与此同时，其余行都可自定义，如博客名称等，可以自行尝试。

修改好后，在项目根目录运行以下命令：

```bash
hugo server
```

如果没有报错的话，就可以看到 hugo 服务器在本地运行了。

## 创建文章

接下来我们可以开始写文章了，通过直接在命令行（blog目录下）输入：

```text
hugo new posts/helloworld.md
```

新建一篇文章。在生成的文件中使用 `markdown` 格式来书写文章内容。

```markdown
---
title: "Helloworld"
date: 2020-04-19
draft: true   #上传时需要改为false,因为这一行的含义是'是否为草稿'
---

## 说明

> HelloWorld

这是内容
```

## 网站预览

执行 `server` 命令，对所有已发布和编辑中的文章进行预览：

```text
hugo server
```

使用浏览器打开 [http://localhost:1313](http://localhost:1313) 预览。

当然，这一步可以使用bat脚本自动化，blog文件夹下新建**本地运行.bat**，右键编辑以下内容

```bash
@echo off 
chcp 65001 # 用于显示UTF-8字符
echo 【本地运行】
start chrome http://localhost:1313/
hugo server
pause
```

## 发布内容

写完文章，预览没问题后，可以更改文章的草稿状态 `draft: false`，然后编译生成静态网站内容了：

```text
hugo
```

可以看到生成的静态内容都在 `public` 目录下面：

```text
public
├── 404.html
├── categories
├── css
├── index.html
├── index.xml
├── page
├── posts
├── sitemap.xml
└── tags
```

## 部署到线上

最简单的部署方式，只需要把 `public` 目录下的内容上传到 `Github`，并使用 `Github Pages` 创建一个站点，就可以通过：`xxx.github.io` 访问了，还可以绑定自定义域名。
