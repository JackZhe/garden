---
title: Flex Note
date: 2019-09-03 18:01:51
tags:
  - Flex
categories:
  - CSS
---
关于 Flex 布局的文章有很多 好文章 
1. [Flex 布局教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool) 

2. [30分钟彻底弄懂flex布局](https://cloud.tencent.com/developer/article/1354252)


### Flex

```css
.box{
  display: flex;
  justify-content: center;
  align-items: center;
}
```
```css
.wrapper{
  position: relative;
}
.box{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
这两种水平垂直居中的方法，是平时用的比较多的。