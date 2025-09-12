---
title: "Defensive Coding"
date: 2025-09-12 10:23:22 +0800
categories: [JavaScript]
tags: [syntax]
---

## JS 中的防御性编码

防御性编码是指在写 JavaScript 时，尽量避免歧义、陷阱（pitfall）或者其他意想不到的行为。主要是由以下情况引发：

- Automatic Semicolon Isertion(ASI)
- Type Coercion
- Prototype pollution

### ASI

自动分号插入是指在 JS 中，当解析器在遇到某些情况时会自动插入分号，主要特征如下：

1. 当行末有换行并且在换行处无法继续解析时，解析器会插入分号
2. 在 `}` （块结束）或文件末尾，必要时也会插入分号
3. 在某些以 `(`, `[` 或者 `/` 等符号开头的行，如果前一行没有显示分号，可能会和前一行的表达式拼接在一起，导致语法错误或语义错误

## 常见的防御手段

1. 前导分号（leading semicolon）：当声明语句是以 `(`, `[`, `+`, `-`, `/` 开头或者是一个模板字符串时，我们可以在前面添加分号，防止解析器误认为该行代码位上一行的一部分

   ```js
   const a = 1
   [2, 3].forEach(x => console.log(x))
   
   // Parsed as: const a = 1[2, 3].forEach(x => console.log(x))
   
   //Defensive Coding: Leading semicolon
   const a = 1
   ;[2, 3].forEach(x => console.log(x))  
   ```

2. 使用 `void 0` 替代 `undefined`

    ```js
    var undefined = 123
    console.log(undefined); //123
    
    // Defensive coding: use void 0 instead of undefined
    if(x === void 0) {
      // ...
    }   
    ```

3. 使用 Double not `!!` 替代布尔转化

    ```js
    const a = "hello"
    const b = undefined
    const c = null
    const d = 0
    const e = NaN
    
    console.log(!!a) // true
    console.log(!!b) // false
    console.log(!!c) // false
    console.log(!!d) // false
    console.log(!!e) // false
    
    // Equvalent to Boolean(value)
    ```

4. 显示类型转化

   ```js
   const x = Number("500") // 500
   const y = String("123") // "123"
   const z = Boolean(1) // true
   ```
