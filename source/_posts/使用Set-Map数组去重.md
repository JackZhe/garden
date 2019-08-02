---
title: 使用Set&Map数组去重
date: 2019-06-22 22:58:51
tags:
 - ES6
categories: 
 - JavaScript
---

利用Set/Map数组去重,可以是代码更加简洁

## Set

类似数组，数据唯一

### Set 遍历数组

根据 set 里的数据唯一，来遍历数组

```javascript
const oldArr = [1, 2, 3, 4, 2, 3, '2'];
const newArr = Array.from(new Set(oldArr))；
// const newArr = [...new Set(oldArr)]

// [ 1, 2, 3, 4, '2' ]
```



当数组是由对象组成 [{},...,{}]

```javascript
const oldArr = [
  { id: '1', name: 'jack', age: 20, value: 'man' },
  { id: '2', name: 'rose', age: 20, value: 'woman' },
  { id: '2', name: 'rose', age: 20, value: 'woman' },
  { id: '5', name: 'tom', age: 22, value: 'woman' },
]

function unique (arr) {
  const set = new Set();
  // set 数据的唯一性
  arr.map((item) => set.add(JSON.stringify(item)));
  return Array.from(set).map((item) => JSON.parse(item));
}
unique(oldArr)
// [ { id: '1', name: 'jack', age: 20, value: 'man' },
// { id: '2', name: 'rose', age: 20, value: 'woman' },
// { id: '5', name: 'tom', age: 22, value: 'woman' } ]
```

缺点：当对象的键值没有规律性时，通过把组成项转化成字符串，是不同的两个

```javascript
const oldArr = [
  { id: '1', name: 'jack', age: 20, value: 'man' },
  { id: '2', name: 'rose', age: 20, value: 'woman' },
  { id: '2', name: 'rose', value: 'woman', age: 20, },
  { id: '5', name: 'tom', age: 22, value: 'woman' },
]

function unique (arr) {
  const set = new Set();
  // set 数据的唯一性
  arr.map((item) => set.add(JSON.stringify(item)));
  return Array.from(set).map((item) => JSON.parse(item));
}
unique(oldArr)

// [ { id: '1', name: 'jack', age: 20, value: 'man' },
// { id: '2', name: 'rose', age: 20, value: 'woman' },
// { id: '2', name: 'rose', value: 'woman', age: 20 },
// { id: '5', name: 'tom', age: 22, value: 'woman' } ]

```



## Map

类似对象，但键值可以是各种类型的值



### Map  遍历数组

map 的 key 唯一

```javascript
const oldArr = [
  { id: '1', name: 'jack', age: 20, value: 'man' },
  { id: '2', name: 'rose', age: 20, value: 'woman' },
  { id: '2', name: 'rose', value: 'woman', age: 20, },
  { id: '5', name: 'tom', age: 22, value: 'woman' },
]

function unique (arr) {
  const res = new Map();
  // 根据 name 来过滤 可以是id/age/value
  return arr.filter((item) => !res.has(item.name) && res.set(item.name, 1));
}
// Map { 'jack' => 1, 'rose' => 1, 'tom' => 1 }

unique(oldArr);
// [ { id: '1', name: 'jack', age: 20, value: 'man' },
// { id: '2', name: 'rose', age: 20, value: 'woman' },
// { id: '5', name: 'tom', age: 22, value: 'woman' }]
```



## ~~reduce()~~

```javascript
var hash = {};
this.selectProject = this.selectProject.reduce((preVal, curVal) => {
    hash[curVal.id] ? '' : hash[curVal.id] = true && preVal.push(curVal);
    return preVal
}, [])
```

c