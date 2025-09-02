---
title: 'Solve File '@tsconfig/node22/tsconfig.json' not found.'
date: 2025-09-02 19:59:00 +0800
categories: [bug]
tags: [vue]
---

## Problem Description

After installing a Vue using `npm create vue@latest`, you may encounter an issue with the `tsconfig.node.json` file, as detailed below:

```js
File '@tsconfig/node22/tsconfig.json' not found.
```

The Vue scaffold(e.g., create-vue) does not automatically include the corresponding `'@tsconfig/*` configuration for all Node.js version by default.

Instead, it selects based on the template you use and the current ecosystem context.

## How to Solve?

The simplest solution is to install the missing dependency:

```bash
npm install @tsconfig/node22 --save-dev
```
