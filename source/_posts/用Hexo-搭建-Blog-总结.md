---
title: 用 Hexo 搭建 Blog 总结
date: 2018-11-11 17:13:20
tags:
  - Hexo
categories:
  - Note
---

最近又想捡起 Blog 了，原因是我发现看过的一些书和一些知识点，由于长时间的不用，留在脑子里的所剩无几！（惭愧啊）

用 Hexo 搭建博客，它的的文档丰富，主题也很多。按照文档上的步骤可以很快的搭建一个很好看的 Blog. 然后在 Github Pages 服务就可以部署到线上了

## 引用图片问题

### 安装

```
$ npm install hexo-asset-image --save
```

```
$ npm install hexo-asset-image@0.0.2 --save
```

hexo new 'xxx' 创建新的文章的时候，会在 \_posts 文件夹下生成 xxx.md 和一个 xxx 文件夹 用来存放图片

### 语法

```
{% asset_img xxx xxx %}
```

{% asset_img 1.jpg 重开6 %}

### 问题

遇到了问题是图片不会显示
解决办法: github [issues](https://github.com/xcodebuild/hexo-asset-image/issues/32#issuecomment-498626924)

## hexo 引入 CodePen

### 安装

```
$ npm install hexo-codepen --save
```

### 语法

```
{% codepen userId|anonymous|anon slugHash theme [defaultTab [height [width]]] %}
```

| 参数     | Value            |
| -------- | :--------------- |
| userId   | codepen 的用户名 |
| slugHash | codepen/pen/hash |
| height   | 265              |
| width    | 100%             |

### 效果

{% codepen jackZhe|anonymous|anon agqWQr theme [defaultTab 300 [width]]] %}

## 添加 emoji

hexo 自带的 markdown 不支持渲染 emoji, 可以更换其他的 hexo-renderer-markdown-it 渲染 markdown 成 Html

```
npm un hexo-renderer-marked --save
npm i hexo-renderer-markdown-it --save
npm install markdown-it-emoji --save
```

### 配置

## 添加域名

### 仓库设置

在仓库里 setting => GitHub Pages => Custom domain 填写 jinyizhe.com(已过期)
:satisfied: 域名续费一年比一年贵，用不起了

绑定过域名的时候，要在仓库里新建一个 CNAME 文件(没有后缀名) 把域名 写进去 eg: jinyizhe.com

## 待续...
