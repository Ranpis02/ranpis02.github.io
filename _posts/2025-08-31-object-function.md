---
title: 'Shorthand in ES6'
date: 2025-08-31 16:33:18 +0800
categories: [JavaScript]
tags: [syntax]
---
Modern JavaScript(ES6+) introduces some features for writing concise and efficient object functions, improving code readability and maintainability.

## 01 Method Shorthand

ES6 allows ommiting the `function` keyword and colon `:` in object method definitions.

```js
// Traditional
const obj = {
  sayHello: function() {
    console.log('Hello');
  }
}

// Shorthand
const obj = {
  sayHello() {
    console.log('Hello');
  }
}
```

## 02 Property Shorthand

When an object's property name matches a variable name and its value come from that variable, we can omit the property name and colon.

```js
const p_name = 'Alice'
const p_age = 25

// Tradtional
const person = {
  p_name: p_name,
  p_age: p_age
}

// Shorthand
const person = {
  p_name,
  p_age
}
```

## 03 Computed Property Names

Modern JavaScript(ES6+) supports dynamic property creation. We can use square brackets `[]` for dynamic property names, paired with shorthand for flexbility.

```js
// Traditional
const key = "id"
const person = {}

person[key] = 123

// Shorthand
const person = {[key]: 123}
```

## 04 Getter and Setter Shorthand

Use `get` and `set` keywords for cleaner property access control.

```js
const obj = {
  _name: 'Alice',
  
  // Getter
  get name() {
    return this._name.toUpperCase();
  },

  // Setter
  set name(value) {
    this._name = value;
  }
};
```
