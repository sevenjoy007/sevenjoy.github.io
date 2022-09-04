---
title: "个人博客的搭建" # Title of the blog post.
date: 2022-09-04T10:53:02+08:00 # Date of post creation.
description: "Article description." # Description used for search engine.
featured: true # Sets if post is a featured post, making it appear on the sidebar. A featured post won't be listed on the sidebar if it's the current page
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# menu: main
usePageBundles: false # Set to true to group assets like images in the same folder as this post.
# codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
showRelatedInArticle: false # Override global value for showing related posts in this series at the end of the content.
categories:
  - Technology
tags:
  - tools
  - blog
---

# 个人博客的搭建

## 前言

目前网上有很多现有的博客平台，如知乎、掘金、csdn、segmentfault、简书、博客园等等，可以直接在这些平台上发表自己的博客。优点是可以专注内容本身，缺点是页面格式受限于平台本身而且会受其广告/通知干扰。

**这里专指搭建个人的博客平台，记录下我的博客搭建过程。**

下面先介绍一个关于网站搭建的基本概念

### 静态和动态网站

- 静态网站

> 每个页面都是建站者发送到服务器的一个html文件，每次增删改都要对服务器文件进行一次下载上传。

- 动态网站

> 浏览器请求某个页面时，服务器根据当时时间、参数等动态生成html页面，再发给浏览器。

### 搭建个人网站选项

1. 静态网站生成技术
   
   如JekyII、Hugo、Hexo等，结合Github pages，就能免费完成个人网站的搭建

2. 内容管理系统CMS
   
   需要有自己的服务器跟域名，可以用于搭建企业级网站。如WordPress、Halo等。

综上，因为不想花钱🙃，加上只是搭个博客记录内容非规模性网站，故选择前者。

### 静态网站生成框架

1. **Hexo**

网站：[hexo.io](https://hexo.io/zh-cn/)

> node.js编写，中文友好，有很多主题。
> 
> 教程：[手把手教你从零开始搭建个人博客，20 分钟上手 - 掘金](https://juejin.cn/post/7036876600993906719)

2. hugo

网站：[gohugo.io](https://gohugo.io/)

> go语言编写的，编译速度快

因为对go比较熟悉，所以还是决定用hugo

## 用hugo+githubPages搭建个人博客

### 1. 安装hugo

```bash
brew install hugo
hugo version        // 检验是否安装成功
```

### 2. 创建博客

```bash
hugo new site myblog
```

创建的博客项目为myblog，目录结构如下:

```
├── archetypes
│   └── default.md
├── config.toml         # 博客站点的配置文件
├── content             # 博客文章所在目录
├── data                
├── layouts             # 网站布局
├── static              # 一些静态内容
└── themes              # 博客主题
```

### 3. 使用博客主题

挑选主题：[themes.gohugo.io]([https://themes.gohugo.io/](https://themes.gohugo.io/))，我选的是[Clarity | Hugo Themes](https://themes.gohugo.io/themes/hugo-clarity/)

```bash
cd ../themes
git clone git@github.com:chipzoller/hugo-clarity.git
tree hugo-clarity
```

下载主题内容如下

```
hugo-clarity
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE.md
├── README.md
├── archetypes
├── assets
├── exampleSite        # 本主题实例内容
│   ├── LICENSE
│   ├── README.md
│   ├── archetypes
│   ├── config
│   ├── content        # 示例博客文章
│   ├── layouts
│   ├── resources
│   └── static
├── i18n
├── images
├── layouts
├── resources
├── static
└── theme.toml
```

使用主题：复制到根目录

```
cp themes/hugo-clarity/exampleSite/* ./ -r
```

### 4. 启动博客服务

```bash
hugo server
```

可以看到服务默认会在占用1313 端口，在浏览器中访问`http://localhost:1313/` 地址，预期那种应该可以看到跟hugo官网演示的页面
