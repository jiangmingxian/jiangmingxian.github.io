---
title: "Hugo快速入门"
# summary: "..."
date: 2024-04-29T17:13:23+08:00
draft: false
tags:
- 建站
---

https://gohugo.io/documentation/

# 一、快速入门

```bash
# 安装 hugo
brew install hugo

# 创建项目，项目目录为 quickstart
hugo new site quickstart
cd quickstart
# 初始化 git 仓库
git init
# 添加特定主题到 themes 目录，并将其作为 git 子模块
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
# 指定主题
echo "theme = 'ananke'" >> config.toml
# 本地部署网站，会将网站构建到内存中，并基于简易的HTTP服务器提供页面访问，修改内容实时生效
hugo server
```

<aside>
📌 官方教程有点问题：

- config.toml 和 hugo.toml 不能共存，否则会报错
- 添加新文件，hugo new content posts/my-first-post.md 会报错，改为 hugo new posts/my-first-post.md
</aside>

目录结构：

- archetypes：新内容的模版
- content：网站内容，我们主要维护这部分
- data：用于扩展内容，通常用不上。https://gohugo.io/templates/data-templates/
- public：构建好的网站
- themes：主题。我选择的是官方文档的 [ananke](https://github.com/theNewDynamic/gohugo-theme-ananke#readme)

# 二、网站配置

https://gohugo.io/getting-started/configuration/

- 老版本的配置文件是 config.toml，新版本的配置文件是 hugo.toml

# 三、内容

常用元数据：

- date：发布日期
- draft：是否草稿
- title：标题
- weight：权重，集合中排序会用到

默认不会渲染的内容

> Hugo allows you to set draft, date, publishDate, and expiryDate in the [front matter](https://gohugo.io/content-management/front-matter/) of your content. By default, Hugo will not publish content when:
> 
> - The draft value is true
> - The date is in the future
> - The publishDate is in the future
> - The expiryDate is in the past

# 四、部署网站

```bash
# 构建网站，并将内容发布到 public 目录下
hugo
```

实际通常使用 CI/CD 流——Github Pages + Github Actions


