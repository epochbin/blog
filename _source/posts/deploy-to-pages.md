---
title: "把它挂到 GitHub Pages"
slug: deploy-to-pages
date: 2026-11-02T21:30
tags: [部署]
---

从零到能访问，大概十分钟。一共四步。

## 一、建仓库

打开 github.com，右上角 + → New repository。

- 名字随意，比如 blog
- 选 **Public**（私有仓库的 Pages 要付费，评论也用不了）
- 不用勾 README，空的就行

建好后仓库地址类似 `github.com/你的用户名/blog`

## 二、拿一个 Token

这是唯一有点门槛的一步。

打开 https://github.com/settings/personal-access-tokens/new

- **Token name**：随便，比如 blog-publisher
- **Expiration**：可以选 No expiration，省得半年后过期
- **Repository access**：选 Only select repositories，只勾刚才那个 blog
- **Permissions** → 找到 **Contents**，改成 **Read and write**

其他权限一个都不用给。

生成后那串字符只显示一次，先复制到备忘录。

## 三、填进编辑器

打开这个 HTML，点底栏 **设置**：

- GitHub 用户名
- 仓库名（blog）
- 分支（main）
- Token（粘上刚才那串）
- 站点标题、副标题、你的邮箱
- 站点地址：`https://你的用户名.github.io/blog`

保存。设置面板底部有「测试连接」，点一下，能读到仓库就说明 Token 对了。

## 四、开 Pages 并发布

回到仓库，**Settings → Pages**：

- Source 选 **Deploy from a branch**
- Branch 选 **main**，目录选 **/(root)**
- Save

然后回编辑器，点底栏 **发布**。等几十秒，访问：

~~~
https://你的用户名.github.io/blog/
~~~

第一次可能要等一两分钟，刷新几次。

## 之后每次

写完 → 点发布 → 等半分钟。没有别的事要做。

## 几个坑

- **Token 只读会导致 404**。填的时候确认 Contents 是 Read and write，不是 Read
- **仓库如果是 用户名.github.io**，站点地址就是 `https://用户名.github.io/`，没有子路径
- **发布失败先看面板里的日志**，它会写清楚卡在哪一步（读分支、建树、提交、更新分支）
- **想清空重来**，用设置里的「清空仓库」，它会二次确认
