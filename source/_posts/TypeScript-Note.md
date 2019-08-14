---
title: TypeScript Note
date: 2019-08-06 16:19:00
tags:
  -
categories:
  - TypeScript
---

<!-- 该笔记来自 [极客邦](https://time.geekbang.org/course/intro/211) 梁宵 TypeScript开发实战 -->

Angular2 / Vue3 由 TypeScript 重写，使得对外暴露的 api 更容易结合 TypeScript。

> TypeScript 是一种由微软开发的自由和开源的编程语言。它是 JavaScript 的一个超集，而且本质上向这个语言添加了可选的静态类型和基于类的面向对象编程。

## TypeScript

TypeScript 是拥有类型系统的 JavaScript 的超集。

1. 类型检查
2. 语言扩展
3. 工具属性

.ts 文件结尾，最终被编译成 .js 文件，而且还可以直接在 .ts 文件里写入 JavaScript 代码。

### 强类型语言

不允许改变变量的数据类型，(强制转换除外)

```java
class Untitled {
	public static void main(String[] args) {
          int x = 1;
          boolean y = true;
          x = y;
          System.out.println(x);
	}
}

// boolean cannot be converted to int
```

### 弱类型语言

变量可以赋值不同的数据类型

JavaScript 是弱类型语言

```javascript
let num = 1;
let str = "a";

str = num;

console.log(str); // 1
```

### 静态类型语言

在编译阶段确定所有变量的类型

### 动态类型语言

在执行阶段确定所有变量的类型

### 基本类型

| ES6 数据类型 | TypeScript 数据类型 |
| ------------ | :-----------------: |
| Boolean      |       Boolean       |
| String       |       String        |
| Number       |       Number        |
| Undefined    |      Undefined      |
| Null         |        Null         |
| Array        |        Array        |
| Function     |      Function       |
| Object       |       Object        |
| Symbol       |       Symbol        |
| -            |        void         |
| -            |         any         |
| -            |        never        |
| -            |        元组         |
| -            |        枚举         |
| -            |      高级类型       |

### 类型注解

类型注解是一种轻量级的为函数或变量添加约束的方式,相当于强类型语言中的类型声明

{% asset_img 20190807151506.png %}

函数 greeter() 接收 string 类型的参数，当传入一个数组是会报错。

文档[教程](https://www.tslang.cn/docs/home.html)
