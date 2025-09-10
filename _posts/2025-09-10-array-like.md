---
title: "Array-like Object"
date: 2025-09-10 16:04:00 +0800
categories: [JavaScript]
tags: [theory]
---

> 参考：<https://dev.to/rasaf_ibrahim/array-like-objects-in-javascript-a-deep-dive-469b>
{: .prompt-tip}

## 类数组是什么？

在 JavaScript 中，经常会提到一个概念： `类数组`（array-like object）。`类数组`，顾名思义，像数组，但不是数组，而是一个对象，这个对象拥有索引 index 以及长度 length 属性，然而 `类数组` 并没有继承 `Array.prototype`，因此也没有继承 `Array` 的方法，例如 `map()`， `reduce()`，`sort()`， `forEach()` 等等。

示例

```js
let arrayLike = {
  0: 'foo',
  1: 'bar',
  2: 'baz',
  length: 3
}
```

## 常见的类数组

1. `arguments` 对象

   ```js
   function foo(a, b, c) {
     console.log(arguments) // [Arguments] { '0': 1, '1': 2, '2': 3 }
     console.log(arguments.length);  // 3
     console.log(arguments[0]);  // 1
     console.log(arguments['0']);  // 1
   } 
   foo(1, 2, 3)   
   ```

2. DOM 方法返回的结果

   ```html
   <div id="app">
     <p>Hello, World!</p>
     <p>Good Morning!</p>
     <p>Good Evening!</p>
   </div>
   ```

   ```js
   const pElements = document.querySelectorAll("p")
   console.log(pElements) // NodeList(3) [p, p, p]
   ```

## 将 array-like 转换为真正的数组

1. 使用 `Array.from()`

   ```js
   const arrayLike = {
     0: 'foo',
     1: 'bar',
     2: 'baz',
     length: 3
   }
   
   const arr = Array.from(arrayLike)
   console.log(arr); // [ 'foo', 'bar', 'baz' ]
   ```
