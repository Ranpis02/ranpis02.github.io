---
title: "如何使用 Vue？"
date: 2025-09-05 22:00:00 +0800
categories: [reflection]
tags: [vue]
---

如何使用 `Vue`，这听起来是一个很蠢的问题（其实应该也是），其实我只是想表达怎么引入 `Vue` ，又怎么来使用。

## 如何在 HTML 中使用 Vue？

### 方法1：`CDN` + 全局变量

使用 `CDN(content delivery network)` 将 `Vue` 的源码引入后，`Vue` 作为全局变量暴露在外面，通过对象解构获取创建 App 实例的函数 `createApp`，再去创建 App 实例，创建完成后再挂载到 DOM 对象中

1. 先导入对应的 CDN

   ```js
   <script src="https://unpkg.com/vue@3.5.21/dist/vue.global.js"></script>
   ```

2. 创建对应的 DOM 元素

   ```html
   <div id="app">
     <button @click="count++">Current Number is : {{ count }}</button>
   </div>
   ```

3. 解构 `createApp()` 创建实例，并挂载到对应的 DOM 中

   ```js
   const {createApp, ref} = Vue
 
   const count = ref(0)
 
   const app = createApp({
     data() {
       return {
         count,
       }
     },
   })
 
   app.mount("#app")
   ```

### 方法2：CDN + ES Module

除了上述方法，还可以直接从 CDN 中 `import` 需要的函数，只需要将 `<script>` 的 `type` 属性的值设置为 `module` 即可（默认为 `application/javascript`）

```html
<script type="module">
  import {
    createApp,
    ref,
  } from "https://unpkg.com/vue@3.5.21/dist/vue.global.js"

  const count = ref(0)

  const app = createApp({
    data() {
      return {
        count,
      }
    },
  })

  app.mount("#app")
</script>
```

## 从 npm 包中导入  `Vue`

这个就很简单了，直接 `npm i vue` 即可，这里不过多赘述。
