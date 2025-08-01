---
title: 'How to check the data type in C++'
date: 2025-08-01 00:33:18 +0800
categories: [c++]
tags: [type checking]
---

In C++, sometimes we need to check or inspect the type of a variable or expression. So I summarize some ways to implement it.

## 01 Use `typeid`

Through using the `typeif` operator from `<typeinfo>` to get the type information at runtime.

```cpp
#include <iostream>
#include <string>
#include <typeinfo>
using namespace std;

int main()
{
   string s;
   cout << typeid(s.c_str()).name() << endl;
}
```

Output: `PKc`
> `PKc` is the mangled type used by Itanium C++ ABI(used by GCC/Clang) to represent a specific C++ type.
>
> - `P` -> Pointer(*)
> - `K` -> `const` qualifier
> - `c` -> `char`
{: .prompt-tip}
