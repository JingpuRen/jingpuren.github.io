---
id: how-to-deploy
title: 部署个人网站
sidebar_label: 怎么部署个人网站？
sidebar_position: 2
description: 部署个人网站的方法，记录我的部署过程，并且避免再次犯相同的错误
tags:
  - docusaurus
---

# 部署个人网站
> 我的个人网站是基于docusaurus开源库来实现的，因此这里的部署也是针对于docusaurus开源库。此外，我使用的是Github Pages + Docusaurus
> 来进行部署的。Docusaurus官方文档在这里 : :link:[Docusaurus官方文档中文版](https://docusaurus.io/zh-CN/docs)

### 前置条件
- Git


### 部署命令
```
npm run build -- --clean
```
```
$env:USE_SSH = $true; npm run deploy
```