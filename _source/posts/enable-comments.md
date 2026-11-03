---
title: "打开评论区"
slug: enable-comments
date: 2026-11-01T19:00
tags: [配置]
---

评论区用的是 [giscus](https://giscus.app)，它把留言存进你仓库的 GitHub Discussions。所以不需要任何第三方服务器，也不用注册新账号——留言的人用 GitHub 身份登录就行。

不想用也没关系，先关着。每篇文章底部的「写信给我」一直都在。

## 三个前提

1. 仓库是 **Public**
2. 仓库开启了 **Discussions**
3. 装了 **giscus App**

前两个在仓库的 **Settings → General → Features** 里：勾上 Discussions，仓库顶部会多一个 Discussions 标签。

第三个：打开 https://github.com/apps/giscus，Install，只授权你的博客仓库。

## 拿两个 ID

打开 https://giscus.app/zh-CN：

- **Repository** 填 `你的用户名/仓库名`
- 填对了下面会出现一个绿色的对勾
- **Discussion 分类**选 Announcements
- **页面 ↔ Discussions 映射**：随便选，编辑器会用文章 slug 自己覆盖
- 主题也不用管，它跟随你的明暗切换

往下滑到底，会有一段代码，里面有两行是关键：

~~~
data-repo-id="R_kgDO..."
data-category-id="DIC_kwDO..."
~~~

## 填进设置

编辑器 → **设置** → 评论（giscus）：

- 勾上「在文章底部显示评论区」
- 评论仓库留空（自动用本站仓库）
- 仓库 ID：`R_kgDO...`
- 分类名：Announcements
- 分类 ID：`DIC_kwDO...`

保存，发布一次。

## 怎么验证成功

打开任意一篇文章，正文底部会出现「留言」区块。第一次有人留言时，你的仓库 Discussions 里会自动多出一条讨论，标题就是文章 slug。

如果整块不显示：先检查两个 ID 是否都填了（缺一个就不渲染）、开关是否保存、以及这次有没有发布成功。

## 几个说明

- 评论只在**文章页**出现，首页和归档页没有
- 每篇文章对应一条独立讨论，按 slug 匹配，所以换文件名不会丢评论
- 读者可以选表情、回复楼中楼，都是 giscus 自带的能力
- 评论是**公开的**，和仓库一样所有人可见
